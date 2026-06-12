---
title: "Dual boot with Win XP - but no XP disc"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by trishacupra on 2007-03-31
Hi,

This is my first post. I'm a Windows power user who really wants to ditch Windows and I'm hoping Ubuntu is the Linux distro for me.

I have a Compaq Presario V2000 widescreen laptop. I bought it with Windows XP Home pre-installed, but it didn't come with the Windows installation disc. Instead, there is a partition with System Recovery stuff on it, and I created PC Recovery discs (it used 10 CDs!).

On the bottom of my laptop there is a sticker which proves my Windows is genuine and has a Product Key, which I assume is the serial number.

I want to set up my laptop to dual boot Win XP and Ubuntu. Eventually I want to get rid of Windows altogether (hopefully sooner rather than later).

But because I don't have a Win XP disc, I'm worried about not being able to reinstall Win XP if things get messed up. (Just as a back-up plan.)

Does anyone know if I can use my serial number/ product key with any XP disc? Or, could I just use my System Recovery discs to reinstall Windows if things go pear-shaped?

Also, I've gotten the impression that I can install Ubuntu to dual boot on my laptop with XP already installed, and the Ubuntu disc lets me create a new partition to run Ubuntu on. Or, do I need to reinstall Win XP fresh from the disc in the process? I've removed all my data from my laptop hard drive (which is only 40GB) to an external hard drive (my Dad taught me to keep my OS on a separate drive from my data). So, I'm not worried about losing any important files.

I know this is really more of a Windows question, and that I could ask Compaq this question. So, sorry if this question is out of place here. I'm hoping for a quick answer from someone who has been in a similar situation here. 

Thanks in advance for any advice.

Trisha

---

### Post by K.Mandla on 2007-03-31
Hi Trisha, welcome. 

First, it's my understanding (and I might be wrong; someone correct me if I am) that the product key is what is actually licensed to you. So it doesn't matter if you use your original XP installation disc or a backup disc or an XP disc borrowed from a relative. So long as the serial number you provide is the one assigned to that computer, it doesn't matter.

Personally, I've had rotten luck with the recovery discs that Dell sometimes "makes" with their recovery software. It may have changed recently, and it may be a Dell thing, but invariably I get a bunch of software I didn't want or consider bloatware -- when all I wanted was a clean XP install. I can't speak for Compaq, but I would recommend looking for a proper clean XP install disc.

All that being said, you can install Ubuntu on a preinstalled version of Windows; just defragment your drive and resize the XP partition to leave an unformatted, unpartitioned area for Ubuntu. The guided partitioner should do the rest. 

Let us know if you have problems, or more questions. :)

---

### Post by HellSpawn on 2007-03-31
If you have your Recovery Discs then your OK, you can go back to Windows just booting from those disks, and you'll have your Laptop as good as new. Can you make DVDs instaed of 10 CDs?? if not make at least one more Set of those just in case, or do not delete the Partition with the Recovery data, your laptop should know how to restore from it.

You can Install Ubuntu in a dual boot with XP, the Ubuntu Installer will guide you on how to partition your hard drive.

Remember to backup your stuff first.

Good Luck

---

### Post by SilverZero on 2007-03-31
Whoops, see below.

---

### Post by SilverZero on 2007-03-31
Also, be aware that Linux will try to install GRUB to the MBR, which may or may not be a concern to you. I just know that I've had a lot of problems in the past with getting rid of a bad Linux install, and being unable to boot into Windows after that (usually had to go through some fixmbr routines).

Tips if that happens to you: Make sure only one partition is active (probably the Windows partition), make sure the MBR is restored, make sure ntdetect, ntldr, etc. are all in your root ( C: ) directory.

What I do now is install GRUB in a small (50-100mb) /boot partition at the beginning of my primary HD. If you do that, make sure the /boot partition is active and it should work.

Of course, I'm a perennial newbie, too, so anybody can correct me if I'm off-base. :)

---

### Post by trishacupra on 2007-03-31
oops - double post.

---

### Post by trishacupra on 2007-03-31
Wow, you guys are fast! I know I'm going to enjoy being part of this community. :KS 

Thanks for the advice. 

@K.Mandla: That's what I was thinking about the product key. Just want to be sure, though. Thanks for the reminder to defragment.

@HellSpawn: I don't have a DVD burner in my laptop, but I have an external DVD burner drive, so I can make another copy of the recovery discs - I think it uses 4 DVDs or less. I'll do that just in case. I didn't have my DVD burner set up when I made the first set of discs. And I'll leave the recovery partition on my hard drive - I'm only using the laptop's hard drive for the operating systems, and an external hard drive for my data. So, everything is already backed up and out the way. 

