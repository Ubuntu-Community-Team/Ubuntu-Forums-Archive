---
title: "Unbuntu and Xp"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Seven71ne on 2008-01-23
Hey everybody, I have a question, Which im sure youve seen Before in the past, but none of them actually answered my questions.


Well How can i have Unbuntu, and Windows XP Media Edition on my computer at the same time? Ive seen it done, my brother had it for awhile, but i havent seen him for a long time. 

Heres the stuff i do in windows:
Play games like, Counter Strike Source, Call of duty 4, Bioshock etc., Search the web, msn, that sort of stuff

Now i know i cant play games on unbuntu, or atleast thats what i think. But i wasent looking to do that anyway, i really want to play with it, and when i get my laptop, ill install it on there, and use it on the laptop. 

Anyone with any links, or ideas they can help me with?

---

### Post by ahervey85 on 2008-01-23
the way i did was use gparted live cd and create a partition. you will probably have to resize xp of course to make room for a partition for ubuntu then run the live cd and install it on the second partition. im sure there are others that will have links for you as i dont right now on hand. i have vista and ubuntu running on mine. when you install ubuntu and start up your computer grub will give you a choice of booting into xp or ubuntu hope this helps

---

### Post by Mogurijin on 2008-01-23
The term your looking for is dual-booting. 

The best way to do this (short of looking up a tut) is to back-up stuff, use an Ubuntu Live CD to use Gparted to repartition your hard drive (I'd say at least 10 gigs for Ubuntu and 512 swap or more depending on your memory), and then run the installer. But please, make a backup so you don't hose your hard drive and get angry :(

---

### Post by Seven71ne on 2008-01-23
Okay, well, can i just download unbuntu, put it on a cd, and use it like a live cd? 


And what do you mean, back up my HD (right now i have nothing to loose, i can just get back) but do you mean like something else? JW!

---

### Post by Mogurijin on 2008-01-23
If you have nothing you care about then your fine. And,yeah, you can just use Ubuntu as a live CD. Just go to  [here]("http://www.ubuntu.com/getubuntu/download") and download the Live CD (not the alternate) and just burn the iso to a disc. If you need help with that, I can probably find you some instructions. ;)

---

### Post by Seven71ne on 2008-01-23
haha please find some instructions (considering this new PC didnt come with nero (something im really used to haha)

---

### Post by Mogurijin on 2008-01-23
It seems you are familiar with what isos are. So just install [_this_]("http://isorecorder.alexfeinman.com/isorecorder.htm") power toy. You may need to restart afterwards. When the power toy is installed, just pop a cd into your burner, right-click on your iso and select Copy to Disc (or something like that). Now you can just follow the wizard to burn your Live CD. Enjoy.

---

### Post by antoz on 2008-01-23
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) 

There is a lot of info about Ubuntu on the above links,A

---

### Post by zabien1970 on 2008-01-23
I've always used the links in the sticky at the top of the absolute beginner page (the last one that sasy plus install methods). It gives the links for ubuntu plus infrarecorder and how to md5sum,
Since this is an OS you don't want any corruption which md5sum checks, then make sure you burn 'as an image' as slow as possible, I think 4x is recommended

---

### Post by oni5115 on 2008-01-23
As a side note, you might also want to check out WineHQ and see if all the games you play do run in Wine without issues. I haven't had much trouble with Starcraft and World of Warcraft so far, but I have not tried Counter Strike or anything.

That said, what I've done on my laptop is 10 Gb for windows XP, 10 Gb for /, and the rest for /home.  I used the ext2/3 windows driver to access the /home directory if I need anything.   It seems to be working quite well for me thus far.  Although, I've been to busy playing with Linux to ever bother logging back into windows.  :)

---

### Post by Mogurijin on 2008-01-23
I know people take lots of precautions with operating system isos, but I've been pretty care free with them. No md5 and high speed (usually not max though). Also, I've not had  problems with corrupted disks, at least none that I know of :o

---

### Post by Seven71ne on 2008-01-23
> **Mogurijin said:**
> It seems you are familiar with what isos are. So just install [_this_]("http://isorecorder.alexfeinman.com/isorecorder.htm") power toy. You may need to restart afterwards. When the power toy is installed, just pop a cd into your burner, right-click on your iso and select Copy to Disc (or something like that). Now you can just follow the wizard to burn your Live CD. Enjoy.

I actually have no idea what isos are hah!

---

### Post by Mogurijin on 2008-01-23
Well, still follow the instructions ;). Isos are image files. They simply store all the information of a cd (such as files and stuff) in one file. I'm pretty sure you can access these individual files with various programs, but the point is, burning software (like the powertoy I mentioned) can use these isos to easily make CDs.

---

### Post by zabien1970 on 2008-01-23
> **Seven71ne said:**
> I actually have no idea what isos are hah!

its the type of file .iso

also before partitioning defrag windows, i've seen it mentioned you should run defrag 2-3 times

---

### Post by Mogurijin on 2008-01-23
2-3 times might be a bit excessive, however, this is coming from the guy who has never bothered with md5s....But just with personal experience, I have not had to defrag my hard drive before installing Ubuntu, however, it defiantly can't hurt. I could just be lucky ;)

---

### Post by jeffus_il on 2008-01-23
A .iso file is the image (an exact replica) of a cdrom or dvd.

---

### Post by Seven71ne on 2008-01-23
Ok so basicall heres what i do

1 Set restore point
2 Defrag Computer 3 times
3 Download the powertoy
4 Download the live cd
5 Burn to blank cd, at slowest rate
6 Put CD in drive
7 Shut off PC
8 Turn pc back on
9 What now? haha

I have around 140 gigs of HD Space, and 100 is free, 1 gig of ram, and a 2.99 processor

---

### Post by 565Customz on 2008-01-23
catch the bios screen and boot from cd it runs slow though

---

### Post by Mogurijin on 2008-01-23
Look toward the bottom of this thread:

[http://ubuntuforums.org/showthread.php?t=675714]("http://ubuntuforums.org/showthread.php?t=675714")

I gave a guy a quick explanation on setting up a dual-boot.

---

### Post by Seven71ne on 2008-01-23
Ok cool, im basically downloading the unbuntu file. Now, theres this beryl thing ive been seeing, kinda like XGL, how can i get this?

And what is this thing your always typing in to open things up? lol its sooo confusing!!

---

### Post by aysiu on 2008-01-23
An alternative to dual-booting is installing Ubuntu as a virtual OS inside Windows:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

