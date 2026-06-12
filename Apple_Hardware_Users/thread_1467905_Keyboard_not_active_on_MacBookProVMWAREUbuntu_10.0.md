---
title: "Keyboard not active on MacBookPro/VMWARE/Ubuntu 10.04"
date: 2010-05-01
forum: Apple Hardware Users
---

### Post by nitrogun on 2010-05-01
Using VMWARE Fusion 3.01 on Macbook Pro 15", C2D 2.8Ghz, installed Ubuntu 10.04 on a virtual disc, no problems installing. boots up, offers me my mac username/password logon, but no keyboard entry registers, Cursor is in the password box, tried external PC keyboard, same lack of keyboard enry. So deleted Virtual disc, awaiting suggestions from this forum.

---

### Post by blakviet on 2010-05-01
i have the exact same problem, everything installs perfectly and when you I try to type my password to log in i get no response. but i does work on my PC very well but I prefer to have it on my new macbook.

---

### Post by idemal on 2010-05-01
I have the same problem with VMware Fusion 3.02 on a Mac Pro. Install went perfectly but I can't type my password to login, nor can I do anything else with the keyboard.

---

### Post by epheterson on 2010-05-01
Hmm... guess it's not just me then.

Any solutions? I can't get the On-Screen keyboard to come up either.

---

### Post by binary10 on 2010-05-01
Did you have 'use easy install' checked from the fusion 'Linux Easy Install' window ? 

 Try it without auto install, I found it worked WITHOUT that option checked and got into the same condition as you with it checked.

---

### Post by epheterson on 2010-05-02
This does solve the problem -- I was waiting to see if there was an easier trick before I reinstalled.

Luckily Ubuntu installs really fast, Ubuntu continues to work well after the tools are installed via this method.

Perhaps somebody should file a bug report with Ubuntu?

---

### Post by arkhitekton on 2010-05-05
I've had the keyboard problem with Ubuntu 10.04 in VMware Fusion 3.0.2 on a MacBook, US keyboard layout.  I got around the problem as follows:

[LIST]
[*]At the logon screen, go to the Accessibility Preferences at the bottom of the screen, and  tick on screen keyboard.
[*]You may have to reboot if the virtual keyboard doesn’t start.
[*]You can now type in your password using the virtual keyboard on the logon screen. Once logged in, your  physical keyboard works.
[*]Open a terminal, and reconfigure your console using the command:
[/LIST]
 > sudo dpkg-reconfigure console-setup[INDENT]For my MacBook I scrolled through the list of keyboards and selected the MacBook/MacBook Pro type.  I then accepted all the other default options that were presented.
[/INDENT]
[LIST]
[*] Reboot, and you’re done.
[/LIST]
Thanks to Cat Slave Diary for the solution:
[http://www.greebo.net/2010/05/03/ubuntu-10-04-lts-upgrade-vmware-fusion-keyboard-issues/](http://www.greebo.net/2010/05/03/ubuntu-10-04-lts-upgrade-vmware-fusion-keyboard-issues/)

A bug report is also filed on LaunchPad:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/548891)

Arkhitekton

---

### Post by 14geronimo on 2010-05-23
I seam to have had the same issue with VMW 3.0.1, Ubuntu 10.04 on Windows XP Pro SP3. The trick about restarting after the first attempt of bringing up the on-screen keyboard (a bug in itself presumably) got me out of this one. Thank you Arkhitekton.

---

