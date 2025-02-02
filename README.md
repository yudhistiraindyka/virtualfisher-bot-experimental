# Virtual Fisher : Autofish Bot

Auto Fishing Bot made in Python 3 for [Virtual Fisher](https://virtualfisher.com/) Discord bot.

## Features
- Auto Fish 
- CLI UI (Menu)
- [Captcha Bypass](#captcha-information)
- Auto Buff (more treasures + more fish)

## Demo
![demo](assets/images/demo.gif)


## Installation and Update
Using the terminal, type:
```bash
git clone https://github.com/thejoabo/virtualfisher-bot.git
cd virtualfisher-bot
pip install -r requirements.txt
```

## Usage
Using the terminal, in the repository folder, type:
```bash
python autofishbot.py
```
**Note:** *On the first start up, the bot will ask you to fill the configuration file name (which will be stored at 'configs/' folder). After setting everything up, run the command again. In case of several config files you will be prompted to choose one. [More help](assets/faq.md) | [Template](assets/template.config).*

## Customization

You can easily customize the options listed below in the automatically generated [config file](assets/template.config):

```config
#Example
[PREFERENCES]
CHANNEL_ID = 123456
USER_TOKEN = M@yToke_n123
OCR_API_KEY = MyK!ey12.3
USER_COOLDOWN = 3.5
BAIT = WORMS
AUTO_BUFF = TRUE
BUFF_LENGTH = 5
FISH_ON_EXIT = FALSE
COMPACT_MODE = FALSE
DEBUG = FALSE
NUMBER_FORMATTING = DEFAULT
```
*Detailed information [here](assets/faq.md).*


## Captcha Information
Virtual Fisher has now removed almost every captcha. The only one left is the image recognition one. They also changed how those images are generated, so **preprocessing is no longer required**. The OCR.SPACE API for image to text recognition seems to work with reasonable consistency in the tests performed. Therefore, to automatically solve captchas you **will need** an [API KEY](#how-do-i-get-my-free-key-).

The metodology is pretty straight forward, when a new captcha is detected:

1. A request is sent to the API for each available OCR engine
2. The results are filtered to assert those with reasonable certainty
3. The filtered result list is tested
If all tests fail, a request to regenerate the captcha will be sent (up to 3 times). If everything goes wrong, the bot will halt util you solve it manually.

Keep in mind that the captcha detection method  is not flawless, unexpected events can cause some unusual behavior that could influence detection accuracy. Therefore, it should not be left alone without monitoring for longer periods of time.
### Demo
![captcha-demo](assets/images/captcha-demo.gif)
*(the current step is outputed on the top, 1.5x speed)*


- ### HOW DO I GET MY **FREE** KEY ?
All you need to do is use [any](https://temp-mail.io/en) email to get it here: https://ocr.space/ocrapi/freekey.

- ### THERE IS ANY OTHER WAY TO DO IT **WITHOUT** THE KEY ?
For now this is the only way. But I'm thinking about the possibility of make an API myself to enable users to redirect their requests through a list of keys.

*[Need more help ?](assets/faq.md#how-do-i-get-my-ocrapikey-)*


## Changelog
###  v1.2.0 - 7/31/22 (current)
#### **Added**
- support to multiple configuration files
- support to third-party (custom) menus - experimental
- debugger class (using inspector package)
- pause/resume class
- compact mode ([#23](https://github.com/thejoabo/virtualfisher-bot/discussions/23), [#15](https://github.com/thejoabo/virtualfisher-bot/issues/15) )
- resize function for messages and notifications (to avoid errors when strings > terminal width)
- FAQ to config parameters
#### **Changed**
- discord webgate (connectivity issues, compartmentalization)
- cooldown method - normal distribution ([#12](https://github.com/thejoabo/virtualfisher-bot/discussions/12))
- project overall structue (features can now be compartmentalized, config folder, app folder)
- config management method (also, new parameters)
- proper async approach (dispatcher and listener)
- all menus are now parts of a class (MenuManager)
- imports (external packages limitation)
- captcha detection method ([#14](https://github.com/thejoabo/virtualfisher-bot/issues/14))
- calculations for menu dimensions and proportions
#### **Fixed**
- sanitized normal emotes (@yudhistiraindyka [#22](https://github.com/thejoabo/virtualfisher-bot/pull/22), [#20](https://github.com/thejoabo/virtualfisher-bot/issues/20))
- multiple embeds handling for profile functions
- pause function argument handling 
- autobuff/resupply function queries  
- captcha regen when all results fail ([#14](https://github.com/thejoabo/virtualfisher-bot/issues/14))
- captcha timeout limit to check for confirmation messages
- captcha answer duplicates are now ignored
- captcha safe-exit methods when abnormal behavior is found
- config manager class (proper exceptions handling, minor compatibility issues)
- reduced memory consumption while paused
- stalling conditions for the dispatcher (while captcha detected or autofish is paused)
- curses exceptions handling (addwstr() type errors) ([#21](https://github.com/thejoabo/virtualfisher-bot/issues/21))
  
...

[FULL CHANGELOG HERE](assets/changelog.md)


## Contributing
- Pull requests are welcome. For major changes, open an issue first to discuss what you would like to change.
- If you notice any errors, bugs or strange behavior **[PLEASE OPEN AN ISSUE](https://github.com/thejoabo/virtualfisher-bot/issues/new)** containing a screenshot or describing the problem.
- [**Suggestions**](https://github.com/thejoabo/virtualfisher-bot/discussions/new) are welcome.

