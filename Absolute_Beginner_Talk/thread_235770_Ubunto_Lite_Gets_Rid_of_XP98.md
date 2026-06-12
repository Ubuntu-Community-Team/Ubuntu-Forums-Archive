---
title: "Ubunto Lite Gets Rid of XP/98?"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by samureye on 2006-08-13
I got Ubuntu lite and I put it to install thinking that it could make a third option on my PC for Windows 98/XP. Well, it didn't. I *think* I made a partition with Partition Magic, I chose the Linux option but I obviously don't knwo what I did.

So I put ubuntu Lite to install and it did something and ended up rebooting right back into the Live CD with nothing seemingly changed, so I took out the CD and restarted the PC and it is stuck when it says loading IDE OK. So I think I lost my Windows XP/98 Partitions though it didn't seemingly delete  anything.

I am currently downloading the latest Ubuntu install, not the Lite, the proper thing. I take it the install would wipe everything clean or enable me to find out if my files are still there? If anything I can count my losses, it was an old PC and all I want from there is some music.

---

### Post by steve.horsley on 2006-08-13
You should not try and make a partition for Ubuntu. Delete that partition again and leave the disk space unallocated. The Ubuntu installer will offer to use the free space and when you say yes, it will create the partitions that it needs for itself. It will also format them properly, something that Partition Magic seems not to be able to do reliably.

---

### Post by PriceChild on 2006-08-13
If its hanging on IDE ok... then there's a problem with the bios booting the box me thinks...

no chance you've a dual bios like me and could swap to the backup to see if that solves it?

---

### Post by az on 2006-08-13
> **samureye said:**
> I got Ubuntu lite and I put it to install thinking that it could make a third option on my PC for Windows 98/XP. Well, it didn't. I *think* I made a partition with Partition Magic, I chose the Linux option but I obviously don't knwo what I did.

Where did you get the cd?  There is no ubuntu lite installer yet...

---

### Post by sean_ on 2006-08-13
> **steve.horsley said:**
> You should not try and make a partition for Ubuntu. Delete that partition again and leave the disk space unallocated. The Ubuntu installer will offer to use the free space and when you say yes, it will create the partitions that it needs for itself. It will also format them properly, something that Partition Magic seems not to be able to do reliably. Are you trying to overwrite his Windows? I did everything in Partition Magic except make my SWAP and EXT3 partitions in Linux. Suppose you have 200gb, resize it to 100,000KB(Should be 100gb), then make a linux partition for SWAP, make that 512mb then make a partition with EXT3, set the mountpoint to / and make the size like, 90,000KB.

---

### Post by samureye on 2006-08-13
> no chance you've a dual bios like me and could swap to the backup to see if that solves it?

No idea.

I haven't the slightest clue as to where I got it from, really. I downloaded it some time ago and now 2 days ago I decided it was time to install Linux and learn it, I've tinkered with SLAX and some other Live CD in the past.

As I said before, I have Ubuntu downloading right now (dial-up). My bios is set to read CDs, floppies then hard drives thanks to my BIOS tinkering some time ago. If I just put in the Ubuntu CD that I am downloading now, will it wipe everything and install as the only OS, deleting any partitions, OS installs etc?

---

### Post by sean_ on 2006-08-13
> **samureye said:**
> No idea.

I haven't the slightest clue as to where I got it from, really. I downloaded it some time ago and now 2 days ago I decided it was time to install Linux and learn it, I've tinkered with SLAX and some other Live CD in the past.

As I said before, I have Ubuntu downloading right now (dial-up). My bios is set to read CDs, floppies then hard drives thanks to my BIOS tinkering some time ago. If I just put in the Ubuntu CD that I am downloading now, will it wipe everything and install as the only OS, deleting any partitions, OS installs etc? The Live CD is just the installer, no it won't over write windows. If you read what I said, you will install Ubuntu easily.

---

### Post by samureye on 2006-08-13
Okay, someone was telling me to get a Windows bootdisk and use fdisk which will be able to show me if I have lost everything, which they doubt I have. Instead of going through this trouble, will downloading [this]("http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-i386.iso") and put it in the system wipe everything and just install Ubuntu, so as to say it is the only OS on the computer and there are no partitions? Like I bought a brand new PC with it installed then. Sorry if I'm being difficult.

---

### Post by sean_ on 2006-08-13
Okay, I'm done helping you, you're completely ignoring me.

---

### Post by seshomaru samma on 2006-08-13
> **samureye said:**
> Okay, someone was telling me to get a Windows bootdisk and use fdisk which will be able to show me if I have lost everything, which they doubt I have. Instead of going through this trouble, will downloading [this]("http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-desktop-i386.iso") and put it in the system wipe everything and just install Ubuntu, so as to say it is the only OS on the computer and there are no partitions? Like I bought a brand new PC with it installed then. Sorry if I'm being difficult.

I think Sean has answered your question.
The installer is flexible - it CAN erase all your partitions , if YOU want it to, leaving Ubuntu as the only OS.
or it CAN also leave your windows partitions intact , if YOU want it to, making a Windows/ubuntu dual boot.
When the live CD boots up , it will have an install option , if you click the install option , you will be asked several questions. One of the questions will be how you want to part your disc. You will then be able to choose whether to keep win98/xp or not. 
Hope that helps....

---

### Post by samureye on 2006-08-13
Sean_ and seshomaru samma, thank you. When it gets done downloading I'm going to check it out. And no, I wasn't ignoring you man, just wasn't too clear on my end. Thanks.

---

### Post by Frank Golden on 2006-08-13
> **samureye said:**
> Sean_ and seshomaru samma, thank you. When it gets done downloading I'm going to check it out. And no, I wasn't ignoring you man, just wasn't too clear on my end. Thanks.
Steve.horsley is right. Using the desktop CD you are downloading,
when you burn and boot the CD it will by default install to memory. On the resulting desktop will be a icon to install.
Double clicking will result in Ubuntu installing on your machine interactively. It is best to have XP/98 already installed.
Also have a space on your HD unallocated (free). About 10GB works
for me. During the install process you will be asked where you want to install. If you have the unallocated space you will have
an option to install to the largest free space. Choosing this
will cause Ubuntu installer to properly format this free space
and install itself to it. Leaving your other stuff alone. It 
will end up on 10GB being about 9GB ext3 with the rest being swap. All this is almost automatic, you must tell it what to do at almost every step. If it screws up your your other stuff it is because you told it to. Near the end of install it will install GRandUnifiedBootloader or GRUB. When you reboot
a menu will appear, if you do nothing it will boot Ubuntu (default) in 10 seconds. Hitting any key will pause the menu
allow you to peruse it. Use arrow keys to scroll down. Your
MS stuff should be at bottom.
See these guides for a more thorough explanation.
The first one is for use with the Alternate install CD.
The second for the DesktopCD you are downloading.

[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)

[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by samureye on 2006-08-14
Thanks a whole lot, as soon as this finishes downloading in a while, i'm off to it!

---

### Post by steve.horsley on 2006-08-14
You actualy want it to erase windows and use the whole disk? Why didn't you say so? I seem to remember that the installer offers 3 choices:
* Erase and use the entire disk
* Use the free space (meaning un-partitioned space if there is any)
* Custom partitioning, where youcan largely do what you like

---

### Post by samureye on 2006-08-14
I was saying that I may HAVE to do that it seems I've lost my Windows partitions, both XP and 98. Take a look [here]("http://ubuntuforums.org/showthread.php?t=236386") though. Sigh.

---

