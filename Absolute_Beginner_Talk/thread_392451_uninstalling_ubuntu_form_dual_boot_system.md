---
title: "uninstalling ubuntu form dual boot system"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Cipher Short on 2007-03-24
Hello again. I have found myself at an unavoidable juncture in my short Ubuntu life. I need to remove it from my second hd so I can have it for another puter. I would like to reinstall it after I put another hd in this machine but thats later. Right now I have scanned the forum for advice. I tried to run my windows install cd to fix the boot loader before uninstalling Linux, problem being as with so many windows products (especially bundled products, like my operating system set up for just this puter, when I tried to get into the recovery portion of the dis it only gave me two options: destroy it all and reinstall or its so called "safe" restore where it "safely saves your info" and reinstalls the operating system. Problem is its windows so you know that doesn't work, never saves anything just gives me a clean operating system. Not a problem if you don't have anything you want to save but I do, alot of stuff I have dwnlded and user data I want to keep. Some of the advice said if windows could find the hd I put it on it could reformat it and take care of the GRUB issue, wrong, restarting causes grub stage 1.5 to kick back "error 17". Fact is Im tired of this and stressed out. All I want is my computer to boot win XP and my other hd ready to be placed in another computer. No one ever told me when I was first setting this thing up in dual boot format it would be this difficult and Im just not smart enough to figure it out on my own. I don't want to give up on Linux I just need to get it off this hd, get windows on it and get another hd in here to run Linux. Instead I just want to go on a murderous rampage and destroy everything I see. Please help me before its too late for me, my family, and central Wisconsin !

---

### Post by rsambuca on 2007-03-24
You will need to get a hold of an actual Windows installation disk to run the command 'fixmbr'.  It doesn't matter which version of Windows disk you use.  The recovery disks that you get with many preinstalled systems will not work.

---

### Post by haricharan on 2007-03-24
Do you have a recovery Disk or a reinstallation disk? .... What brand is your computer. I believe the HP-Compaq comes with Recovery Disks only. You cannot use them to run recovery commands in Windows...What it does is just recovers the system back to original state leaving the non NTFS/FAT partitions as it is.

---

### Post by Cipher Short on 2007-03-24
:mad: yea see thats part of the windows problem, most computers now a days seem to only come with the stupid "recovery cd" whats there to recover if you just want an operating system! I have a copy of 98 that came with my old puter, will that work? A person could alway pirate a copy of something like xp, or xp pro, would that work? Not that I would do that but would it work?

---

### Post by rsambuca on 2007-03-24
I believe the Win98 disk will work.  There should be a recovery mode when you boot from it, and then just run the command:  fixmbr

---

### Post by confused57 on 2007-03-24
See this link for uninstalling Ubuntu:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

or you can use the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Cipher Short on 2007-03-25
ok, tks 4 the help so far. I have managed to get my puter to boot just windows xp :( however it still will not allow me to remove the second hd. It is reformated back to ntfs but it happened to do it in 2 partitions that both have a little unknown (to me at least) used space on them. Why wont it let me remove the hd? TIA :)

---

