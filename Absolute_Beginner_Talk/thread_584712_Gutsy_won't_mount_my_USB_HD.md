---
title: "Gutsy won't mount my USB HD"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by Angus77 on 2007-10-21
s

---

### Post by Qwerty_ on 2007-10-21
Is your USB hard disc formatted as a NTFS drive.

If it is you need to run the following

```
sudo apt-get install ntfs-config
```

Then run

```
sudo ntfs-config
```

And select the necessary boxes.

---

### Post by Angus77 on 2007-10-21
(accidentally posted before I meant to)

I upgraded to Gutsy, and now I can't mount my my external HDD!

I get an error message saying 

```
Unable to mount the volume 'MISC'
Unable to mount the volume 'VIDEO
Unable to mount the volume 'AUDIO'
Details
mount: wrong fs type, bad optiom, bad superblock on /dev.sb1,    missing codepage or helper program, or other error     In some xases useful info is found in syslog - try     dmesg | tail or so
```

So I tried dmesg | tail and got

```
[ 3804.833019] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[ 3804.834020] sdb: Write Protect is off
[ 3804.834024] sdb: Mode Sense: 33 00 00 00
[ 3804.834026] sdb: assuming drive cache: write through
[ 3804.834030]  sdb: sdb1 sdb2 sdb3
[ 3804.838620] sd 3:0:0:0: Attached scsi disk sdb
[ 3804.838667] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 3805.298094] FAT: Unrecognized mount option "usefree" or missing value
[ 3805.310140] FAT: Unrecognized mount option "usefree" or missing value
[ 3805.342342] FAT: Unrecognized mount option "usefree" or missing value
```

I have no idea what any of that means!

I never had these problems in Feisty. In fact, I made these partitions using GParted on Feisty. ( I made them FAT partitions so I could use the drive with an XP machine at work)

---

### Post by Goliash on 2007-10-21
Here you can find the bug and how to solve the problem: [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025")

---

### Post by Angus77 on 2007-10-21
I can't believe I got a reply from QWERTY_ in three minutes when I hadn't posted anything but the letter "s"!

Goliash: Thanks! Now it works!

Any idea what "usefree" is?

---

### Post by Qwerty_ on 2007-10-21
Well Angus77 lots of people have been asking about NTFS questions so I used my powers of deductive reasoning to think you would be in the same boat.

---

### Post by Angus77 on 2007-10-21
Well, thanks a lot for the quick reply!

---

### Post by mgmiller on 2007-10-21
Don't keep us all in suspense.
Did it work?  :popcorn:

---

### Post by Angus77 on 2007-10-21
Yes, it does! Perfectly!

---

### Post by FrankN on 2007-10-22
> **Goliash said:**
> Here you can find the bug and how to solve the problem: [https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025")

Thank your for this link: the (simple) fix did the trick. Mounting memory cards now works fine again.

---

### Post by ossi on 2007-10-29
HOw to solve this in KDE?

---

### Post by kspn on 2007-10-29
Or Xubuntu, I installed gconf-editor and it didn't do anything

---

### Post by rabidus on 2007-10-29
This worked for me.  My prob was disconnecting my external hard drive without unmounting properly first.  Upon reconnecting the drive I was informed the drive failed to mount and the manual mount -t etc. instructions did not help.  Thanks for the link!

"Go into gconf-editor and navigate to /system/storage/default_options/vfat/mount_options, and then remove the "usefree" option from the list. Exit gconf-editor, and try hotplugging your drive again."

---

### Post by kspn on 2007-11-04
I tried that on Xubuntu and it has had no effect, When I rebooted by system into the 2.6.22-14 Kernel it worked fine. It is only with the latest Kernel that I am having issues.

---

### Post by David Bird on 2007-11-04
I replaced 7.04 with 7.10 (New Install as I put in a bigger HDD) my USB Flash Drive (FAT32) and External DVD Writer no longer work, my USB Scanner and Bluetooth transmitter work fine.

I've removed "usefree" but without any luck.

below is a log of what happens when I install my USB Flash Drive


Nov  4 16:27:42 smeg kernel: [582584.167854] usb 4-6: new high speed USB device using ehci_hcd and address 16
Nov  4 16:27:42 smeg kernel: [582584.279613] usb 4-6: device descriptor read/64, error -71
Nov  4 16:27:42 smeg kernel: [582584.495262] usb 4-6: device descriptor read/64, error -71
Nov  4 16:27:42 smeg kernel: [582584.710888] usb 4-6: new high speed USB device using ehci_hcd and address 17
Nov  4 16:27:42 smeg kernel: [582584.822711] usb 4-6: device descriptor read/64, error -71
Nov  4 16:27:43 smeg kernel: [582585.445642] usb 4-6: device not accepting address 17, error -71
Nov  4 16:27:43 smeg kernel: [582585.557464] usb 4-6: new high speed USB device using ehci_hcd and address 18
Nov  4 16:27:43 smeg kernel: [582585.782085] usb 4-6: device descriptor read/all, error -71
Nov  4 16:27:43 smeg kernel: [582585.896890] usb 4-6: new high speed USB device using ehci_hcd and address 19
Nov  4 16:27:44 smeg kernel: [582586.304197] usb 4-6: device not accepting address 19, error -71
Nov  4 16:27:44 smeg kernel: [582586.304227] hub 4-0:1.0: over-current change on port 7

any suggestions?

---

