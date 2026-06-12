---
title: "Change boot timeout ?"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by Drakkor on 2006-06-26
Ok, I have XP on drive 1 ,and Ubuntu on drive 2, and I'm dual booting with Grub from the mbr,which is what I want, however, I would like to change the default
10 second timeout to boot Ubuntu,say to 5 seconds. I know there is a setting somewhere, I just can't find it !  Thanks !

---

### Post by DCM36 on 2006-06-26
use this command
```
sudo gedit /boot/grub/menu.lst
```

and change the timeout value to whatever you like

---

### Post by Drakkor on 2006-06-26
Thanks, DCM36 worked great !  Cheers :p

---

### Post by ajgreeny on 2006-06-26
Type *gksudo gedit /boot/grub/menu.lst* in a terminal and look for the para like this:-

[I]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5[/I]

You'll see I have my system on a 5 second timeout, as you want.  You can change this to anything you want, but I've read that it can cause problems if you set it to 0(zero), though I don't know what happens if you do, I've never had the courage to try it out.

Incidentally you can also change the OS that boots by default by changing the bottom line of the following section:-

[I]## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0[/I]

 to read the appropriate number from the list in the menu, Ubuntu being the standard default boot OS.

---

### Post by Drakkor on 2006-06-26
Thanks also, ajgreeny, but I want to use XP less and less now that I have Ubuntu,lol :) Free at last ! Of the constant spyware,antivirus,worm,trojan, and malware scans ! I've been using Dapper for about 8 or 9 days now, and it's rock solid, even though I have installed lots of programs, and customized it, it's still rock solid. (From a guy who really doesn't know diddley about Linux)
**UBUNTU ROCKS !!** :-D

---

### Post by glotz on 2006-06-26
I wholeheartedly agree! :)

Here's a few tips for you. Just like most tweaks, they probably will help you but they could mess up things for you too, so be careful there.

You'll probably want to install a specific kernel, see [http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

And you might want to disable services you don't use, for example I don't use bluetooth or RAID, see [http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

Got multibuttoned mouse? Does your sound work? Got Nvidia or ATI acceleration sorted? Want help with any of that?

---

### Post by Drakkor on 2006-06-26
Yep,glotz, got my Xmms going, DVD playback, TVTime,Nvidia,printer,and arlready updated the kernel to 686, at first there were too many options at boot,can't remember now,but now all I have is Ubuntu i686, Ubuntu i686 safe mode,the Memtest and other operation sytems..XP. I'll have to check on the services,
Thanks ! :)
I do have a multi-button Logitech optical mouse with a button on the left side
that in windows if I clicked that, it would go a page back which was nice,rather than hitting backspace or the left arrow to navigate, could I get that working?
Thanks :eek:

---

### Post by glotz on 2006-06-26
Sure you can. I've too got a Logitech optical with a back button. See this guide [https://wiki.ubuntu.com/ManyButtonsMouseHowto](https://wiki.ubuntu.com/ManyButtonsMouseHowto)

---

