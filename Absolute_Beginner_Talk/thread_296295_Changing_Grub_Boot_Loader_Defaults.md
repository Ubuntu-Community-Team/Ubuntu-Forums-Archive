---
title: "Changing Grub Boot Loader Defaults"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2006-11-09
Basically, i have installed Ubuntu and Windows XP Pro on my family's computer, and its all fine i use ubuntu, they use windows.

their is one problem though they use that computer far more than i do, and i would like to set the Grub boot loader to load windows on startup as default.

thanks for your help.

---

### Post by Henry Rayker on 2006-11-09
There will be a line in the menu.lst file that says something like

default # (where # is a number). You will need to change that # to the one that corresponds to Windows. I believe you need to count (starting at zero) every line that begins with the word "title". When you find the number that corresponds to Windows, put that in the default # line.

I hope that helps. If you can't figure it out, please post your menu.lst and we'll help you out further.

---

### Post by jkvv_1973 on 2006-11-09
if you are a windowscentric person...check out


[http://ubuntuforums.org/showthread.php?t=228104&highlight=grubEd](http://ubuntuforums.org/showthread.php?t=228104&highlight=grubEd)



GrubEd is a little (UPDATE: NOW 'QUITE BIG') script I wrote which gives users a nice GUI to alter their grub settings. It is a vastly modified version of my earlier, non-GUI script.

Using GrubEd, you'll be able to alter your grub settings at the touch of (a few) buttons! It currently supports:

Default menu item editing: Set Grub to boot into whichever OS you want through a handy menu.

Timeout editing: Set the timeout to whatever you feel like. Displays a confirmation box if you set it below 3 seconds.

Disable the timeout: Always getting caught out? Just disable the timeout!

Hide Grub: Hide or unhide the Grub menu depending on your current settings.

Change custom colour settings: Set grub to a colour scheme of your choice!

Add a Grub splash screen: Make Grub display an image as it's background!

Enable / Disable memtest86: Don't want it? Scrap it :P

Change the number of kernels Grub shows: Confused by a big list of the same OS? Simply change the number of kernels to keep your list tidy!

Direct Edit: Shows your entire Grub settings file for easy editing.

Reboot: Reboot your machine to test your new settings.

Backup: Back up your current Grub settings. I reccommend you use this first!

Restore: Easily restore your backed up Grub settings file.

There's also a handy help file to tell you how to use the script properly.

Here's the text of the README to tell you how to install / uninstall / use:

---

### Post by Jamesbowden on 2006-11-09
I'll try this GrubED thing, if it doesn't work (i'm sure it will work) i'll do the source list thing.

:D

---

### Post by bulldog on 2006-11-09
It works,trust me.:D

---

