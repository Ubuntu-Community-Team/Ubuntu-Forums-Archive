---
title: "Partitioning/Installing Ubuntu 6.06.1 (External Drive)"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by williamsr6 on 2007-07-30
Hello all,

I'm very new to everything Linux, but I'm extremely interested. I have some computer knowledge, but a lot of the talk on the forums seems totally foreign to me, so forgive me if my questions have already been asked...I searched and couldn't find the answers I needed.

Anyway, I burned a Live CD of Ubuntu 6.06.1 and am extremely impressed. I want to install it, but I don't have the space or the certainty I'll want it enough in the future to partition my laptop's hard drive. What I'm wanting to do is create a partition on my external USB hard drive, install Ubuntu there, and boot from the drive. This is where things get sticky for me.

I have no clue where to start. I don't know how to partition, what to do afterwards, etc. If anybody has the patience to type out some instructions or link me to some other sites for help in doing this, I'd be extremely grateful. Thank you so much in advance!

-Ryan

---

### Post by sourjax on 2007-07-30
Here's what I did with Ubuntu Feisty 7.04, I hope this helps but I'm still a beginner myself...

I burned the Desktop .iso and booted into the LiveCD and when the installer asked where to install it I choose my external HD (80GB Seagate), and it installed perfectly I now have Windows Vista on the internal HD and Ubuntu on my external HD and I boot into Ubuntu 90% of the time, but I still have a need for Windows.

One note: I'm not sure how to install it without messing with your MBR, if I decided to uninstall Ubuntu completely, I'm uncertain of what it would do to my booting capability. Of course I have no reason what so ever to uninstall Ubuntu so no biggie for me, (that is until I decide to buy a second internal HD and put Ubuntu their in order to get my external HD back.)

---

### Post by williamsr6 on 2007-07-30
Thanks for your response. Something I neglected to mention was that on my external, I do already have a backup of my internal HD, so I'm thinking I'll probably need to partition...

I'll try just clicking "install" from the Live CD though, as you suggested. Anybody have any info on how to partition? TIA

---

### Post by sourjax on 2007-07-30
I know that with Feisty, there is a built in partitioning function in the installer, but I don't know how well it plays with windows partitions.

---

### Post by ev5unleash1 on 2007-07-30
Ok, you may run in to trouble going about booting to Windows when you want to install Ubuntu on the external.

What you want to do first before deleting the Partition because when you do you are done you need to reinstall Windows. If your ready to uninstall Ubuntu from the Duel boot you first boot to windows.
Go to Start > Run > and type CMD then ok > then type in 

```
FDISK /MBR
```

By doing so I heard should make it Boot to Windows and the Duel boot screen won't show up on boot. Then you want to boot to the live CD and then delete the ext3 and if you have the SWAP partition then you are Ubuntu Free. An easy way to uninstall ubuntu off that internal Hard Drive :)

---

### Post by williamsr6 on 2007-07-30
Okay, I think I've actually got everything worked out now for the most part. v6.06.1 does have a partitioner built into the installer, but it won't recognize my external drive. It only gives me the option to partition my internal drive. Anybody know the solution to this?

Sorry for being so much trouble, thanks to anyone and everyone who replies.

---

### Post by ev5unleash1 on 2007-07-30
Yea when you open the partitioner make sure the USB dirve is located and mounted before opening then click file or one of those options it will let you choose which drive you want to partition :)

---

### Post by williamsr6 on 2007-07-31
Okay, well, I thought I had everything set up and ready to go, but I've run into another problem. :(

I completed wiped my 80gb external drive and installed Ubuntu on it using the Live CD. After I did this, I took the appx. 79gb Linux parition and resized it to 39.06gb, leaving 32.60gb unallocated so I could later format this part in Windows XP and use it to store my system backup. Well, once I shut down my system, removed the Live CD and booted from my USB Drive, Ubuntu attempted to load for about 5 minutes before showing the following message:


> 
     Booting 'Ubuntu, Kernel 2.6.15-26-386'
root   (hd 0,0)
     Filesystem type is ext2fs, partition type 0x83
kernel   /boot/vmlinuz-2.6.15-26-386 root:/dev/sdc1 ro quiet splash
     [Linux-bz Image, setup=0x1c00, size=0x15787d]
initrd   /boot/initrd.img-2.6.15-26-386
     [Linux-initrd @ 0x1f941000, 0x6ae36b bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
[17179572.116000] PCI:Failed to allocate I/O resource #7:1000@10000 for 0000:00:1e:0
ALERT! /dev/sdc1 does not exist. Dropping to a shell!

BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh: can't acces tty; job control turned off
#



I've tried booting it up from the USB Drive twice and gotten the same issue. Any ideas? I'm dying here!

---

### Post by sourjax on 2007-08-01
> **williamsr6 said:**
> I completed wiped my 80gb external drive and installed Ubuntu on it using the Live CD. After I did this, I took the appx. 79gb Linux parition and resized it to 39.06gb, leaving 32.60gb unallocated so I could later format this part in Windows XP and use it to store my system backup. Well, once I shut down my system, removed the Live CD and booted from my USB Drive, Ubuntu attempted to load for about 5 minutes before showing the following message:





I've tried booting it up from the USB Drive twice and gotten the same issue. Any ideas? I'm dying here!


Why did you resize it? I'd reinstall Ubuntu with out resizing it. Try to boot and if it doesn't work let us know.

---

### Post by williamsr6 on 2007-08-01
Okay, I finally got everything right! I'm not exactly sure what I did wrong, but even when I used Gparted I couldn't wipe my external drive and Windows refused to even acknowledge it. I downloaded Partition Magic, wiped the drive clean, split it into 2 partitions, formatted one to NTFS and successfully installed Ubuntu on the other. I'm running off my hard drive right now, so thanks to both of you for your help! :)

---

