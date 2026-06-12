---
title: "XP boot issue"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by moomintroll on 2007-03-03
Hi - I'm new to this but would like to stick with it and eventually say goodbye to Windows.  The problem is I am currently dual booting, the default is Ubuntu but occasionally I would like to boot in to XP until I'm completely happy to get rid of XP.

If I start up I can not boot in to XP - what seems to work is if I boot in to Edgy and then restart, if I then select XP from grub Windows then boots without problem

Any ideas appreciated as I really want to make Ubuntu work

Thanks

---

### Post by Amenemhet on 2007-03-03
Does your pc boot immediately to Ubuntu? If so..
You need to adjust your boot menu...
In a terminal window, type..
$cd /boot/grub
In there you will find a file called menu.lst..read it, it has very good comments, and what you want to do is adjust the time your boot loader takes to automatically boot your default operating system..
You may see a comment that is 'commented out' like this...
#timeout=
timeout=10 > this will tell the boot loader to wait 10 seconds before it starts loading the default os
You can change this to what you wish..ie:10 secs or 30 secs, whatever, and then when you start up your pc, you should see your boot loader, with a countdown to load the default os.In this time you can choose what os to start. You could also change your default os as well, if you wish..there will be a line that says...
default=0   > 0 being the first or default os to load, change this to 1 if windows is the second choice, although I think grub puts vesa mode as a 2nd choice, so maybe you need to change this to 2, meaning the 3rd 'choice' to boot.

---

### Post by moomintroll on 2007-03-04
The problem is that windows wil not load at all unless I boot into Ubuntu first / restart / then select windows from grub menu - this then lets windows boot.

If I was to start the PC and select windows without booting into Ubuntu first then the Windows XP splash dcreen flashes for a second and then the pc reboots.  To re-iterate - if I boot into ubuntu first / restart windows load 

Any ideas what the issue is??

Thanks

---

