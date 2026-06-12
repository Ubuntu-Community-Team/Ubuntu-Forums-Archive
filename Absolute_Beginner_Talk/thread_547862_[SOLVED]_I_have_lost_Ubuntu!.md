---
title: "[SOLVED] I have lost Ubuntu!"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by enzeru on 2007-09-10
New Problem:

So my new question, how do I uninstall grub if it is already installed? I don't want to screw this up anymore than i already have...

==OLD PROBLEM - SEMI FIXED==

Problem:
I have a dual boot setup running XP and Ubuntu installed on physically separate hard drives right now. Over the weekend my windows drive failed spectacularly and I had to get a new hard drive.  Being fairly computer savvy I reinstalled windows and got it all back up and running but I noticed that my grub seems to be gone (i assume it was installed on the windows drive which was the primary boot i believe) so I cant see Ubuntu but I know its there (separate hard drive). Also can not access livecd for some reason (mentioned below) it wants user/pass

Some things I have tried:
I tried switching the default hard drive to bot just to force it into loading Ubuntu by looking for it first but it gives me a error about loading OS.
I tried loading into my livecd to see if I could find the drive and just pull my stuff off of it but my livecd asks me for a user name and password. I thought maybe it had loaded into my Ubuntu somehow but when tried my Ubuntu login it didn't work.

 If anyone knows how to reload grub (or maybe some other boot loaded?) without destroying my Ubuntu installation, or at least access my Ubuntu to back up my files for a reinstall would be appreciated.

---

### Post by JawsThemeSwimming428 on 2007-09-10
I don't know much about it but I use EasyBCD on Vista. Not sure if you can use it with XP or your situation.

---

### Post by forestpixie on 2007-09-10
this should help -
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

or have a look at [this]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

---

### Post by enzeru on 2007-09-10
> I don't know much about it but I use EasyBCD on Vista. Not sure if you can use it with XP or your situation.
From what I just looked up that is a Vista boot loader tweak so it would be incompatible with XP

> **forestpixie said:**
> this should help -
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

or have a look at [this]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

Problem with that is it wants me to boot from the livecd and use it to recover but when I bot the livecd i wants a user name and password I don't know for some reason (did not do that when I installed Ubuntu so not sure whats going on with it) is there a default user name and password that ubuntu livecd's load that it wants?

---

### Post by CaptainInsaneO on 2007-09-10
Try reinstalling GRUB: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

I've fixed GRUB error 17 before using fixmbr on my Windows install disk. Kind of unrelated, but a good tip none the less. And completely mind-boggling because I have no idea why it works.

Try this out to access your Linux from Windows: [http://www.fs-driver.org/](http://www.fs-driver.org/) (Only works if you're using ext2 or ext3 filesystems).

P.S. The username is ubuntu and the password is blank.

---

### Post by enzeru on 2007-09-10
> **CaptainInsaneO said:**
> Try reinstalling GRUB: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

I've fixed GRUB error 17 before using fixmbr on my Windows install disk. Kind of unrelated, but a good tip none the less. And completely mind-boggling because I have no idea why it works.

Try this out to access your Linux from Windows: [http://www.fs-driver.org/](http://www.fs-driver.org/) (Only works if you're using ext2 or ext3 filesystems).

Quickly browsed the thread, but again my livecd is asking for some sort of user/pass combo so I cant load into it to use any of these threads to reload grub :( and i just told it to install so it probably is ext2 or 3 so if I cant figure out the livecd thing can just try that

---

### Post by CaptainInsaneO on 2007-09-10
Again, try ubuntu as the username and leave the password field blank and see if that lets you boot the livecd.

---

### Post by enzeru on 2007-09-10
> **CaptainInsaneO said:**
> Again, try ubuntu as the username and leave the password field blank and see if that lets you boot the livecd.

I was already replying when you made that edit, I tired it and that didn' work either I think my livecd may be damaged so I am downloading a new one now, will see if it fairs any better =/

---

### Post by CaptainInsaneO on 2007-09-10
That's always a good solution too. Make sure that when you burn the iso to disk, to burn at the slowest burn rate possible to minimize errors. Then use the "Check disc for errors" option when you first boot it. :)

---

### Post by enzeru on 2007-09-10
> **CaptainInsaneO said:**
> That's always a good solution too. Make sure that when you burn the iso to disk, to burn at the slowest burn rate possible to minimize errors. Then use the "Check disc for errors" option when you first boot it. :)

Ok well it appears I did have a bad livecd, but now I have gone and made a real mess of things :( I managed to install grub but i installed it on the wrong drive,

I loaded grub but set wrong drive (Ubuntu one) as install point so when i reboot it loads the boot drive (Windows drive) and has no clue Ubuntu is there still.  Simple enough, I swap my hard drive order and make Ubuntu the boot drive.  Well now it cant find the operating systems because i went and switched the hard drive order on it.  So i reloaded the livecd and installed grub on the windows drive this time, but I forgot to switch the hard drives back so now I have grub on both drives but neither will boot cause they each thing the operating systems are on different discs...

So my new question, how do I uninstall grub? I have been trying to find a uninstall command in it but I don't know what I am doing in the grub program and don't want to make the situation worse than it already is

---

### Post by CaptainInsaneO on 2007-09-10
If you have a Windows install disc, run fixmbr from the repair utility on that disc. (i.e. boot into windows setup, choose "Repair" and run fixmbr). That should reset the mbr on your Windows disc, no switching of discs needed and you should be good to go from there.

---

### Post by enzeru on 2007-09-10
> **CaptainInsaneO said:**
> If you have a Windows install disc, run fixmbr from the repair utility on that disc. (i.e. boot into windows setup, choose "Repair" and run fixmbr). That should reset the mbr on your Windows disc, no switching of discs needed and you should be good to go from there.

Well did that and got windows back up and running.

But when I had it all set back up and tried to load grub to my windows drive i got "Error 17: Cannot mount selected partition".  :(  
Quick Google search turned up [this thread in the Gentoo forums]("http://forums.gentoo.org/viewtopic.php?t=120802") that solved my issue. For some reason since i am running separate hard drives i had to run the root on my windows drive (hd0) but then tell it to setup on my Ubuntu drive (hd1). Not sure why this works but solved the problem i now have a working dual boot again.  Thanks for your help everyone couldn't have fixed this issue without you :)

---

### Post by CaptainInsaneO on 2007-09-10
Congrats on getting it fixed!

I actually have the same set up as you, I run Windows and Linux on two different physical drives... I've never had a problem with grub though. Don't really understand why, tbh. I just point and click during install. :lolflag:

Glad to help.

(It's funny how Ubuntu is a free OS and the customer support is better than Microsoft could ever HOPE to be. :tongue:)

---

