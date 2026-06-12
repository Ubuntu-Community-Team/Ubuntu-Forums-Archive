---
title: "Dual Boot? I'm Clueless..."
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by KudoKid on 2007-12-22
I consider myself to be pretty good with computers,but honestly, I have no idea how to go about dual booting. how would i go about doing it?

Heres the main idea. I have ubuntu on my computer, with a 250 gig hard drive, and i want to dual boot XP. Now, from my perspective, dual booting means when i turn my computer on, i choose which OS to boot, is this correct?

Now a few questions.
Ubuntu is immune to viruses and malware, however XP is far from immune. Now, I never had malware or viruses on XP before i switched to ubuntu, so this isnt a bit issue for me, but if somthing happens on XP, will ubuntu be effected too?

Lastly i want to ask, If i have files on ubuntu, is there a way to access them through windows? Such as music, videos, just general media.

Thanks a ton to all who help me out. I hope to do this tonight, but tomorrow will do fine if it takes a while.
Thanks again. 
Love & Happiness -- KudoKid

---

### Post by Flyingjester on 2007-12-22
If something happens to xp, your ubuntu install should be unaffected. 
and there are some programs to do acess files [http://lifehacker.com/software/featured-windows-download/access-linux-files-from-windows-with-linux-reader-334535.php](http://lifehacker.com/software/featured-windows-download/access-linux-files-from-windows-with-linux-reader-334535.php) is just one possiblity. (didn't read too indepth on it, but seemed to be worth looking at)

---

### Post by wormser on 2007-12-22
The first thing you need to do is start downloading the Ubuntu .iso file.  The read threw this [site]("http://www.psychocats.net/ubuntu/index.php").  It answers a lot of noob questions like how to burn an .iso as an image.  Ubuntu is not going to be effected by virus.  You will also be able to move files between both.  Search the forum for NTFS-3g.  Don't be afraid to ask any questions here.  This is a great community with lots of people willing to help.

---

### Post by Mark_in_Hollywood on 2007-12-22
> **KudoKid said:**
> I consider myself to be pretty good with computers,but honestly, I have no idea how to go about dual booting. how would i go about doing it?

Heres the main idea. I have ubuntu on my computer, with a 250 gig hard drive, and i want to dual boot XP. Now, from my perspective, dual booting means when i turn my computer on, i choose which OS to boot, is this correct?

Now a few questions.
Ubuntu is immune to viruses and malware, however XP is far from immune. Now, I never had malware or viruses on XP before i switched to ubuntu, so this isnt a bit issue for me, but if somthing happens on XP, will ubuntu be effected too?

Lastly i want to ask, If i have files on ubuntu, is there a way to access them through windows? Such as music, videos, just general media.

Thanks a ton to all who help me out. I hope to do this tonight, but tomorrow will do fine if it takes a while.
Thanks again. 
Love & Happiness -- KudoKid

1) You will, once Ubuntu is installed be given a choice of which OS to boot into.
2) Not likely, unless the MBR is sickened by the virus, BUT, since we have both Ubuntu LiveCD as well as SuperGrub (q.v., below) you will be able to easily repair the MBR, GRUB and boot-time files.
3) It could not be easier just a few keystrokes, cut & paste and you will have both disks "talking" to each other. 

Please read, understand and follow the directions at these sites and do come back here with a fresh post to ask questions BEFORE you start, if you are uncertain or curious.

Installing a Dual-Boot with Windows and Ubuntu
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

and

Super Grub Disk Documentation Page
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Let us hear back from you about how it went. And lastly, do make written notes about each step you take, in case you need "emergency" help.

Welcome to Ubuntu

---

### Post by Moop on 2007-12-22
Yes dual booting means just what you think it does. The preferred method is to install XP first and then Ubuntu but there are guides for doing it the other way. 

If XP were to get infected with a virus it wouldn't pass it on to Ubuntu but Ubuntu could pass a virus to XP without being infected itself. There is anti-virus for linux if you feel you need it. 

Ubuntu can read and write to your windows partition but I don't think XP will recognize your Ext3 file system. You can create a separate partition that's fat32 or similar that both windows and linux can use. I could be wrong about this so double check my advice. :popcorn:

---

### Post by KudoKid on 2007-12-22
Okay i have to say this, lol. I already have ubuntu as my OS, i want to add XP, is it the same thing? i have the windows disk...

---

### Post by bodhi.zazen on 2007-12-22
Dual booting is quite easy, I wanted to address security.

Security on Linux has a few thing in common with Windows, but there are many differences.

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by jken146 on 2007-12-22
fs-driver.org for a windows driver for ext2 filesystem

---

