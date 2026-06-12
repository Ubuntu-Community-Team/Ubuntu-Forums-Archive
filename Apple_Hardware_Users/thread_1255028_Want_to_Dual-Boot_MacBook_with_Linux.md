---
title: "Want to Dual-Boot MacBook with Linux"
date: 2009-09-01
forum: Apple Hardware Users
---

### Post by holdencaulfield on 2009-09-01
Hello I have an Unibody MacBook, 2.4GHz processor, 2GB RAM. I really love Mac OS, and I have no problems with it whatsoever. However I would like to boot a Linux OS alongside Mac OS 10.6. 

Is it difficult to do? It seems like you have to mess with the settings for the system to boot. But can't you just boot into it with BootCamp? 

Anyways, I don't know which distribution to install. I've thought about Gentoo, because I'm not trying to install Linux for any actual purpose other than to learn. That's really what I want to do, Mac OS serves all me actual needs. Anyways since this computer is my main computer, I may not be able to have all that time, nor the experience to install it. Although it does have comprehensive documentation. 

So I was thinking:

Gentoo
Sabayon
Ubuntu

But what else might be a good one for me to try? I really want something that I can learn with, even if it takes some time. What's mostly important is that my Mac OS does not get messed up, and that I can restore the HDD to it's full size if I get sick of the other partition. 

Thanks!

---

### Post by anujpathania on 2009-09-01
I don't have much experience with installing Linux on MAC personally, but my friend did messed his macbook up doing so. 

Its definitely difficult than on Windows, we need to write a Wubi like code for MAC I guess.

Also, take backup before toying. Good luck.

---

### Post by blueshogun on 2009-09-01
I'm interested in this as well.  I have a similar MacBook.  Currently, I'm using the bootcamp partition with Windoze, but I haven't booted to it twice since I installed it.  

I can do everything I need to do in OS X, but I'd like my bootcamp os to be one I'll actually use if I'm going to spare the disk space.  I have Ubuntu on my home pc, and I know I'd use it more on my Mac if only for the eye-candy.

So I figured I'd try it myself; all my important stuff is backed up.  Using every live cd in my collection (suse, fedora, ubuntu, dsl-n, freeBSD, ...), I could boot to a nice clean desktop that worked.  Almost all hardware was supported including the iSight, but no wireless!  I won't bother to try to install it to bootcamp if I can't get all the hardware to work.  Maybe there's a driver out there somewhere?  I didn't spend enough time looking.  The OS X disk comes with drivers for windows, but I'm not sure I want to try emulating anything.  

> **holdencaulfield said:**
>  But what else might be a good one for me to try? I really want something that I can learn with, even if it takes some time.

Ubuntu seems to be the reigning champ among new users.  I'll give it my vote; I've seen two converts first hand, the kind of people you wouldn't expect would ever try anything other than the norm.  Pick the one you feel most comfortable with, and if you stick with it you'll be fine.  And then if you switch distros later you'll find them all similar enough that you won't really have to learn anything except where that one option got moved to...

> **holdencaulfield said:**
> Is it difficult to do? It seems like you have to mess with the settings for the system to boot. But can't you just boot into it with BootCamp?

Theoretically it shouldn't be *that* difficult.  Press and hold <option> at boot.  When I did this with the live cd in the drive, it listed My HD, Windows (the bootcamp partition), and Windows (the * live cd).  I'm under the impression the Mac only recognizes its own filesystem and fat(32).  I'm not sure if this requires us to put at least /boot in a fat partition.  Or how "custom" we can make the bootcamp partition for that matter.

 > **holdencaulfield said:**
> What's mostly important is that my Mac OS does not get messed up, and that I can restore the HDD to it's full size if I get sick of the other partition. 

I know you can erase the bootcamp partition at the click of a button with the bootcamp utility in OS X.  It's really impressive to wipe it clean and suddenly have your 120GB back.  As for messing it up...  Backup, and don't install on os x's partition! lol.  I'm sure *someone's* done it, so there's hope for us.

Hope some of that helps.

---

### Post by holdencaulfield on 2009-09-01
> **blueshogun said:**
> 
I can do everything I need to do in OS X, but I'd like my bootcamp os to be one I'll actually use if I'm going to spare the disk space. 

Right, I'm a big Apple fan, I love everything Apple, I just like to learn new things and to become more proficient with computers.
> **blueshogun said:**
> 
Ubuntu seems to be the reigning champ among new users.  I'll give it my vote; I've seen two converts first hand, the kind of people you wouldn't expect would ever try anything other than the norm.  Pick the one you feel most comfortable with, and if you stick with it you'll be fine.  And then if you switch distros later you'll find them all similar enough that you won't really have to learn anything except where that one option got moved to...

I've used Ubuntu before on my old Dell laptop, and it was great, really intuitive desktop environment with GNOME, and everything worked well, except of course the internet, so I gave up eventually. 

I've also used openSUSE, which I didn't like that much, but it was okay. Numerous people have tried to install Gentoo, which I've heard can work quite well, but I'm not sure sure I could figure out the installation, although my friend (who works for geeksquad) told me that if I just follow the manual, it should work fine. I thought about Sabayon, but apparently it has a terrible package management system, which seems strange, because apparently that's Gentoo's highlight.
> **blueshogun said:**
> 
Theoretically it shouldn't be *that* difficult.  Press and hold <option> at boot.  When I did this with the live cd in the drive, it listed My HD, Windows (the bootcamp partition), and Windows (the * live cd).  I'm under the impression the Mac only recognizes its own filesystem and fat(32).  I'm not sure if this requires us to put at least /boot in a fat partition.  Or how "custom" we can make the bootcamp partition for that matter.

