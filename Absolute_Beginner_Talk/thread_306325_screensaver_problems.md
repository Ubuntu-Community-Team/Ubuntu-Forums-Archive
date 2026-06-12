---
title: "screensaver problems"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by stardusk on 2006-11-24
I have a problem with my screensaver loading. I set the screensaver to load after 10 minutes of being idle, but after 10 minutes, the screen is just blank. It's almost as if the screensaver were set to blank. My screensaver theme is 'random'. I want to know how to get my screensaver to show. Thanks in advance.

---

### Post by 23meg on 2006-11-24
Does it work when you choose a specific screensaver instead of "random"?

---

### Post by Cardmaster91 on 2006-11-24
i had that same problem before. i dont recall wat exactly i did to get it to start working, but i recommend trying to see if other screen savers work, and try different times. and finally try restarting. thats all igot, hope it helps

---

### Post by stardusk on 2006-11-24
I tried using other screensavers, but they don't work. Some of the screensavers won't preview.

---

### Post by Spin Doctor on 2006-11-24
Check your powersettings from the preferences menu. Make sure the option for the screen to go to sleep is greater than the time you have for the screensaver to kick in. 

As for testing the screensaver, you might also want try reducing the time of "inactivity" before the screensaver kicks in to 1 minute to see if that makes a change, and move on from there back to normal.

---

### Post by stardusk on 2006-11-24
> **Spin Doctor said:**
> Check your powersettings from the preferences menu. Make sure the option for the screen to go to sleep is greater than the time you have for the screensaver to kick in. 

As for testing the screensaver, you might also want try reducing the time of "inactivity" before the screensaver kicks in to 1 minute to see if that makes a change, and move on from there back to normal.

The screensaver was set to come on after 1 minute and powersettings 31 minutes, but the screensaver still didn't show.

---

### Post by niki001 on 2006-11-25
Stardusk,

Try this in console:

'sudo nano ~/.kde/share/config/kdesktoprc'

In the open file insert the following line under the screensaver section:
'DPMS-dependent=false'

save youre file.

Ctrl-Alt-Backspace

and test u'r screensaver now.

succes

---

