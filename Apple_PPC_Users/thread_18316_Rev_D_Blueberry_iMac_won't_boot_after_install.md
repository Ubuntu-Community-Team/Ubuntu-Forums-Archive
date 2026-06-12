---
title: "Rev D Blueberry iMac won't boot after install"
date: 2005-03-05
forum: Apple PPC Users
---

### Post by ubuntu77 on 2005-03-05
I am another Linux newbie, trying to install Ubuntu Linux 4.10 (Warty) on a Rev. D blueberry iMac 333. I get the same problem as Toad did... hangs forever at "Please wait, loading kernel...". During the install, I let the partitioning program use the "guided partitioning" option with all the default values. It produces the following on my upgraded internal IBM Deskstar 60GB HD:

IDE1 master (hda) - 61.4 GB
#1 32.2 KB Apple
#2 1.0 MB boot untitled
#3 60.9 GB ext3 untitled
#4 512.8 MB swap swap (I upgraded the RAM to 256MB)

#2 and #4 have the white on black smiley face icons next to type, and #2 also has the crooked downward arrow next to its smiley face.

Toad said he figured out his problem by making his root partition 7 GB and his home partition about 70 GB. So in order to get my iMac to work, does that mean I need to make my boot partition > 1 GB vice the 1 MB it is now, or do I need to split up the ext3 partition into 2 partitions, say a 6 GB (for root) and a 54 GB (for home)?  In other words, what modifications do I need to make to the partitions listed above (more partitions, different sizes, etc.) so that my iMac will boot properly like Toad's?

Please help!

 :-(

---

### Post by DJ_Max on 2005-03-06
Having a 7GB Root parition, then 70GB /home is, well crazy. You will need to switch it around, as all your core program files, will go into your / parition. Do you have OS X installed.

---

### Post by ubuntu77 on 2005-03-06
Hi, DJ_Max.

Thanks for replying to my post.  I have since managed to get past this initial problem by manually partitioning my HD as follows:

    /                     2GB     ReiserFS
    /boot           128MB    ReiserFS
    /tmp                2GB    ReiserFS
    /var                 4GB    ReiserFS
    /usr                 4GB    ReiserFS
    /usr/local         4GB    ReiserFS
    /home           40GB    ReiserFS

So, I now have a functioning ubuntu system!  Cool!  Now, I have a coulple of new problems.  I tried to install the ATI fglrx-driver by using the command "sudo apt-get install fglrx-driver" and I get an error message that says that it can't find the above package.  I then added "universal" to my repository list, and ran the command again:  same result.  Since you have an iMac also that has an ATIRage Chipset, does ATI make a video driver for PPC Linux in a .deb package?  Or are you resigned to video without 3D OpenGL acceleration?

On another front, my internal speakers don't work, but if I plug in external speakers into my sound out port on the side, the external speakers work fine.  This isn't as big a deal since the externals work, but I am curious:  do you have the same problem on your iMac?  If so, were you able to fix it?

One more question:  what filesystem do you use on your iMac?  As you can see from above, I chose ReiserFS, but I was debating back and forth between ext3 and ReiserFS.  I was having trouble finding online a guide that talks about the different filesystems and their relative strengths/weaknesses.  Do you know of such a guide, and considering my iMac, was ReiserFS a good choice or would ext3 have been better?

Sorry to be so long winded, but I would greatly appreciate your feedback as a fellow iMac owner on the issues I have.

Thanks!

PS:  My iMac specs:
iMac Rev D Blueberry
G3 333Mhz, 256MB RAM, internal IBM Deskstar 60GB HD
Tray loading 24x CD-ROM
ATI Rage Video
Ubuntu 4.10 (Warty Warhog) only (no dual boot with Mac OS 9 or X)

 :smile:

---

### Post by DJ_Max on 2005-03-06
ATI doesn't release their source code for the drivers. They only release x86 Linux/Windows binaries, and MAC OS PPC binaries. With that said, there is no ATI drivers for the LinuxPPC.

I use ext3, but heard ReiserFS is better. As for some info, try [http://www.tldp.org/HOWTO/Filesystems-HOWTO.html](http://www.tldp.org/HOWTO/Filesystems-HOWTO.html)

For the speaker problem, play around with your audio/sound settings, its a lot you can control.

---

### Post by ubuntu77 on 2005-03-06
Thanks for the feedback, DJ_Max.  I'll check out that filesystems howto and experiment some more with my audio settings.  Too bad ATI doesn't make LinuxPPC drivers for their video chipsets.  :(

What windows manager do you primarily use?  Since you have 256MB RAM like me, do you stick with the default GNOME or user a lighterweight xfdce or iceWM?  I'm using GNOME right now, and I was wondering if you found 256MB RAM adequate to run that environment.

Again, thanks for your feedback.

---

### Post by DJ_Max on 2005-03-06
Yeah, ATI is just currently getting there overall Linux support better, so LinuxPPC support is long ways.

I use Gnome, and it runs great.

---

### Post by Hercynium on 2005-06-20
I have a *very* similar hardware setup. It's a 333Mhz Grape iMac (Rev. C, I think). I've maxed out the RAM at 384MB and put in a 20GB Drive. (I could go with larger)


I've been having the same "loading kernel..." issue trying to install Ubuntu Hoary onto my HDD. However, I already have OS X on this drive taking up 6GB. I've tried several different partitioning schemes, and no matter what I've tried, OSX boots fine (even w/ yaboot) but no love from Linux.


The only thing I haven't tried is putting Linux first on the drive and MacOS second. However, I'm not so sure that will work, and my patience is wearing out. ](*,) 

Has anybody else gotten this model of iMac to dual-boot on an upgraded HDD? If so, what's the simplest partitioning scheme that will work?

---

### Post by Hercynium on 2005-06-21
Eureka! I found a solution!

As long as the linux /boot partition is below the 8GB limit, linux boots just fine.
Better yet, I'm dual-booting w/ OS X as well!


I'll come back and post my exact partition table, but the general setup is as follows:

Below 8GB:
  1. Apple Partition Map (64K)
  2. NewWorld Boot Partition (~800K)
  3. Ext2 Linux /boot partition (32M)
  4. HFS+ OS X Partition (7GB)
Above 8GB:
  5. Ext3 Linux / partition (4GB)
  6. Linux Swap partition (1GB)
  7. Ext3 /home partition (rest of space.. 8GB)

This setup did require some install-cd acrobatics, but I'm guessing it could be done in a more streamlined way:

1. I started by using mac-fdisk from the Ubuntu Install CD to create the first two partitions.
2. Then I installed OS X into it's partition. OS X created some other partitions (maybe for drivers and kernel patches?) and left about 123MB of free space before it's partition.
3. In that free space OS X left near the beginning of the disk, I used the Ubuntu Installer's Partitioning tool to create the /boot partition.
4. I then proceeded to create the rest of the linux partitions after the OS X partition.
5. Linux finished installing, and I was in dual-boot heaven!

---

