---
title: "partitioning for dual boot"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by faintscrawl on 2008-02-01
I'm running 7.10 from a live cd I burned after download and everything seems to be running great (and looking sweet) so I'm hooked and I'm going to install.  I want to keep xp around for a while at least.  I've been reading a lot of installation guides, help threads, etc, but haven't quite come across the options the installer is giving me.  I've attached a screen shot (please ignore the screen shot window--newbie error).  What do I do? Guided? I definitely don't want to lose windows.

Thanks in advance.

---

### Post by taurus on 2008-02-01
Maybe these help!

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

p.s.  Next time if you want to take a screenshot, increase the time to 1 second so you would have time to minimize that screenshot window so that it won't be in the way.

---

### Post by motion parallax on 2008-02-01
Manual, then the next step will let you choose how to partition it. But that's the way I set up my dual boot.  I never tried the guided.  

You can just hit forward and see what the next steps are.  Ubuntu won't actually install until you've completed all the steps and told it to begin.

---

### Post by faintscrawl on 2008-02-01
I found those links through google. That's the thing: the options are different in those screen shots.  Thanks for quick reply.

So I have to do manual?  Yikes, I'm way out of my league here.

---

### Post by Superkoop on 2008-02-01
The way I did my partitioning yesterday, was I used the partition editior (System>Administration>Partition editor).
All you need to do is shrink a volume so you have enough room for ubuntu, 10G or larger probably. 
And then when you go back to the screen you took a screenshot of, it will give you another option to use the guided install, it will say something like "use largest undedicated space", something like that.

---

### Post by faintscrawl on 2008-02-01
> **Superkoop said:**
> The way I did my partitioning yesterday, was I used the partition editior (System>Administration>Partition editor).
All you need to do is shrink a volume so you have enough room for ubuntu, 10G or larger probably. 
And then when you go back to the screen you took a screenshot of, it will give you another option to use the guided install, it will say something like "use largest undedicated space", something like that.

Oosh.  I wish you'd come along 10 minutes sooner.  After looking everywhere until my eyes went bloodshot I just went ahead with the guided, and well, I have good news and bad news.  Ubuntu works great.  But I have no dual boot and for all I know no more windows. Talk about taking the plunge.  If anyone thinks I probably do have windows somewhere, please tell me where I might find it and run it.

By the way, I just looked in system>admin and unless I'm blind I have no partition editor.

---

### Post by taurus on 2008-02-01
Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
And if you want to use gparted again, you need to install it.

```
sudo apt-get update
sudo apt-get install gparted
```
And just so you know, you cannot resize Ubuntu while you are using it.  You must do it from a LiveCD.

---

### Post by stalkingwolf on 2008-02-02
what option did you select under the Guided section?

---

### Post by faintscrawl on 2008-02-02
> **taurus said:**
> Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
And if you want to use gparted again, you need to install it.

```
sudo apt-get update
sudo apt-get install gparted
```
And just so you know, you cannot resize Ubuntu while you are using it.  You must do it from a LiveCD.

Thanks for not giving up on me.

I tried the command you suggested but it says "invalid".  See screen shot.  You'll see I actually tried twice.

---

### Post by faintscrawl on 2008-02-02
> **stalkingwolf said:**
> what option did you select under the Guided section?

Let's see.  I have to remember.  That was 10 hours ago.  But I'm pretty sure there were no options under guided, which was why I posted to begin with, because screenshots I found from a google search suggested I would have options.

---

### Post by taurus on 2008-02-02
The command is

```
sudo fdisk -l
```
It is an upper case letter L and no space in between.  Otherwise, just highlight the command with the left button of the mouse and paste it to a terminal on your machine with the middle button, wheel.

---

### Post by faintscrawl on 2008-02-02
ah..thanks, taurus. ok that works better.

screen shot attached.  what's the prognosis, doc?

---

### Post by mysticrider92 on 2008-02-02
That screenshot means: /dev/sda1 is formatted ext3 with Ubuntu installed on it, /dev/sda2 is extended (it is a logical partition, not physical), and /dev/sda5 is a swap partition (acts as extra RAM to speed up the computer). This means that Windows was deleted, as there is no NTFS or FAT32 partition on your hard drive.

---

### Post by faintscrawl on 2008-02-02
Oh, GREAT!  

Maybe there should be some sort of warning during the installation process for average joe's like me--or maybe we should just still well away from Linux.

I guess I'm a full-time ubuntu user now (thank God it's working well).  Do you think that partition set up is good?

Thanks for the bad news :)

---

### Post by mysticrider92 on 2008-02-02
The partition setup is fine.

Installing Linux is not an easy task if you have never done it before. There is a small warning on the summary page before the install starts, but it is easy to miss, and the partition step is often challenging.

You should enjoy Ubuntu, and if you need help, just ask.

