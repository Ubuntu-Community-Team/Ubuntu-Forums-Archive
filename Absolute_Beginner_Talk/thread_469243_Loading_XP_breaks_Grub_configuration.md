---
title: "Loading XP breaks Grub configuration"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by imog on 2007-06-09
My T43 gets stuck in a reboot loop after every time I reboot after using XP.  The message displays "Grub loading Stage1.5", it then reboots to the POST screen, displays the message again, and continues to loop.

I can allow the Grub OS list to display again by using the LiveCD and issuing some commands to restore Grub.  But after running XP again and rebooting, the same problem will reoccur.

What part of running XP is killing my Grub?  Is it XP itself?  Is it McAfee?  Is it Cisco CSA?

---

### Post by HunkirDowne on 2007-06-10
XP did this to me yesterday.  XP is breaking GRUB most likely.  I cheated and put a fresh install on another partition which reinstalled GRUB but only after trying to reinstall GRUB including a refresh of my master boot record using **DOS** FDISK: "FDISK /MBR" that I had laying around.

If you have a "live" CD that does rescue you might try the following that I got here doing a search for "fdisk /mbr grub" (sans quotes):

(Insert and boot live cd)
(Enter terminal)
$ sudo grub
grub> find /boot/grub/stage1
(grub will report the location as (hd#,#) indicating the disk and partition of the location.
grub> root (hd#,#)
grub> setup (hd#)
grub> exit
(reboot)

Caveat: I have not tested this but I would try it.  Read on for my background and some advice if you have time.  Otherwise, just try the above and let me know if you get it working.

background:
I'm a recently returning Linux user so I'm trying to brush up on some stuff.  My "stable" system is an old Dell with two operating systems, both Linux.  My "unstable" system came with XP which I've shrunk to about 15 GB and installed three other Linuxes -- one of which will go away but I will have a default boot (Ubuntu Christian Edition), maintenance boot (Ubuntu), and mobile boot (XP), the latter only until I get wireless, scanner, print functions ironed out or I decide I can't live without some of the software (haven't tried WINE yet, though).

advice:
You may want to consider looking through the HOWTO section on tldp.org which is what I'm doing right now.  I think I am going to end up with a small DOS partition with just enough tools to repair my MBR and maybe contain an emergency boot loader like LILO or loadlin.   My preference would be GRUB but I don't know if I can install GRUB to a DOS boot partition.  So that would be /dev/hda1 and XP would go on the next partition, /dev/hda2 with /dev/hda3 as the extended partition which would contain logicals hda5, 6, 7, & 8, the first two for linux mount points, the next for swap, and the last for extra data storage.

I've been away from Linux for a while and some things have changed, like Xorg and using /dev/sda1 instead of /dev/hda1 for my non-SCSI HDD.  I think I understand the Xorg bit but scratching my head about the sda designation for IDE HDD's but it could have something to do with the larger IDE's now available -- I dunno.
</ramble on>

---

### Post by EndPerform on 2007-06-10
That's a weird situation.  I have XP dual-booting on this box and I don't have any problems.  Does McAfee check the boot record to see if it has changed?  Perhaps it thinks there's a problem and tries to put the old one back, causing issues.

---

### Post by ronmarley1 on 2007-06-10
> **imog said:**
> My T43 gets stuck in a reboot loop after every time I reboot after using XP.  The message displays "Grub loading Stage1.5", it then reboots to the POST screen, displays the message again, and continues to loop.

I can allow the Grub OS list to display again by using the LiveCD and issuing some commands to restore Grub.  But after running XP again and rebooting, the same problem will reoccur.

What part of running XP is killing my Grub?  Is it XP itself?  Is it McAfee?  Is it Cisco CSA?
Same thing for me.  Started about two weeks ago.  It doesn't always happen after booting Windows, but most of the time.  I usually just use the Super Grub Disk to fix, but it's really getting annoying.  I wish I could just use Linux, but I need a couple of apps for school.  I've tried just about everything I can think of.

---

### Post by imog on 2007-06-10
> **HunkirDowne said:**
> If you have a "live" CD that does rescue you might try the following that I got here doing a search for "fdisk /mbr grub" (sans quotes):

(Insert and boot live cd)
(Enter terminal)
$ sudo grub
grub> find /boot/grub/stage1
(grub will report the location as (hd#,#) indicating the disk and partition of the location.
grub> root (hd#,#)
grub> setup (hd#)
grub> exit
(reboot)

Caveat: I have not tested this but I would try it.  Read on for my background and some advice if you have time.  Otherwise, just try the above and let me know if you get it working.

I have done the above, and it gets me back to loading the OSs, however Grub gets toasted everytime I reboot out of XP.

So it indeed works.  It just doesnt fix the source of my issue.

---

### Post by wolfen69 on 2007-06-10
ever think of downloading virtualbox? run xp in linux and you wont have these issues.

---

### Post by Shazaam on 2007-06-10
I'm still a noob when it comes to Grub but have you tried playing with the settings in menu.lst? It may have something to do with the default partition that loads first and making it stick. But be careful as I have borked my system a few times playing with it. Make sure you back it up before doing any editing.

---

### Post by HunkirDowne on 2007-06-10
Well, virtualbox shows promise from what I've read so far.  Glad to see there are enough hardcore OS/2 users out there to prompt at least an alpha.  This really might work for imog depending on what apps are needed for school.  (imog?)

---

### Post by HunkirDowne on 2007-06-10
Check out wolfen69's suggestion about virtualbox.  What apps do you need to run, if I may be so nosy?  I've been there with the school thing and had to struggle to run Windows apps in OS/2 years ago.  My best Windows app, Mathcad (for which there was no OS/2 equivalent that went public) was eventually completely broken (via upgrades) but by that time I was close enough to graduation that it didn't matter.

The only other thing I can offer is that you might want to look at the following site.  This is sort of what I had in mind of doing myself but not exactly -- he is using the NTLDR as his boot loader which can then boot Grub.  Sortof a roundabout way but NTLDR is a good enough bootmanager even if it is Windows (NT came from OS/2).


**Dual-Boot Linux and Windows 2000/Windows XP with GRUB HOWTO**
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html")

HTH!

---

### Post by ronmarley1 on 2007-06-13
> **HunkirDowne said:**
> Check out wolfen69's suggestion about virtualbox.  What apps do you need to run, if I may be so nosy?  I've been there with the school thing and had to struggle to run Windows apps in OS/2 years ago.  My best Windows app, Mathcad (for which there was no OS/2 equivalent that went public) was eventually completely broken (via upgrades) but by that time I was close enough to graduation that it didn't matter.

The only other thing I can offer is that you might want to look at the following site.  This is sort of what I had in mind of doing myself but not exactly -- he is using the NTLDR as his boot loader which can then boot Grub.  Sortof a roundabout way but NTLDR is a good enough bootmanager even if it is Windows (NT came from OS/2).


**Dual-Boot Linux and Windows 2000/Windows XP with GRUB HOWTO**
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html")

HTH!
Hey HunkirDowne,
Thanks for the suggestions.  I teach English, and our attendance and gradebook programs only run on Windows.  Since this is the school's laptop, virtualbox is not an option.  The IT office gave me special permission to use Ubuntu.  The NTLDR bootloader option works for me.  The tutorial at the link you gave works great.
Thanks to all!  Problem solved for me.

---

### Post by imog on 2007-07-04
> **HunkirDowne said:**
> Check out wolfen69's suggestion about virtualbox.  What apps do you need to run, if I may be so nosy?  I've been there with the school thing and had to struggle to run Windows apps in OS/2 years ago.  My best Windows app, Mathcad (for which there was no OS/2 equivalent that went public) was eventually completely broken (via upgrades) but by that time I was close enough to graduation that it didn't matter.

The only other thing I can offer is that you might want to look at the following site.  This is sort of what I had in mind of doing myself but not exactly -- he is using the NTLDR as his boot loader which can then boot Grub.  Sortof a roundabout way but NTLDR is a good enough bootmanager even if it is Windows (NT came from OS/2).


**Dual-Boot Linux and Windows 2000/Windows XP with GRUB HOWTO**
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html")

HTH!

Actually I support windows users at work and this is why I need a dual boot.  I can do a lot of things (consoleone, intellisync, netiq) in linux by term serving into our management server but some apps like our Blackberry Manager dont like running in a term serv environment so must run natively.  An XP machine joined to AD is also much nicer for interfacing with the sharepoint server we run also as it ties into office 2k3 and passes the auth credentials and everything, making it all pretty seamless.  I already do some virtualization with VMware, but it doesnt pop the same way running natively on an everyday workstation - itd be different if it was a machine I was just using to crunch some formulas here and there, but responsiveness is very important to me as I am getting work done directly through my machine 7 hours of my work day.  (the rest of the time I'm reading digg)

I haven't played much further with straightening things out since my last post but I will take a look at your link and post back about what my end results are.  Thanks!

---

