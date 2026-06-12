---
title: "Making a grub partition"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by AgelessDrifter on 2007-04-16
Here's the situation. A friend of mine borked his box recently, and after seeing my shiny new Beryl, he's decided he wants to give Linux a shot. However, he also wants to maintain a WinXP partition as a failsafe in case there's ever anything he needs it for (he games a lot).

So I reformatted and installed Windows XP on a 10 gig partition (out of a thirty gig drive) first, because, as I understand it, Windows likes to be on the first partition, for whatever reason. Then I installed Ubuntu on the remaining 20G.

When I got done with that whole process and went to boot up for the first time, I got a Grub error 18.

Looking through the forum, some have said that the problem is with an old BIOS that won't boot past 1024 cylinders. My pal doesn't know who the manufacturer for his mother-board is, as he bought the computer custom made by someone with whom he no longer has contact. Anyway, updating the BIOS is out (unless there's some easy way to find out who made the motherboard).

Another solution I've seen recommended, is to make a small partition at the start of the disk exclusively for Grub itself. That seems do-able, but what's the easiest way to go about it? The CD drive on this computer is a little old and very slow, so the LiveCD is extremely slow-running. It seems like I should install Ubuntu first, and do the rest of the meddling from there, but then Linux would have to be on the first partition instead of Windows, and I hear that's not good.

Any suggestions? All the guides I've been able to find about creating a grub partition seem a little over my head.

---

### Post by Happy_Man on 2007-04-16
Could you give a link to one of these guides? One of us may be able to translate it into English for you. ;)

---

### Post by AgelessDrifter on 2007-04-16
Sure. Here's the last one I looked at:

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

I guess the biggest confusion here is, can I do the things in that guide from the LiveCD? I wouldn't think so.

Or, if I need to install ubuntu to do the things in that guide, should I create the grub partition and a windows partition (left blank, just as a spot-holder) on the disc before the linux partition, so that I can put windows on the first partition after I'm done putting the grub partition together? Or will I still get the same error that way? 

I have only very little experience with screwing with partitions, and most of that was through Partition Magic, which I don't think will run on Linux.

---

### Post by dstew on 2007-04-16
I think what you need to do is create a /boot partition that is entirely within the first 8 Gb of the disk. Since you are just installing, the best way is to resize/move the windows partition using GParted from the Ubuntu Live CD or using a GParted Live CD, to create a small 100 Mb unallocated space to the left of the Windows partition. Format it as ext3. Then re-install Ubuntu as before, but give the 100 Mb partition the mount point /boot.

I think the issue of making a Grub partition, as found in the link above, is not what you need to do.

---

### Post by AgelessDrifter on 2007-04-16
Okay, I did all that, and I'm about to click "forward" to go through with it, but I wanted to double-check:

It's telling me Grub will be installed on (hd0). The 100mb partition I created at the beginning of the disk and gave the /boot to is called (hda1). Do I need to change (hd0) to (hda1)?

---

### Post by AgelessDrifter on 2007-04-16
:confused:

---

### Post by dstew on 2007-04-16
No, that is perfect. (hd0) is grub's way of naming /dev/hda, which is a disk. /dev/hda1 is a **partition** on the disk, and you do not want grub to go there. When grub tells you it will install in (hd0), that means it  will install into the MBR of the first disk, which Linux names /dev/hda, which is what you want. Your boot partition is /dev/hda1, which is (hd0,0) in grub-speak, just for your information.

---

### Post by NicoleM on 2007-04-16
hd0 will install it to the MBR

hd0,0 will install it to the first disk, first partition (aka hda1)

it sounds ot me like you want the second of the two options since you made a partition specifically for grub, but i'm no grub expert... (unless you're no longer following the grub partition walkthrough that you linked above)

---

### Post by mrpeenut24 on 2007-04-16
I'm not even sure you should need a separate partition for grub.  I do a lot of meddling with partitioning, and have NEVER had to make a separate partition for grub.  I've always simply put it on hd0 (the MBR of the first disk) and had the other partitions go from there.  This has always worked for me, in ubuntu, suse, and freebsd.  And I've worked with some pretty old computers.

---

### Post by nyquist on 2007-04-17
IIRC some Linuxs install with a separate Boot partition, I think that happened when I tried to install SUSE many years ago. AFAIK you don't need this with Ubuntu.

If you just reduce the size of your windows partition, then Ubuntu should install OK in the free space. 
Ubuntu will provide you with a multi-boot menu.

A useful utility is a program called 'SuperGrub'.  It will make a bootable CD or floppy which can usually boot unbootable systems and restore lost boot commands.    A Google search should find the program.

---

### Post by aberry5555 on 2007-04-17
This might help to update the bios, its a program that runs in XP, once you've installed it you can open it and it should give you all the details about your motherboard or whatever else you need to know about.

here's the link: [http://www.majorgeeks.com/download4181.html](http://www.majorgeeks.com/download4181.html)

p.s. sorry for giving XP help in Ubuntu forums :p

---

### Post by Innomado on 2007-04-17
I had to find a copy of Super Grub on Saturday. Here's the link that I used.
[http://sgd.linux-beginnerforum.de/index.php](http://sgd.linux-beginnerforum.de/index.php)

The site is in German but just click on download and you should see the link towards the bottom of the page.

---

