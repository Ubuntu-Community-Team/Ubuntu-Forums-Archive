---
title: "update problems"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Pragmatist on 2007-03-14
I've been having several problems since I last updated my system.  

My main question is:
How do I find a complete list of all updates made to my system?  Is there a text file containing the information?  In Synaptic, the "History" feature is grayed-out, so that doesn't help.

Here are some specific problems I'm experiencing:

1.) Key repeat is off:  I've run the command "kbdrate" and although the command exits successfully, nothing changes.  The key repeat works in a virtual terminal, so the problem must have to do with the GUI.  Also, when I run System-->Preferences-->Keyboard, nothing happens.  I found out that the command is "gnome-keyboard-properties" and when I run it in a terminal I get this:
> (gnome-keyboard-properties:10229): capplet-common-WARNING **: NULL GConf value: /desktop/gnome/peripherals/keyboard/repeat: possibly incomplete setup

(gnome-keyboard-properties:10229): capplet-common-WARNING **: NULL GConf value: /desktop/gnome/interface/cursor_blink: possibly incomplete setup

(gnome-keyboard-properties:10229): capplet-common-WARNING **: NULL GConf value: /desktop/gnome/typing_break/enabled: possibly incomplete setup
Segmentation fault


2.) "Window List" applet is not working:  The "Window List" applet that should be in the panel by default, is not there.  I have tried adding it to both panels and it still doesn't work.  It does get added as the seperator shows up, but it doesn't work.  "Window Selector" does work, but that is not what I prefer.

3.) When I update my system, my /boot/grub/menu.lst file is changed to include UUID's.  This always produces a "File Not Found" message when I try to boot.  The only way to fix it has been to use a LiveCD or an OS on another partition.

Unlike the first two problems, this last issue is something I know how to fix once it occurs.  My main interest is whether I can prevent my menu.lst from being changed every time I perform an update.

Please help!  If nothing else, I'd greatly appreciate if someone could tell me how to find a list of my recent updates.  Then I could go through and research each package to see which ones are likely to be the cause of the problems.

Thanks.

---

### Post by rawler on 2007-03-25
I think I experience the keyboard-repetition-problem. Are you running Feisty?

I've managed to track it down a little, and I've filed a bug against gnome-control-center in Launchpad. [https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/95960](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/95960)

Check it out, and see if the same conditions for reproducing applies to you.

---

### Post by freesitebuilder on 2007-03-25
> **Pragmatist said:**
> 
My main question is:
How do I find a complete list of all updates made to my system?  Is there a text file containing the information?  In Synaptic, the "History" feature is grayed-out, so that doesn't help.


I asked a similar question and got an answer here:
[http://www.ubuntuforums.org/showthread.php?t=390997](http://www.ubuntuforums.org/showthread.php?t=390997)
which may help.

---

### Post by Pragmatist on 2007-03-25
> **rawler said:**
> I think I experience the keyboard-repetition-problem. Are you running Feisty?

I've managed to track it down a little, and I've filed a bug against gnome-control-center in Launchpad. [https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/95960](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/95960)

Check it out, and see if the same conditions for reproducing applies to you.

Thanks for the reply.  I've solved my problem by reinstalling GNOME, Metacity and Nautilus!  A bit of a cheat, I know, but I was desperate to solve the problems that were spawning new ones every minute!

---