---

### Post by Snyfuss on 2008-02-02
I'm real new to Ubuntu and, for that matter, Linux, as well.  I have just gotten myself to the point where I can dual-boot Ubuntu and XP and, here's the really cool part, read and write data between the two.  I did it by consulting a combination of the following:

[INDENT]Linux 2007 Edition Bible.  It's a book that comes with CDs for doing things like partitioning your Windows harddrive and installing Linux.   Other, online methods for doing this (such as burning an ISO file to a DVD) didn't work for my HP Pavillion zv5227wm laptop (for whatever reason, the DVD wiith the ISO file wouldn't boot).  [/INDENT]

[INDENT]Linux Learning Curve.  A series of podcasts, which I found on iTunes (located at http:feeds.feedburner.com/LinuxLearningCuve).[/INDENT]

[INDENT]Ext2 Installable File System for Windows.  A piece of freeware located at [http://fs-driver.org/](http://fs-driver.org/) which allowed Windows to read - and write - to a Linux Ext2 partition.[/INDENT]

In short, I used the CDs which came with the Linux Bible to partition my Windows XP laptop and, then, install Ubuntu.  Since I'm trying to transition between XP and Linux (by using programs such as Open Office), one of my first problems was "how to share data."  After several failed attempts such as formatting the partition which I wanted to share as NTFS (Ubuntu couldn't get past the permissions issue) and FAT32 (again, permissions was the issue), I found the "Ext2 Installable" freeware.  So, I formatted my "shared data" partition using Qparted (which is accessible by booting the "Ubuntu" section of the Linux Bible CD) as Ext2.  Then, on the Windows side, I installed "Ext2 Installable." 

Since I created the Ext2 partition _after_ installing Linux, I had the problem of mounting it and setting the permissions so that Windows could write to it.  These problems I "solved" by mounting the partition to a directory I created called /mnt/share.  I then encountered the problem of Windows (and Unbuntu) not being able to read-write to this partition so I did a "chmod 777" command to make "share" accessible.

Then, my only problem was how to mount the partition on every boot.  I did this by using vi to edit the /etc/fstab file to include the following line:

/dev/hda4 /mnt/share ext2 defaults,errors-remount-ro 0 1

Please note that you must change "hda4" to be whatever the partition is called by your Linux setup (use fdisk -l to determine this).   You must also edit "/mnt/share" to be whatever directory you want to install your share partition to.

I realize that what I just wrote might be overwhelming for the novice and containing several errors and/or ambiguities and/or pieces of bad advice for the more seasoned user.  Nevertheless,  I post this information so that, like me, somebody who is trying to get into Linx, might be able to "piece together" the information I just wrote with something else s/he has read and come to a successful conclusion.

---

### Post by Sidewinder1 on 2008-02-02
The command is sudo fdisk -l  where the last character is a lower case L

---

### Post by dgbearcat on 2008-02-02
Hey, sorry I missed your post because this is EXACTLY what I asked about and figured out a few days ago. 

Here's what I did, in case you want to format and reinstall both for a dual boot:

Assume you've got a fresh windows install. We'll say you have a 100gb hdd.

So you'll get windows up and running and get all your drivers set up, etc. Then boot from the live CD. Go under system->admin->partition tool. It's called "gparted". You'll see your bit NTFS section where windows lives, and then probably one or maybe two others that are backup/restore partitions. Use the arrow to "scale down" your ntfs partition to whatever you like. I've got a lot of crap saved in windows, and don't expect to install too much into linux, so I made it like 60gig/25gig, with the leftovers being the other two partitions I had. The 25 gig area was not "unused space". This took about 5 minutes or more, so just wait for it and be patient.

I then booted again from the livecd, and saw a new option of "use largest segment of free space" or something like that. I selected that and completed the install. 

Worked like a charm! Only problem I've encountered at all is that Ubuntu won't standby, but that's apparently a known issue. Somehow it's messed up my windows standby so that it doesn't always work, but since ubuntu takes about as long to just shut down and load up as windows does to standby, I don't really mind much. 

Here's the thread where I got it worked out with some screenshots that might help:
[http://ubuntuforums.org/showthread.php?t=684207](http://ubuntuforums.org/showthread.php?t=684207)

---

### Post by faintscrawl on 2008-02-02
Thanks.

I should have been more patient and waited for more advice before proceeding.  Now that I've lost windows xp (according to poster above who looked at my screen shot after doing the sudo f-disk l), I'm not able to do a dual boot--at least until I get my hands on a copy of xp.    Fortunately, I had backed up all my docs, music ,etc and am happy to see open office deals well with my word and excel docs.  In all it feels like a big spring cleaning on my computer--an unexpected one--but maybe not so bad.  Who knows, maybe I'll never run windows again.

---

