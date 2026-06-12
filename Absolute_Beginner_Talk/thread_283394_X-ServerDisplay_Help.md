---
title: "X-Server/Display Help"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by tetherblood on 2006-10-24
First off,
This is my first post and problem so i hope you can bare with me on this. I am an inexperienced linux user and decided to install Ubuntu 6.06 i386 to see what it could offer..
The install went OK, managed to connect to the internet.. then i installed a program called [EasyUbuntu]("http://easyubuntu.freecontrib.org/") which went about autodetecting hardware and installing drivers, codecs and popular apps. I installed the graphics drivers as i assumed i needed them (Ubuntu would freeze whenever the screensaver started).

Bare with me :P

When i restarted the Ubuntu log-in screen was not displayed and i got a screen saying would i like to autodetect the error/view it. I selected yes and get a screen with some text and no real "diagnosis" but a mention of xorg.conf. After googling on the windows boot i found a few helpful (are they!? you tell me!) commands to help understand what was up. First i logged on through the terminal that appears instead of the GUI log on screen using my username and password.

The first was **fglrxinfo** which returns **unable to open display :O**
i assumed this to be confirmation of a gfx problem?

I also read somewhere that the problem could be that the config is using the **ati** driver instead of the **fglrx** so i set about changing this.

First i tried **sudo gedit /etc/x11/xorg.conf**
but it returned an error loosely saying it couldnt open/get the file and this particular error contained NULL in it.

Second i tried **sudo dpkg-reconfigure xserver-xorg**
which brought up a series of menus (similar to those in the Easy Ubuntu installation) to configure certain hardware (GFX, Monitor, Mouse, Keyboard) i selected auto detect card it brought up my Radeon 9000. On the next page i selected **fglrx** as the driver and continued through adding the settings for UK keyboard, mouse etc and at the end it returned a warning that it was overwriting the xorg.conf and i assumed that these settings would now be saved.

On reboot or **fglrxinfo** i still recieve the same problem.
**Cannot open display :0**
When i reopen **sudo dpkg-reconfigure xserver-xorg**it always seems to have 'reverted' back to the old settings (i dont know if it reads the defaults from the conf file) and trying a few different setups hasnt helped.

I am running Ubuntu 6.06 i386 dual boot with Windows XP Pro.
My graphics card is ATI Radeon 9000.
As im using one machine it was difficult for me to provide accurate accounts of some errors, i can get these on request.

Any help would be appreciated because i really cant wait to get back onto Ubuntu as i was highly impressed before this problem kicked me the you-know-whats. 

Apologies in advance:
If this is in the wrong forum
If this is one of those questions that gets posted everyday :mad: 

Thanks in advance
Matt (a prospective windows convert)

---

### Post by dmizer on 2006-10-24
well you couldn't edit xorg.conf because the directory is wrong ...
the x in x11 should be a capital X (linux file and directory names are case sensitive).  but dpkg-reconfigure xserver-xorg is a better way of going about making changes to your xorg.conf file anyway.

what is the output of lspci?  this will show what chipset your ati card is using.

when you reconfigured xserver-xorg, were you sure to set up your monitor again?

since you used easy ubuntu, you may have to rely on them for help untangling the mess.  they're a good crew and easy to get in touch with them in irc.

note: what follows is opinion (opinion based in lots of experience, but opinion none the less)...
-> screen savers are bad.  they use extra cpu and monitor power when your pc would other wise be idle (think green planet man!), and many of them are buggy anyway.  just don't use it ;)

use a blank screen instead.  boring? yes, but i've never had a problem with the computer locking up as a result of a blanked screen.

---

### Post by funkyade on 2006-10-24
I've just replied to a similar thread here, this may help -

[http://ubuntuforums.org/showthread.php?t=283464](http://ubuntuforums.org/showthread.php?t=283464)

if you are still stuck post back.

---

### Post by tetherblood on 2006-10-24
i have to be honest, the problem seems to have fixed itself!
after sitting on windows for a while posting in this forum and browsing google, a restart brought me back onto the log in screen of ubuntu which was a shock. No doubt something i did nudged it as i was wrestling with it for a good few hours.
Im now Ubuntu active again!

Thanks for the heads up about the case sensetivity, a good newbie lesson for me and i have since edited the xorg.conf to the correct driver.

Ive also disabled my screensaver ;) 

Sorry for the false alarm, but the links provided should help anyone else that gets these problems.

Thanks

Matt

---

