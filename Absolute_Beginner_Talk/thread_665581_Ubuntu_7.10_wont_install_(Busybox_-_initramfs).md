---
title: "Ubuntu 7.10 wont install (Busybox - initramfs)"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by lone_deranger on 2008-01-12
Im having trouble installing Ubuntu 7.10.  
Im trying to set up a dual boot system, with windows already installed.
I have two hard drives 20gb + 80gb
Pentium 4 2.6ghz
ati radeon
1 gb ram

After trying the other presented solutions on this forum, the Busybox - initramfs message keeps appearing.
When i changed "quiet splash" to all_generic_ide it entered an infinite cycle, and i noticed a recurring message
"sdb doesnt support dpo ou fua". Could that be my problem?

id be grateful for any feedback!
thanks

---

### Post by moffa on 2008-01-12
I had a similar issue.  If you wan to install Ubuntu I suggest using the alternate mode cd.  It's a text based installer.  The only other issue I had was I had to modify the grub menu to nosplash instead of splash.

---

### Post by lone_deranger on 2008-01-12
Ok, thanks for answering.
Im downloading the alternate iso to try. 
I hope its not too difficult setting up the partitions, swap etc from the text installation.

---

### Post by naugiedoggie on 2008-01-12
> **lone_deranger said:**
> Ok, thanks for answering.
Im downloading the alternate iso to try. 
I hope its not too difficult setting up the partitions, swap etc from the text installation.

The "alternate" installer is designed for systems that are short on the resource scale.  For example, the standard install would not work on my old Compaq Presario 600Mhz laptop, which had 168MB RAM.  I ran the "alternate" version happily.

The initial setup will be the same, you just won't have as much CPU & RAM-hogging junk installed.

Thanks.

mp

---

### Post by lone_deranger on 2008-01-13
Sounds great! Im going to burn the cd now and try it out.
Will update!

---

### Post by Sef on 2008-01-13
You might want to read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/"), even if you aren't dual booting.

---

### Post by lone_deranger on 2008-01-13
Well, i installed using the alternate cd, and at least this time i could get it to install.
I setup the  swap to:
         - beginning of free space
         - primary
         - bootable flag off

I hope thats right. 
Then (while installing) an error ocorred during the grub installation. It said: "grub boot loader on hd failed."

I continued installing and when time came to reboot, no dual boot options came up, and it went straight to windows.

Any suggestions! 
Thanks all! :)

---

### Post by moffa on 2008-01-13
Since you're not getting the grub menu showing at all I can't help you modify it.  To modify it you have to select the ubuntu entry (usually the first one), hit 'e' to edit it and change the line from ... splash ... to ...nosplash...

You have to get Grub to install properly first.

You need at least one partition for swap space and another for / (the main path).  Did you setup a / partition as well?  I don't think the bootable flag need to be on.

Is windows installed on one hard drive and you are installing ubuntu on another hard drive?  Did the ubuntu installer detect windows?

---

### Post by CE-Man on 2008-01-13
I have been trying to install Ubuntu 7.10 and when i reboot with the CD-Image my screen just says ISOLINUX etc. and does not do anything after that... How long is it supposed to take to load?

---

### Post by lone_deranger on 2008-01-13
> **moffa said:**
> Since you're not getting the grub menu showing at all I can't help you modify it.  To modify it you have to select the ubuntu entry (usually the first one), hit 'e' to edit it and change the line from ... splash ... to ...nosplash...

You have to get Grub to install properly first.

You need at least one partition for swap space and another for / (the main path).  Did you setup a / partition as well?  I don't think the bootable flag need to be on.

Is windows installed on one hard drive and you are installing ubuntu on another hard drive?  Did the ubuntu installer detect windows?


I tried installing again (using the alternate iso) this time all went smoothly! 
Thanks for all your help. the answers to your above questions are all "yes", but when i tried the second installation I moved the bootable flag to yes. 

I cant wait to get to familiar with this new Operating system! :)

Just one more question: It seems to be quite slow, is that normal when using the alternate installation. I checked CPU usage, and they seem appear normal.

thanks again!

---

### Post by moffa on 2008-01-13
The alternate cd just uses a different installer.  The OS is exactly the same.  What do you mean by slow?  Perhaps installer the proprietary driver for your ATI video card will speed things up.  You can activate it using System > Administration > Restricted Drivers Manager.  I know the indexing feature does thrash your hard drives for a bit but it should go away if you leave your computer on idling.

---

### Post by lone_deranger on 2008-01-14
By slow I mean slow to boot,and sometimes slow to respond when opening and closing applications. 

I have been having a problem while browsing with firefox, which sometime goes grey, but i have already found some help for that, Im going to check if it works.

There is also another larger problem: when I try installing new things, example: "sudo apt-get install -y gdesklets" when it reaches the end of the installation process it simply freezes, no mouse or keyboard action.
When this happened, I had to reset manually. It then wouldnt start automatically, and gave me the message:
/dev/hdb1/: unexpected inconsistency; run fsck manually (ie - without -a -p options)
fsck disk died with exit status.

So i did the fsck manually, and at the end a screen came up saying:
Could not star the X server (your graphical environment) due to some internal error. Please contact system admin or check syslog to diagnose.
Please restart when problem corrected.

So it is probably as you suspected: graphic card problems. When doing as you said: System > Administration > Restricted Drivers Manager the message "your hardware doesnt need any restricted drivers".

Sorry for being so troublesome, and thanks once again for all your help. :)

---

### Post by moffa on 2008-01-14
The errors seems to state your hard drive has some problems.  Is it a very old hard drive?  If it is, try testing it with a boot cd, I use [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)
It seems that your hard drive is dying.

The ATI driver package is xorg-driver-fglrx and the control panel program is fglrx-control.

---

