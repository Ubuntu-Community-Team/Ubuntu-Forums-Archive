---
title: "I am a noob :P"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by Dark_X on 2007-07-24
I am a noob and I want to try linux but I don't know what I should do.  I just started downloading ubuntu.

---

### Post by Jellyffs on 2007-07-24
Once downloaded, just burn it. Then boot your PC on the CD. You might need to tell your BIOS to do so.

---

### Post by kevinlyfellow on 2007-07-24
Excellent!  On the ubuntu download page there should be instructions on how to burn you download onto a cd.  Once you do that, just make sure your bios is set to boot off of the cdrom and restart the computer with the cd in the drive.  It will boot into linux off of the cd so you can see how everything works before you install it.

Here is a howto for burning your disk
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Rocket2DMn on 2007-07-24
You are going to want to burn the .iso image to a cd.
Before that you should check the md5sum on the image file to make sure it downloaded correctly.
[HowTo]("https://help.ubuntu.com/community/HowToMD5SUM")
[Hashes]("https://help.ubuntu.com/community/UbuntuHashes") to check against
Once that checks out, you can burn the image to a cd, but you should do it at a slow speed, like 4x, to decrease the chances of a bad burn.  You should also use quality media if you can, not dirt cheap stuff.
You'd be surprised how many problems following these steps solves.

Once you have that boring stuff out of the way, you can restart your computer and boot from the LiveCD!  You can check out the system, surf the web, and lots of other cool stuff.  You can also use the CD to install Ubuntu, but there are steps you should take before doing this.  Ask about that if you want to install Ubuntu.

---

### Post by por100pre1 on 2007-07-24
Just keep in mind while using the Live CD that Ubuntu won't run very fast... beacuse it won't touch your hard disk at all.

---

### Post by WarholsGhost on 2007-07-24
you might need a bit more information.

First off welcome, you will enjoy it, but the first thing you need to remember is Ubuntu IS NOT WINDOWS!! so don't try to make it be something it's not, and if its difficult or frustrating just remember you are relearning something new when before you were using a system you have been using a very long time

as for the downloading ubuntu, what you are downloading is a cd image file which acts like a cd. you need a image burning program (try to find a free one, i used to use alcohol 120% before i switched to ubuntu). Once you do that take the iso image file and burn it to a disk. This disk will be not only the install disk but a live cd meaning when you boot from the cd rom you can use ubuntu (but it runs off the cd rom drive as opposed to your hard drive). you must boot the cd to install ubuntu. the icon will be on the desk top when you boot and the installation process is really simple. 

i hope that is helpful, come here with questions

---

### Post by Dark_X on 2007-07-24
Am I going to need to download any drivers or anything?  The only internet connection I have is wireless.  The adapter is a D-link WDA 2320. I checked their website and they don't have drivers for linux.

---

### Post by dylan623 on 2007-07-24
> **Dark_X said:**
> Am I going to need to download any drivers or anything?  The only internet connection I have is wireless.  The adapter is a D-link WDA 2320. I checked their website and they don't have drivers for linux.

That could be a problem. Try using ndiswrapper, but if it takes you more than a week, just buy a new wireless card. (a compatible one)

---

### Post by kevinlyfellow on 2007-07-24
> **Dark_X said:**
> Am I going to need to download any drivers or anything?  The only internet connection I have is wireless.  The adapter is a D-link WDA 2320. I checked their website and they don't have drivers for linux.

Actually according to a review on newegg, it has great linux support.  I don't know much about wifi drivers (never had to deal with them much) but your card is supported by the madwifi drivers, which I don't know if it is supported out of the box in ubuntu.

---

### Post by doomster on 2007-07-24
welocme . i dont wanna get you "feared" with linux, but wireless is  a pain in the ***. . i dont thing with dlink adapter you will have a problem. for most of your downloads, a wireless connection , as my personal beliefe, is enough:)

---

### Post by Dark_X on 2007-07-24
Can I burn this iso on a dvd?  I don't have any cds and I won't be getting any soon.](*,)

---

### Post by doomster on 2007-07-24
yes i dont thing you will have a problem:) just use the " Burn cd image " option of your recording utility :)
and USE THE LOWEST SPEED AVAILABLE, to avoid any read errors during the installation

---

### Post by Rocket2DMn on 2007-07-24
Yeah, it should be able to work. If it doesn't work, you didn't hear it from me ;)

---

### Post by Dark_X on 2007-07-24
I just remembered... Is 64 bit going to make things harder for me?:-k

---

### Post by doomster on 2007-07-24
i dont thing 64bit is gonna make anything harder :)

> **Rocket2DMn said:**
> Yeah, it should be able to work. If it doesn't work, you didn't hear it from me ;)

u have used several other distro's live cd's burned on a dvd instead. i dont find a reason why ubuntu shouldnt work :) so dont worry:)

---

### Post by Rocket2DMn on 2007-07-24
There are entirely too many smilies on this page
:lolflag:

---

