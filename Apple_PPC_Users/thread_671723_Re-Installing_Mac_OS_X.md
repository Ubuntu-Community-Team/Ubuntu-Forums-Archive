---
title: "Re-Installing Mac OS X"
date: 2008-01-18
forum: Apple PPC Users
---

### Post by Dr.Greenmac on 2008-01-18
I have just installed UBUNTU on my ibook G4, but the results arent what I spected.
I really like Ubuntu, in fact, my principal computer which is a PC uses ubuntu, and im not planing to leave it. but I dont wanna use it on these ibook so....
What should I do?  
1. just put the install dvd of Mac OS X 10.4 and EVERYTHING will work fine
2. or should I  format the drive first ??

There is no problem by reinstalling the OS X? did ubuntu did somerhing bad to my HD that now Im not gonna be able to install Mac OS X never again??

Thanks in advance pals!

seeya

---

### Post by pytheas22 on 2008-01-18
I've never used OS X but I'm pretty sure that there's no reason that you wouldn't be able to just put in the installation disk and have it wipe out Ubuntu.  It will probably just reformat the drive itself; no need for you to do it beforehand.  But maybe someone who has actually installed OS X over Ubuntu could confirm.

---

### Post by tgalati4 on 2008-01-18
If your disk still has HFS+ then you are fine.  Although you can install OS X on ext3, it is recommended to use Apple's HFS+ file system.  You can see your file system type by using gparted.

I agree with you, I tried Ubuntu on a powerbook and it just can't compare in functionality to Tiger.  I have 152 days of uptime on my powerbook running Tiger and everything works.  I like Ubuntu on x86 hardware, but for powerbook G4's Tiger is king.

I would reformat the drive.  I've never had to reinstall Tiger, but I assume there is a formatting utility on the install DVD.

---

### Post by stream303 on 2008-01-19
I've done this more than I care to admit. :)

You should have no problem, just hold down the "C" key when you boot the OSX install disk and away you go.

However, before you start to click all the install options after the OSX install disk has booted, you have the option of running Disk Utility first before the actual install.

If you had any private data on the drive, you can do some simple or extensive disk-wiping first.

If you ever envision trying Linux again on the Mac, instead of letting the install overwrite the whole disk, you can use Disk Utility to partition the drive into something smaller.  In my case, I just partitioned my drive in two so that I could dual-boot either OSX or any flavor of linux.

If you do it now, you won't have to go through 3rd party OSX utilites to repartition your active drive should you want to dual boot at a later date...

In my case I reinstalled Tiger and then followed up with the latest Apple combo-update, etc, although I think I have finally given in to Gutsy full time.

---

### Post by Dr.Greenmac on 2008-01-19
Thanks U very much for your quick answers! ill try to just put in the install dvd and began the instalation like U  told me guys.

Thanks!!

---

### Post by Dr.Greenmac on 2008-01-19
Hey, Im waiting for a friend to give me back my Mac OS X 10.4 install DVD, so mean while y decided to try to install Mac OS X 10.2 with some cds ive got. when I booted from the fist CD the gray screen with the apple logo ¨ loading screen" apeared but, like 5 sec, then it gets stucked and goes no where like kind of something is wrong, so I think about 3 thing:

Is my hard drive damaged?
Is the Disc im using damaged?
Is my computer not able to support that OLD MAC OS X 10.2?

So, im just waiting for the install DVD to make the real shot but I decided to take a screenshot of my Gparted showing my partitions ¨ partitions that i didnt make, cause when I installed ubuntu I just hit USE ENTIRE DICK¨.
So please tell me if some thing is wrong or should i dont worry that much? im really scared about my HD i dont know why I have the idea in my head like kinda saying ¨ YPU SCREWD UP YOUR HD AND YOU WILL NEVER BE ABLE TO INSTALL MAC OS X !! ¨

So please tell me if im wrong!

[IMG]http://i57.photobucket.com/albums/g231/ilvanroot/Screenshot--dev-hda-GParted.png[/IMG]

Thanks!

---

### Post by stmiller on 2008-01-19
If you are going to do a clean install of OS X, I would remove all of those partitions you see in gparted. And leave the entire disc as raw, unformatted space.

---

### Post by Dr.Greenmac on 2008-01-19
But...how can i do that if they are mounted cause are the ones that linux use??
note: my live cd doest work my ibook.......

---

### Post by VidiotGeek on 2008-01-20
> **Dr.Greenmac said:**
> But...how can i do that if they are mounted cause are the ones that linux use??
note: my live cd doest work my ibook.......

Ok. First, breathe. No need to get freaked out. You're not likely to screw up your disk beyond repair. I won't say it's impossible, but you're definitely more worried than you need to be. First, don't waste your time with OS X 10.2, (Jaguar) unless it's the ONLY option you have while you wait for your Tiger disk. I'd say to at least use Panther (10.3) or just wait until you get the Tiger disk. That first partition you see in black is the bootstrap partition. This is a partition on Macs (with the PowerPC chip at least) where the bootloader sits, be it Apples loader or Yaboot for a Linux or Dual boot system. Nothings wrong.

When you boot from the Mac OS X CD, their should be a menu at the top for utilities or something, I forget what it's called. Open "Disk Utility" & select your internal HD, then click the Erase tab. Format it as HFS+ & you're ready to reinstall Mac OS X.

Note: If you're pretty sure that you'll want to dual boot Linux at a later point in time, I would recommend making 2 partitions at this point, as others have mentioned. To do this, just go to the Partitions tab instead, Format partition 1 as HFS+ & partition 2 as Free Space. This is exactly how I set up my dual boot & with a bootable SuperDuper clone of my Mac OS X install on an external FireWire drive, I can completely wipe my internal drive, & have both Mac OS X & Linux back on it in an hour or two.

---

### Post by Dr.Greenmac on 2008-01-20
Hey dude THANKS!!!! Il just wait for my tiger DVD and make a clean instalation of mac os X.......

Seeya

---

