---
title: "System tray space expands on adapter plug-in / removal"
date: 2012-01-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by necrosmash on 2012-01-11
Hi, I'm running Ubuntu 11.10 on my Asus Eee 1015px netbook. I installed standard Ubuntu on this a good while back (standard Ubuntu) and installed the lubuntu-desktop package earlier today. I've been using it ever since.

However, I've come across an odd bug. Every time I either plug in my power adapter or remove it, empty space gets added to the system tray icons. This happens every time I do anything with the adapter, and happens whether the battery icon is visible or not.

I recorded it happening in case my explanation doesn't make much sense: [http://youtu.be/wUqWbRGr5rA](http://youtu.be/wUqWbRGr5rA)

Any help regarding the problem would be greatly appreciated :).

Cheers

EDIT: Just a quick update in case any of y'all feel like helping: I reinstalled Lubuntu (full wipe) and the problem persisted with both the Live USB and the version that ended up installed on my netbook.

Anyone know anything at all?

---

### Post by Flazer on 2012-02-01
> **necrosmash said:**
> Hi, I'm running Ubuntu 11.10 on my Asus Eee 1015px netbook. I installed standard Ubuntu on this a good while back (standard Ubuntu) and installed the lubuntu-desktop package earlier today. I've been using it ever since.

However, I've come across an odd bug. Every time I either plug in my power adapter or remove it, empty space gets added to the system tray icons. This happens every time I do anything with the adapter, and happens whether the battery icon is visible or not.

I recorded it happening in case my explanation doesn't make much sense: [http://youtu.be/wUqWbRGr5rA](http://youtu.be/wUqWbRGr5rA)

Any help regarding the problem would be greatly appreciated :).

Cheers

EDIT: Just a quick update in case any of y'all feel like helping: I reinstalled Lubuntu (full wipe) and the problem persisted with both the Live USB and the version that ended up installed on my netbook.

Anyone know anything at all?

I get the same issue happening when waking from sleep/suspend or hibernate.  Haven't noticed it with the power adapter, but each time it gets worse and moves further to the left, eating into the task bar.

Also, I've noticed in the last two days, probably after an update, when first loading the desktop from a boot/reboot, the "start icon" has a white background to it, and so does the "power" button all the way on the right of the task bar.

I then adjust the panel prefs to something else, then back to the desktop wallpaper and it fixes it.

Anyone else notice these tray bugs?

setup EeePC 1005hab Lubuntu 11.10

---

### Post by trevor998 on 2012-02-14
I have the same problem on Lubuntu 11.10.  Any system notifications, such as conneccting or disconnecting to wireless, plugging or unplugging the power, create 4 or 5 system notification spots that persist and take up space.  Would appreciate any input on how to disable these notifications.

A partial solution is to disable the system tray in the panel settings, but that removes the wireless and battery icons and menus, which are needed.

---

### Post by MaquinaX on 2012-03-23
Hello Everyone,

      I can also confirm to the bug on Lubuntu 11.10. I installed mine on my Lenovo S10 Netbook. When it's working properly, it's great, the perfect speed for my little machine. But as soon as space issues start, damn, the desktop pretty much becomes unuseable. Only way to pretty much restore everything is to logoff, and back on again. It must be a but with the message demon, or alert demon. Let me play around with them, and see if I can get more info on this bug.


MaquinaX

---

### Post by MaquinaX on 2012-03-23
OK gents, I have an update. 
The issue is being caused by the XFCE Power-manager. From what I figure out, it appear that the moving "Space" is a result of the pop-up messages that Power Manager produces everytime the power is connected or disconnected. Since there may be an issue with the plugin or script, as it is meant for XFCE desktop,
somehow, LXCE cannot produce the pop-up, and creates moving space instead. If someone can pitch in more information as to how the XFCE Power-manager is calling for the pop-up message, then perhaps we can adjust it to "molt" to LXCE enviroment.

     Also, a quick work around is to right click on power-mananger and quit plugin, and then the "Spaces" will also be eliminated.

MaquinaX

---