### Post by sci-fi guy on 2007-07-24
It (64-bit) shouldn't be a problem, for the most part. Flash will be an issue after you install. [Try this.]("http://ubuntuforums.org/showthread.php?t=476924") Worked like a charm for me. ;)

---

### Post by doomster on 2007-07-24
:) thats because we are happy to help ppl get around:)furthermore we re happy to share the spirit of ubuntu:)

---

### Post by Dark_X on 2007-07-24
> **doomster said:**
> :) thats because we are happy to help ppl get around:)furthermore we re happy to share the spirit of ubuntu:)

Since your happy to help people...:mrgreen:  I also want to dual boot with my vista.  Can I  (or do I have to) keep the vista boot manager?

---

### Post by Rocket2DMn on 2007-07-24
> **Dark_X said:**
> Since your happy to help people...:mrgreen:  I also want to dual boot with my vista.  Can I  (or do I have to) keep the vista boot manager?

You should be able to use GRUB, the boot manager that comes with Ubuntu.  You need to be sure you have enough free space on your drive thought, and the newer the windows installation, the better.
You need to defragment your windows partition as best you can so you can add the ubuntu partition to the end of the drive when you install from the LiveCD.  You will need enough room for the SWAP as well.

Please make sure you have backups of your files and whatnot before you start.

---

### Post by sci-fi guy on 2007-07-24
I dual-boot w/Vista, but I do not use Vista's boot manager. I just resized Vista's partition and installed in the new space. Ubuntu never mentioned Vista during the install, but is available to boot from when I start up. Also, I recommend that you create a separate /home partition to recover from crashes.

---

### Post by lepz on 2007-07-24
> **Dark_X said:**
> I just remembered... Is 64 bit going to make things harder for me?:-k

Not trying to put you off but I would seriously think of downloading x86 for now, because you will have alot of issues with flash.

---

### Post by Jellyffs on 2007-07-24
> **lepz said:**
> Not trying to put you off but I would seriously think of downloading x86 for now, because you will have alot of issues with flash.

I agree.

---

### Post by Dark_X on 2007-07-24
> **sci-fi guy said:**
> I dual-boot w/Vista, but I do not use Vista's boot manager. I just resized Vista's partition and installed in the new space. Ubuntu never mentioned Vista during the install, but is available to boot from when I start up. Also, I recommend that you create a separate /home partition to recover from crashes.

Can ubuntu read ntfs?  I already have a 8GB partition that I use for backup files.  What size partition/partitions should I make. I have a 180GB hard drive so space isn't a problem.

---

### Post by Rocket2DMn on 2007-07-24
> **Dark_X said:**
> Can ubuntu read ntfs?  I already have a 8GB partition that I use for backup files.  What size partition/partitions should I make. I have a 180GB hard drive so space isn't a problem.

Yes, you will need to install ntfs-3g.

---

### Post by benx009 on 2007-07-24
> **doomster said:**
> yes i dont thing you will have a problem:) just use the " Burn cd image " option of your recording utility :)
and USE THE LOWEST SPEED AVAILABLE, to avoid any read errors during the installation

this is an important rule to follow, but i've burnt all my linux distros at max (52x) and have never ran into problems:)  envy me

---

### Post by sci-fi guy on 2007-07-24
> **benx009 said:**
> i've burnt all my linux distros at max (52x) and have never ran into problems:)  envy me

Ditto :-#

---

### Post by Dark_X on 2007-07-24
I tried the disc about an hour ago and... lucky me, it didn't work.  10 min after it says "booting the kernal" the screen goes blank.  Is it a graphics driver problem?   What should I do?

---

### Post by sci-fi guy on 2007-07-25
Try the "Check for errors" option or whatever it is called at the bottom of the disc's menu and report back. How did you download the ISO? Bittorrent? HTTP? If you downloaded via bittorrent, I suggest that you have your bittorrent client check for errors. If you downloaded via HTTP, you need to compare the md5 checksums.

To check md5sums in Windows, download [this]("http://www.pc-tools.net/win32/md5sums/") or [this]("http://www.md5summer.org/"), find the ISO's md5sum wherever you downloaded it from, and compare the md5sum with the one generated by either one of these programs. If they do not match, you are out of luck and have to download it again.

Actually, you might be able to install [Bittorrent]("http://www.bittorrent.com/download") or some other bittorrent client, move the ISO to the download destination folder (I think it is in My Documents), find a torrent file [here]("http://torrent.ubuntu.com:6969/") that has the same name as your ISO, and download that and run Bittorrent. It should find any corrupt chunks and redownload just those chunks.

---

### Post by Lord Illidan on 2007-07-25
If you are using good media, then 52x shouldn't be that much of a prob.

---

### Post by Dark_X on 2007-07-25
Sorry I should have told you I fixed the problem.  The problem was the screen resolution.  It was to big for my screen.:lolflag:
Although I am now having another problem: [http://ubuntuforums.org/showthread.php?t=509353](http://ubuntuforums.org/showthread.php?t=509353)

---

