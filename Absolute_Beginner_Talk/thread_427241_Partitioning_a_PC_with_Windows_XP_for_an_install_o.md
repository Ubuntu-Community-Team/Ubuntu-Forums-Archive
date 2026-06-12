---
title: "Partitioning a PC with Windows XP for an install of Ubuntu Feisty Fawn"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by afriendcalledben on 2007-04-29
Hi,

I am a complete beginner and know very little but want to dip my toes in Ubuntu. I've had a few gos at installing Ubuntu 7.04 but I freeze up with nerves when it comes to the partitioning section of the install. I recently purchased a Dell PC with XP installed and would really like to install Ubuntu without affecting this installation (I have made backups as I know stuff can go wrong).

Every howto guide says it's dead easy as you simply select the 'Guided' option of resizing an existing partition to create a new one for Ubuntu. However I'm not given that option. I'm only given the option to 'use entire disk'.
[IMG]http://images.afriendcalledben.com/ubuntu/ubuntu_install.jpg[/IMG]

I had a look into manually setting the partition but I didn't understand the requirements. It told me the partition had to be on the root level ("/") but all the partitions set up started on "/dev"
[IMG]http://images.afriendcalledben.com/ubuntu/ubuntu_install2.jpg[/IMG]

I also looked into setting the partitions up in XP but became bewildered. This is how Dell have set up the partitions. I don't get what DELL_UTILITY is for.
[IMG]http://images.afriendcalledben.com/ubuntu/ubuntu_install3.jpg[/IMG]

If anyone reckons they could explain an easy way to set up partitions for this machine I would be massively grateful. Let me know if you require any additional info.

Sorry for the long-windedness. Just wanted to be thorough in explaining my problem.

Thanks in advance, 

ben

---

### Post by BaffledMollusc on 2007-04-29
Whee... that looks really odd. I blame Dell ;)

The Dell utility partition is, I presume, a hidden recovery partition in case something goes wrong. At least, that's what I would have thought; it seems a bit small for that. Maybe it contains tools for fixing your Windows installation if you hose it.

The thing that really weirds me out is that according to the Ubuntu partitioner, you have three SATA hard drives - sda, sdb, and sdf. And why it's sdf rather than sdc, I don't know. 

Can you tell me how many physical hard drives you have in your PC?

Edit: Wait, did you have something plugged into a USB port while you were running the Ubuntu partitioner?

---

### Post by afriendcalledben on 2007-04-29
Yeah Dell likes to make things hard for everyone.

I have two 160gb hard drives consilidated into one partition. If what I said isn't nonsense.

Dell states is thus:

320GB Serial ATA RAID 0 Stripe [2x160GB 7200rpm drives with DataBurst™ cache]

---

### Post by afriendcalledben on 2007-04-29
Sorry just saw your edit. I may have had a 2gb usb stick in, I think.

---

### Post by afriendcalledben on 2007-04-29
Sorry, just replying to say I removed all USB drives and devices, ran Ubuntu installer again and the partitioner only showed:

/dev/sda
/dev/sdb

If that helps.

---

### Post by BaffledMollusc on 2007-04-29
> **afriendcalledben said:**
> Yeah Dell likes to make things hard for everyone.

I have two 160gb hard drives consilidated into one partition. If what I said isn't nonsense.

Dell states is thus:

320GB Serial ATA RAID 0 Stripe [2x160GB 7200rpm drives with DataBurst™ cache]

Okay, that makes sense, and the USB stick explains the third drive.

Unfortunately I've never installed Ubuntu onto a system with RAID, and I'm afraid to suggest anything. I presume it would be possible, probably by creating two partitions on each of the disks, one with XP and one with Ubuntu, and using RAID to mirror the disks, but I have no idea how to go about it. Some quick googling turned up this link [http://www.computing.net/hardware/wwwboard/forum/45609.html](http://www.computing.net/hardware/wwwboard/forum/45609.html) which suggests getting rid of your RAID set up, and just put Windows on the first disk and Ubuntu on the second.

---

### Post by afriendcalledben on 2007-04-29
That sounds quite scary. I think I'll do a lot more research before I take that on.

Thanks for the help, BaffledMollusc.

Cheers,

ben:)

---

### Post by blueCoconut on 2007-06-21
Hi Ben,

I'm actually having a similar problem myself:  I'm trying to partition my newly purchased Dell Dimension 9200 which has double HDD with two 320Gbs and wanted to know if you've managed to find a solution for partitioning with sda, sdb... I'm an absolute beginner and looking for any advice.

Please let me know if you have any suggestions.

Thanks!

---