Right, many people have talked about installing this rEFIt thing, but I don't really know why you would have to do that, because it seems like you could just use boot camp, make a partition, erase that partition and install. But I will probably follow what others have done in the past, if only to prevent headaches for me.

---

### Post by gotenks05 on 2009-09-01
I've done a dual boot plenty of times.  Insert the 10.6 installation media and resize the drive and make a new partition using disk utility on the media, not on the actual OS.  reboot and have the linux installer install on continous free space, whether you enter live mode to install directly.  It works best if you don't have any drives connected besides your internal hard drive.

---

### Post by holdencaulfield on 2009-09-01
Oh okay, well perhaps I will try that. Should I have much trouble configuring the hardware other than the wireless network card of course?

---

### Post by gotenks05 on 2009-09-01
> **holdencaulfield said:**
> Oh okay, well perhaps I will try that. Should I have much trouble configuring the hardware other than the wireless network card of course?

Just make sure you partition the new partition as Free Space or you'll need to use Gparted to reformat the new partition.  No, not really but your iSight and Apple remote won't work out of the box Lirc, and isight-firmware-tools should help through that, you can find the instructions to get those working on this forum.  Your wireless card won't be much of a hassle, just go to System/Administration/"Hardware Drivers", since I'm pretty sure macs use broadcom cards and that worked for me, but I could be wrong on that.

This works best with Ubuntu and Ubuntu-variants.

---

### Post by holdencaulfield on 2009-09-01
What about overheating, I heard that Linux tends to overheat on Apples?

---

### Post by schauerlich on 2009-09-01
> **holdencaulfield said:**
> What about overheating, I heard that Linux tends to overheat on Apples?

No, it's fine.

There's an entire section of the wiki devoted to setting up Ubuntu on Apple hardware. It's split up by what type of computer and what generation you have. I'm guessing you have a MacBook5,1, but you can check by going Apple Menu>About This Mac>More Info and looking for "Model Identifier". Here's the wiki page for a MacBook5,1:

[https://help.ubuntu.com/community/MacBook5-1/Jaunty](https://help.ubuntu.com/community/MacBook5-1/Jaunty)

If you have something different, you can find the appropriate link on this page:

[https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages](https://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages)

---

### Post by holdencaulfield on 2009-09-02
Okay, I think that I will go ahead and give this a try, about how much memory should I allocate for the Ubuntu partition? I have a 250GB HDD, with about 210GB left.

---

### Post by gotenks05 on 2009-09-02
> **holdencaulfield said:**
> Okay, I think that I will go ahead and give this a try, about how much memory should I allocate for the Ubuntu partition? I have a 250GB HDD, with about 210GB left.

Depends how often you'll use it.  30 GB is enough, if you will not use it often.

---

### Post by cfrivas on 2009-09-02
I done it with my PowerBook G4 and all is okay. Was able to repartition my HD by booting from "iPartition" disk and drag open a new partition, about 10gigs for starters, I only had a 60gig HD, and left the remaining as Leopard. Then I rebooted with my Leopard CD and ran Disk Utility to verify and repair my newly partitioned HD with OSX only. Then restart to make sure you still have osx bootable. If okay, then restart and and hold down Command C to boot from Ubuntu Live CD and Install onto free space. :popcorn:

---

### Post by ramenlover on 2009-09-03
Hiya. I installed Ubuntu on my Macbook 5,1 today, been playing around on it mostly for learning. I gave it 15Gb as a partition separate from my OS X volume.

Managed to get some things going, like compiz cube and installing some programs and it's good that some things work straight out of the box, like wireless and the webcam. I've not used linux at all before, it should be noted. Still no sound however, or right click / 2 finger scrolling. None of the code on this page 
[https://help.ubuntu.com/community/MacBook5-1/Jaunty ]("https://help.ubuntu.com/community/MacBook5-1/Jaunty")
or similar seems to do the trick to fix this

Will try again tomorrow

---

### Post by Brightbelt on 2009-09-05
I had Ubuntu 9.04 Jaunty installed on my MacBook5.1 (dual boot with rEFIt using Disk Utility) but I took it off after ongoing troubles. 

This may help you, but I'm not sure if it specifically covers MacBook5.2 ---> [https://help.ubuntu.com/community/MacBook%20Aluminum](https://help.ubuntu.com/community/MacBook%20Aluminum)

I could never fix my reboot problem and I got my sound problem fixed for a while, but then it just stopped working again.

Also, I was finding on my Mac HD in OS X in Disk Utility that I needed to Repair Permissions every time I came out of Linux and back to the MacBook HD partition. And repairing permissions always showed ***Massive amounts*** of corrections needed to complete it. 

So I wondered if Linux was maybe doing something not so healthy  to my hard drive - who can say but it made me nervous enough to pull the plug on Ubuntu. 

So far I'm pretty hesitant and cautious about the 9.04 release. Maybe there are updates on the way to save the day and I respect all the hard work that's been done, but Macs are kind of second or third in line anyways so it's not surprising. 

Frank B.

Good Luck, Frank B.

---

