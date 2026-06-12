---
title: "menu.lst"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by GregM321 on 2007-09-10
I have loaded Ubuntu onto my desk top and when I reboot all I get is the grub>    command prompt.

I have just downloaded the 7.04 iso and burned it using nero (its all i had)

And during the install it recognized the fact that there was a windows partition on there.

My question is this:

Is there not supposed to be a GUI that we can select the os we'd like to boot?

All I get is the command prompt, and when I checked there is not menu.lst in the boot/grub directory  (I don't have it right in front of me but I think that that was where it was supposed to be -- forgive me if it is not exactly right -- but I looked all over for it and can't find it)

Can I install the GUI after the fact if it isn't there?

Thanks for the help

Greg

P.S.  I tried the Fedora 7 and it loads a GUI fine but I have real issues once booted (ie I don't even get to see a mouse cursor so I'd like to try and get Ubuntu to work because once loaded it seems fine but i need something easy (like the GUI, and a menu.lst to edit) in order for anyone else to boot into any other os ie. windows.

Thanks again.

---

### Post by s26c.sayan on 2007-09-10
Try [Reinstalling GRUB]("http://ubuntuforums.org/showthread.php?t=224351") using the Ubuntu Live CD.

---

### Post by Duck2006 on 2007-09-10
At the grub promp type

find /boot/grub/stage1

it will come back with ie (hd0,1)

then type this with what it comes back with

root (hd0,1)

setup (hd0)

quit

and reboot and you sould have a menu to chose your system to boot

---

### Post by southernman on 2007-09-10
**/edited - Sorry, I just reread your post. Don't understand why grub didn't install but follow one of the members above me for fixing it.**

---

### Post by bodhi.zazen on 2007-09-10
Yes, it sounds as if grub was not installed.

To be honest, the easiest for you may be to reinstall :(

Be sure to install grub to your MBR.

If you are interested, you can look at these links and supergurb :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Supergrub : [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by GregM321 on 2007-09-11
Thanks for the suggestions folks -- I am away from the home computer right at the moment but look forward to giving your suggestions a try.

Any idea why grub would not have installed the GUI?  Was there something I missed in the setup?  I did it twice but didn't notice any option for it.  Anyway, I'll give it a shot and let you know how i made out.

Thanks again.

---

### Post by Mark_in_Hollywood on 2007-09-13
Patience, sir. Did you make an .iso cd when you used Nero?

If not, you must use a burner that can make an .iso.

Stupid as I make myself seem,  maybe it's the cd as the problem.

---

