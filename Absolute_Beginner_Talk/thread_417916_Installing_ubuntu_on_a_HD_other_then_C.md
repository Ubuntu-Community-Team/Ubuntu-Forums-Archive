---
title: "Installing ubuntu on a HD other then C:"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by donhogan on 2007-04-22
I have win xp64 on my C: drive and I attempted to install ubuntu  64bit on another completely empty drive. However it doesn't see my xp OS and so won't give me an option on startup...My system still starts in Windows. How can I get a boot option happining so I can maintain my win OS while I get familiar with ubuntu? I had a look in the GRUB file and it is empty? Can anyone help...tks:(

---

### Post by BoneKracker on 2007-04-22
If your grub file is empty you shouldn't be seeing an option to boot Ubuntu either.

Locate the file /boot/grub/menu.lst and post its contents here.

---

### Post by donhogan on 2007-04-22
/media/disk/boot/grub

it has nothing in it but #s

I was able to get into ubuntu via a live boot disk, after which I was able to get into the drive  that I installed ubuntu on......

there appears to be lots of info on butting both OSs on one drive (C:) after a little partitioning but I wanted to keep both OSs on separate drives?
thks Bonecracker...

---

### Post by BoneKracker on 2007-04-22
You can put them on separate drives easily.  The installer gave you the option to do that.

However, it looks like the bootloader did not fully install.

If you haven't done much yet, you might want to just run the install over again.

During the partitioning activity, pick the second drive for the location to install Ubuntu.  (If you have ide drives, then your Windows will be on /dev/hda, and you'll be putting Ubuntu on /dev/hdb; if you have sata or scsi drives, then your Windows will be on /dev/sda, and you'll be putting Ubuntu on /dev/sdb).  (Assuming you have only two drives.) 

During the bootloader activity (GRUB), let it find any existing operating systems.

---

### Post by donhogan on 2007-04-22
I have 4 drives, 2 striped raptors, and 2 large seagate SATAs, but I have a huge amount of data on C: where the win XP64  resides so I don't really have an option to switch win xp to another drive. I did 3 installs and always the same results. Is there some script I could put in the GRUB that would recognize both, Where could I find or download a ready made "kernal"...I'm really new at linux so even the word kernal sounds alien?

---

### Post by BoneKracker on 2007-04-22
The installer will intall a ready-made kernel.

Okay, so you have four drives.  Two seagate SATAs and two raptors.  Lay out the four drives for me...

Are the raptors SATA?
Which drives are striped
Are the striped drives a RAID0 plugged into an SATA RAID controller built into your motherboard?
What are the other two drives plugged into (what kind of controller)?
Which of those drives is XP installed on (which drive, or array, is C:  )
Which drive, or array, do you want to put Ubuntu on.
What's on the drives?

Drive
/dev/hda;   raptor;            ata;             raid0;   part of C:
/dev/hdb;   raptor;            ata;            raid0;    part of C:
/dev/sda;   seagate;        sata;           non-raid; unused
/dev/sdb;   seagate;        sata;           non-raid; unused

I know that's not it, put can you clarify the picture?

Which two Two are striped -- does that mean you are using an SATA RAID controller that's built into your motherboard?  And which drives are they?  Is C: a RAID0?

---

