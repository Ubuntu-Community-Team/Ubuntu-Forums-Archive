---
title: "Some questions"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by cool11 on 2008-02-18
Hello everyone 

I have some questions, it would be great if someone helped me out.
My system config is:
celeron 600 mhz, i810 mobo,192 mb ram, 100 gb hdd (20+80), cd/dvd rw with currently windows 2k installed.
I downloaded the xubuntu 7.10 desktop cd ie live cd. I wanted to ask is:

1) If i do a dual boot with win2k and if i dedicate the 20 gb drive to xubuntu and install on it, where will GRUB be stored on 20 GB drive or 80 GB (80 GB would be master and 20 GB would be slave). Because my question is after installing if i have some problems with the linux distro if i format the 20 gb drive or just disconnect it for some time, will it cause problems with the existing win 2k installation or still display grub without the 20 Gb HDD?

2) I tried the live cd and noticed it was very slow(i think its because of my system). But i noticed one strange thing is that i couldnt see the taskbar and the top applications bar. When i managed to get into terminal it came in full screen and i had no clue what to do. After a few key presses it logged out and now after logging in, the taskbar and applications bar showed up. can someone tell me what really happened ? coz this happened twice, and a little help on the terminal would be really appreciated (how to come out of full screen.. as i used red hat earlier and it opened in a window).

3) I tried configuring the network and configured my ip address and other details as required by my net connection but was not able to establish a network connection and thus the internet.
The network when setup does show the icon in the right top corner but doesnt show any statistics as the windows network connections shows(ie packets sent and received), is it because it was not properly setup?

4) Need some network commands like ping for the terminal (does ping work in ubuntu?)

5) Will the Xubuntu alternate cd be like win xp bootable installation disk or does it make use of commands for installation?

6) Is there a task manager in linux(ctrl+alt+del)?

7) I could view my NTFS partitions by default when i was running the live CD. Would the partitions be displayed by default after installation or will have to mount it?

I know these are a lot of questions, but i need to clarify my doubts before installing xubuntu
I would ask more later :P
Thanks for reading

Thanks and Regards

---

### Post by ruy_lopez on 2008-02-18
Grub doesn't install into a partition that you use for data. It runs from the Master Boot Record at the very start of your HD.

---

### Post by sryth on 2008-02-18
> **cool11 said:**
> 
1) If i do a dual boot with win2k and if i dedicate the 20 gb drive to xubuntu and install on it, where will GRUB be stored on 20 GB drive or 80 GB (80 GB would be master and 20 GB would be slave). Because my question is after installing if i have some problems with the linux distro if i format the 20 gb drive or just disconnect it for some time, will it cause problems with the existing win 2k installation or still display grub without the 20 Gb HDD?

2) I tried the live cd and noticed it was very slow(i think its because of my system). But i noticed one strange thing is that i couldnt see the taskbar and the top applications bar. When i managed to 

3) I tried configuring the network and configured my ip address and other details as required by my net connection but was not able to establish a network connection and thus the internet.
The network when setup does show the icon in the right top corner but doesnt show any statistics as the windows network connections shows(ie packets sent and received), is it because it was not properly setup?

4) Need some network commands like ping for the terminal (does ping work in ubuntu?)

5) Will the Xubuntu alternate cd be like win xp bootable installation disk or does it make use of commands for installation?

6) Is there a task manager in linux(ctrl+alt+del)?

7) I could view my NTFS partitions by default when i was running the live CD. Would the partitions be displayed by default after installation or will have to mount it?


I'm fairly new myself, so I'll only answer the questions I can.  GRUB will be in the master boot record of the master disk...removing the other one might generate an error message but it won't be a fatal one.  

The live cd is very slow yes...because it is reading from a CD, which is much slower than a hard drive.  And even slower on an old CD drive. :)

taskbar and top applications bar...when you get into the menus up there. go into system/preferences and make your screen resolution smaller.

Dunno about the network, mine configured automatically when I installed.

There is a system monitor under the top bar system/administration.  and ps xuw or ps -e are good commands in the terminal.

Your other partitions should be visible...mine were.

---

### Post by Iowan on 2008-02-18
I haven't really dealt w/ Xubuntu, but...
1)
2) I accidently tried to boot the CD from a P100. After it thrashed around for an hour or so, I pulled the power.  There are a couple of ways to get a terminal (or terminal emulator). One is CTRL-ALT-F1 (there are actually six - F1-F6) or CTRL-ALT-F7 for the desktop.  At least on Ubuntu (Gnome).
3)
4) Ubuntu has "ping".
5) The version you got *should* have option to install.

---

### Post by cool11 on 2008-02-18
I thought so ... grub would be on the mbr. I hope it wont corrupt and screw up the HDD on formatting of the drive which has xubuntu on it.
I am asking about the alternate cd, live cd does have a install option through the desktop but the disc was so slow that i thought to give the alternate cd a try.. would it have a normal select next procedure or you need some command experience for the alternate cd?
And btw my drive is not an old one.. its a DVD rw drive ...lol

---

### Post by ruy_lopez on 2008-02-18
The alternate CD asks more or less the same questions as the liveCD installer. The only difference, to my knowledge, is that it uses ncurses to display the menus. You shouldn't have to execute any commands. I find the alternate CD a lot more responsive.

---

