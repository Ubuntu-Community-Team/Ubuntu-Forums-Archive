---
title: "Cannot change Thunderbird date format!"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by harperd on 2007-08-29
I've searched everywhere and tried a number of 'solutions' without any success. In simple terms I want the message date format in Thunderbird to be in European format (ddmmyy or Thu 3 Jan or something like that). I cannot get rid of the American date format and it's driving me nuts!

I've edited the user.js file downloaded the configdate add-on, all kinds of things all to no avail. I love linux but if any of my Windows lovers get to hear of this, they'll laugh their socks off.

Help!

---

### Post by be4truth on 2007-08-30
Are your local settings set to Spanish location?

---

### Post by harperd on 2007-09-05
yes. Spanish location but English language.

---

### Post by digby280 on 2007-10-08
I had the same problem.  The only convenient way I found of solving it was to use a script.  Essentially, you need to set the LC_TIME environment variable before launching Thunderbird.  You can find the correct value for LC_TIME by using the following command:
```
locale -a
```
This should display a list from which you can select the correct locale.  Remember to use the entire name including the postfix.  For reference purposes here is my Thunderbird script:
```
#!/bin/sh
# Launches Mozilla Thunderbird with European formatted dates.
export LC_TIME=en_GB.utf8
thunderbird

```
All you should need to do is change en_GB.utf8 to what ever you desire and make the file executable using chmod.  Hope this is helpful.

---