Thanks so much,

Trisha

---

### Post by perspectoff on 2007-03-31
You can, if you choose, defragment your hard drive so that all the files are (hopefully) placed at the beginning of your NTFS partition that Windows XP resides on. Then, while using the Ubuntu installer disk, you can "shrink" the NTFS partition so that it more closely resembles the area where there is actually data. (Windows usually uses your entire hard drive for its NTFS disk by default.) You usually don't want to touch the system recovery partition, which is generally small (only a few GB).

This isn't foolproof, of course, because some software programs using copy-protection in the form of data placement in "absolute" hard-drive locations. This data cannot be moved during de-fragmentation attempts or the software will become unusable. Since any data that is not moved during defragmentation will be written over when a new partition is created, it will be lost. That particular piece of software would likely then be non-functional.

That is why it is always safest to create a dual-boot system from scratch.

Yes, the license key will work when you re-install Windows, but OEM version license keys are restricted to the original hardware configuration and the identical version of Windows OEM. You probably could not use the license key with a "retail" version of Windows XP Home if you have an OEM version of Windows XP Home, for example. But, I'd love to be corrected. 

Once the NTFS partition is "shrunk"  you can create a new partition for Ubuntu. Note that this is fairly easily to do with the graphical partition manager that is part of the Ubuntu installer.

I would not worry about GRUB. I have never had a problem with it in 7 dual-boot installations. 

Also, you can indeed buy Windows XP OEM discs inexpensively these days, if you really need a back-up plan.

