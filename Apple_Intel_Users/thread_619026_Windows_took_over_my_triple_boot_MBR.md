---
title: "Windows took over my triple boot MBR"
date: 2007-11-21
forum: Apple Intel Users
---

### Post by omax on 2007-11-21
Hi guys.

Windows is really blowing my mind, something less useful has never existed. But I need it for work.

I triple boot MacOSX, Xubuntu and Windows XP.

Due to some error in Windows XP, as allways, I had to reformat that partition from linux


```
fdisk /dev/sda
d
4
n
p
4
t
c
w

mkfs.vfat /dev/sda4
```
You should understand that...
So I ran the Windows XP install CD. Installed it on that new partition (which according to Windows was unpartitioned. Congrats!)
All well, it installs and boots.

Though on reboot, Windows has taken over my MBR so now m rEFIt-menu does not show up. Neither does GRUB.

How can I solv this? I want rEFIt. Not Windows XP, nor GRUB. rEFIt.

Very thankful for any answer!
I appreciate it.

Omax

---

### Post by omax on 2007-11-21
WHAT THE ****!>?!!?

Why does it say in Windows in Disk Management That Disc 0 has 62,33 GB unallocated space and then C: 12,20GB ?!?!?!


Did Windows just delete my entire setup!? Everything I ever had on MacOSX and Linux, every setting I have ever made!? If this is true I'm ******* gonna kill myself! I CAN NOT AFFORD TO LOSE ALL THAT! I DID NOT HAVE ANY FUCKINGH BACKUPS.


I apologize for my ******* choice of words but now Im so ******* pissed off!

---

### Post by banewman on 2007-11-21
We've all been there...
Nothing hurts more at the time...
There are no curses strong enough to convey the emotion....
Put the ubuntu live cd in and open gparted as a check before you drag the knife across your throat :)

---

### Post by SUparJErk on 2007-11-21
As far as getting a boot loader going again, it may be as simple as booting to a livecd, and running:

# grub-install /dev/hda
(assuming /dev/hda is the drive you want to install it on)

As far as recovering your potentially lost data... ehh... :(

---

### Post by MrFSL on 2007-11-21
> **SUparJErk said:**
> As far as getting a boot loader going again, it may be as simple as booting to a livecd, and running:

# grub-install /dev/hda
(assuming /dev/hda is the drive you want to install it on)

As far as recovering your potentially lost data... ehh... :(

My suggestion. Stop! Turn off the computer! - and quickly get it to a certified date recovery specialist.

---

### Post by omax on 2007-11-21
Nah this is great. Just great. windows actually managed to delete three entire partitions. Just excellent work you Microsoft-developers!

Took me about 4-5 months to get my Xubuntu to be exactly as I wanted it.
I lost all my personal pictures, programs, and all my schoolwork. My 2000-word essay that is due in a couple of days. Hurray!

I have backup on some things. But not as much as I wanted to.

Amazing

Thank you Microsoft, for destroying my life for the next couple of weeks!

( Can I take legal causes for this? I choosed to format ONE partition in Windows install CD. But it took away everything I have )

---

### Post by cyberdork33 on 2007-11-21
> **omax said:**
> Nah this is great. Just great. windows actually managed to delete three entire partitions. Just excellent work you Microsoft-developers!

Took me about 4-5 months to get my Xubuntu to be exactly as I wanted it.
I lost all my personal pictures, programs, and all my schoolwork. My 2000-word essay that is due in a couple of days. Hurray!

I have backup on some things. But not as much as I wanted to.

Amazing

Thank you Microsoft, for destroying my life for the next couple of weeks!

( Can I take legal causes for this? I choosed to format ONE partition in Windows install CD. But it took away everything I have )
The problem is that fdisk is not GPT aware... (The formatting system used on Macs). When you start fdisk, it issues a big warning:
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
```
You may be suprised to find that the other partitions might still be there. If you boot up a live linux cd you can check the GPT partition table by issuing the command:
```
sudo parted /dev/sda print
```
parted _is_ gpt aware.

---

### Post by mellowd on 2007-11-21
As far as Windows is concerned it's the only thing you'll ever put on you hard drive. Be very very careful when installing Windows after anything

---

### Post by aletheianalex on 2007-11-26
I had the same problem and thought that I lost everything.  I had to boot up from the OSX install disk and manually repair the GUID and MBR records... it was not easy since you have to do it through the terminal.  I only run Windows on a virtual hard drive now.

---

