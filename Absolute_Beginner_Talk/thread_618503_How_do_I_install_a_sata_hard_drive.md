---
title: "How do I install a sata hard drive?"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by bwallum on 2007-11-20
Is their anything special to do to install a SATA hard drive? Harware Information is calling it SCSI. My Places>Computer>Filesystem can't see the drive.

Rgds
Bob

---

### Post by jfinkels on 2007-11-20
Did you plug in both the data and power cables?

You should be able to see the drive when you run the following command from the terminal. If not, post the output:```
sudo fdisk -l
```

---

### Post by bwallum on 2007-11-20
Yes, I can now see it thanks, this is the output:-

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000313af

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9355    75144006   83  Linux
/dev/hda2            9356        9729     3004155    5  Extended
/dev/hda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

hda is IDE, sda is the new sata drive and seems to need a partition. What's the command for that please?

---

### Post by taurus on 2007-11-20
Install gparted 

```
sudo apt-get update
sudo apt-get install gparted
```
and use it, System -> Administration, to create a partition, /dev/sda1, and format it as ext3 and mount it to /media/sda1.

---

### Post by bwallum on 2007-11-20
Installed Gparted, started it....and....Scanning all devices............

.....and it just keeps scanning. Minutes drift by and  Scanning all devices......

Is this correct? Does it take a long time normally?

---

### Post by Dr Small on 2007-11-20
> **bwallum said:**
> Installed Gparted, started it....and....Scanning all devices............

.....and it just keeps scanning. Minutes drift by and  Scanning all devices......

Is this correct? Does it take a long time normally?
No.

---

### Post by bwallum on 2007-11-20
Uninstalled then re-installed through Synaptic....Scanning all devices.......

Definately not right, system been as sound as a pound up to now. Everything else works, all fully updated.

Can we try a CLI route please?

---

### Post by bwallum on 2007-11-20
Ah! Gparted has decided to wake up, I am now setting up new partition. VERYYYYYY SLOWLYYYYYYY..

Thanks for all your help!

---

### Post by bwallum on 2007-11-20
Gparted has just disappeared! I thought it was writing a 'label' (defaulting to msdos style is a bit of a sick joke though), it dropped into it's ....Scanning all drives.....mode and scanned off the edge of the planet it seems.

Can anybody help with a CLI approach please? What is libparted?

---

### Post by skymera on 2007-11-20
ok try qtparted

i found gparted to be a bit...sucky at times.

---

### Post by bwallum on 2007-11-20
qtparted is scary, but I think I have the drive formatted and active.

Now how do I mount it to /media/hds1 please?

---

### Post by taurus on 2007-11-20
What filesystem did you create for /dev/sda1?

```
sudo fdisk -l
```

---

### Post by bwallum on 2007-11-20
These are my two drives now:-

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000313af

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9355    75144006   83  Linux
/dev/hda2            9356        9729     3004155    5  Extended
/dev/hda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006e367

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161   83  Linux

I formatted the sata drive to ext3. I can see it on the Desktop and also at /media/sata_1.

However I can't put things in it, it says I don't have permission.

ext3 was wrong eh? Is ext3 just a system partition for root? Should I use ext2?

---

### Post by taurus on 2007-11-20
Actually, ext3 is a great choice.  You just need to change the ownership of /media/sata_1 from root to your login name.  _Assuming_ your login name is **wallum**, run

```
sudo chown -R** wallum**:**wallum** /media/sata_1
ls -la /media
```

---

### Post by bwallum on 2007-11-20
Great! Now its mine! Thanks for the help. I have one small tidy that I would like to do. It appears on the Desktop and I like a clean one. How do I stop (and possibly start it again) from appearing on the Desktop?

---

### Post by taurus on 2007-11-20
Log out and back in again.

---

### Post by bwallum on 2007-11-20
yep..that gets rid of it. However it is no longer mounted. I can do it manually but is there a way to do it when I boot up (fstab?) and not have it appear on the Desktop?

---

### Post by taurus on 2007-11-20
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/sata_1   ext3   defaults   0   1
```
Save it.  Then, run

```
gconf-editor
```
And tell it not to display icons on Desktop

OR

Mount /dev/sda1 somewhere else like /mnt/sata_1.  Then, you need to create /mnt/sata_1 and change the ownership of /mnt/sata_1 again.  You only have to do that once.

---

### Post by bwallum on 2007-11-20
Thanks taurus, I managed to lose it this time but then I am feeling tired. I can see how to do it though, thanks to your guidance. I really appreciate your time.

Its midnight my end and a long day awaits, so 'bye just now', as we say in the Borders.

---

### Post by bwallum on 2007-11-22
Hi taurus

Thanks again for all your help. This just to let you know I found the hard drive again and alls well. Its the first sata drive I've had, it is really quiet. In trying to recover I also found this

[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

I have to say I found the CLI approach, using fdisk, quick and foolproof. With qtparted I could see the drive, partition and format it, but lost it on re boot. Not too sure why. The Gnome Partition Editor, GParted, is a disaster in my opinion, you are being too generous calling it sucky.

Anyway thanks again, it was really helpful.

Kind regards
Bob

---