P.
[http://www.geocities.com/perspectiveoffice](http://www.geocities.com/perspectiveoffice)

> **trishacupra said:**
> Hi,

This is my first post. I'm a Windows power user who really wants to ditch Windows and I'm hoping Ubuntu is the Linux distro for me.

I have a Compaq Presario V2000 widescreen laptop. I bought it with Windows XP Home pre-installed, but it didn't come with the Windows installation disc. Instead, there is a partition with System Recovery stuff on it, and I created PC Recovery discs (it used 10 CDs!).

On the bottom of my laptop there is a sticker which proves my Windows is genuine and has a Product Key, which I assume is the serial number.

I want to set up my laptop to dual boot Win XP and Ubuntu. Eventually I want to get rid of Windows altogether (hopefully sooner rather than later).

But because I don't have a Win XP disc, I'm worried about not being able to reinstall Win XP if things get messed up. (Just as a back-up plan.)

Does anyone know if I can use my serial number/ product key with any XP disc? Or, could I just use my System Recovery discs to reinstall Windows if things go pear-shaped?

Also, I've gotten the impression that I can install Ubuntu to dual boot on my laptop with XP already installed, and the Ubuntu disc lets me create a new partition to run Ubuntu on. Or, do I need to reinstall Win XP fresh from the disc in the process? I've removed all my data from my laptop hard drive (which is only 40GB) to an external hard drive (my Dad taught me to keep my OS on a separate drive from my data). So, I'm not worried about losing any important files.

I know this is really more of a Windows question, and that I could ask Compaq this question. So, sorry if this question is out of place here. I'm hoping for a quick answer from someone who has been in a similar situation here. 

Thanks in advance for any advice.

Trisha

---

### Post by trishacupra on 2007-03-31
@SilverZero: Thanks for your tip, though a lot of it doesn't make much sense to me yet. Is there step by step instructions/explanations anywhere on how to do all that, being:

How to make sure only one partition is active. (What does 'active' mean?)

How to make sure the MBR is restored. (What is the MBR?)

How to make sure ntdetect, ntldr, etc. are all in your root ( C: ) directory. (Probably couldn't recognize something like ntldr if it smacked me in the face at this stage.)

How to install GRUB in a small (50-100mb) /boot partition at the beginning of the primary HD. (I kind of understand "why" I should, but wouldn't know "how" to even begin doing it.)

How to make sure the /boot partition is active. (Back to the first question - define 'active'?)

I really want to learn and understand this stuff.

Thanks,
Trisha

---

### Post by trishacupra on 2007-03-31
> **perspectoff said:**
> 

...That is why it is always safest to create a dual-boot system from scratch...

...I would not worry about GRUB. I have never had a problem with it in 7 dual-boot installations... 

...Also, you can indeed buy Windows XP OEM discs inexpensively these days, if you really need a back-up plan...



Thanks very much. I'm starting to understand much better. And yes, I could just get an XP OEM disc off eBay. But hopefully I never have to pay for an OS again - especially when I've already paid for it when it came with my laptop.

---

### Post by SilverZero on 2007-03-31
> **trishacupra said:**
> @SilverZero: Thanks for your tip, though a lot of it doesn't make much sense to me yet.

There's a wealth of info all over the Internet about dual booting, partition schemes, etc. That's where I learned it all (I don't know everything, by any means). [Here's a page I always seem to go back to when I'm fiddling with dual-booting.]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html") What he did is what I did - existing XP installation, /boot partition on the first 100mb of the primary hard drive, all that. Do some Googling for "MBR" and such if you need some more background.

When I installed Ubuntu yesterday, I had to specify where I wanted GRUB installed. I said "hd0,2" which means to install it to the first hard drive (hd0) on the 3rd partition (the 2). NOTE: Linux numbering starts at 0, i.e. 0,1,2,3. . ., NOT at 1. So the first hard drive is hd0, the second (if you have two) is hd1. Keep that in mind when you're dealing with partitions. Even though my /boot partition is at the very beginning of the drive, it was the third partition I made on that drive, so it's numbered that way. I don't know why it works that way, but it does, and if you end up moving your XP partition to make room for a /boot partition at the beginning, you'll need to remember that, too.

GRUB installed fine, but when I booted back up, I got an "Invalid Partition Table" error. I figured out that it was because there was no active partition flag on the primary hard drive, and I'm not sure why it got turned off. Hard drives can have either active or inactive partitions, and as far as I know, it only matters when starting up. The active partition is the one that the BIOS is directed to, and it usually needs to have the instructions for booting the desired operating system - that's the bootloader (GRUB or LILO in Linux, NTLDR for Windows 2000 and later). I'm thinking a lot of problems I used to have with not being able to boot Windows after trashing a Linux install had to do with not having the right partition active. Now I know to check. I have a boot CD called the "Ultimate Boot CD," but I don't remember where I got it. It has a few filesystem tools on it, including some that can let you go in and change which partitions are active. I had to make sure that my /boot partition (where GRUB is installed) was active, so the computer knew that's where it was supposed to look for booting instructions. I hope that makes sense.

The reason I do all this is because I've had problems with GRUB installing to the MBR, which is where Windows likes its own bootloader (NTLDR) to be if there's no other instructions, and Windows is finicky, so it just doesn't work when it doesn't get what it wants. Now, I'm a lover *and* a fighter, but when it comes to Windows startup, I just do what it wants. It's basically all the same in the end, so why not keep things separate?

If you ever fry Linux and just need to get into XP, and there IS a problem with your MBR (like, your screen says something like "NTLDR missing" or something), use a boot disk or boot CD to make sure that the XP partition is active, and if that doesn't work, you will need an XP CD to run "fixmbr" or "fixboot" - more info from Google whenever you need it.

Hope that helps a bit. Like I said, I don't know a whole lot myself, just what I've screwed up and how I remember fixing it. I relied heavily on the guides I found from Google, so you should have even more resources at your fingertips. 

Good luck, and have fun! Everything I've learned about computers in the last decade has come from me just trying things and having to learn how to fix them. I've never lost critical files, even when I've had to reinstall Windows from scratch (I found some great data recovery tools), but that doesn't mean it can't happen. Knowing your pitfalls ahead of time helps, and sometimes necessity is the driving force behind the really good learning. I hope it all goes smoothly for you.

---

### Post by SilverZero on 2007-03-31
By the way, one of the most stressful parts of when I followed that guide was getting the /boot partition in front of the existing XP partition. I had to move the entire thing back 100mb, which takes forever, and is potentially detrimental. I don't know if that /boot partition NEEDS to be at the front end of the drive, if you have a relatively newer system, but maybe you could just try sticking a small 100mb partition AFTER your primary partition, and see if it works (check the active partition info, too - Ultimate Boot CD is great!). If it does, so much the better - shrinking a partition from the back end is much easier than moving all that critical info from the front.

---

### Post by trishacupra on 2007-03-31
Thanks SilverZero. I'm starting to get my head around this now. Thanks for sharing what you've learned from your experiences. I'll google Ultimate Boot CD.

---

### Post by sailor2001 on 2007-03-31
dual booting should be an easy thing to do if you follow the instructions....1. defrag...2.download a mepis disk (you can repair your drive(  ie grub boot) in case something goes wrong. Let the ubuntu disk do it's thing. It will partition the FREE space and not bother your windows at all. By the way, usually on the new boxes, where you have to burn your own recovery disk, the mfg usually allows you to make only one burn.

---

### Post by trishacupra on 2007-04-02
Thanks sailor2001. You're right - I wasn't able to do another burn of the recovery discs. Bummer. But that's just typical...

It's good to know it will be easy enough if I just follow the instructions. I googled 'mepis'. Is the mepis you mentioned the one at [www.mepis.org?](www.mepis.org?)

Thanks!

---

