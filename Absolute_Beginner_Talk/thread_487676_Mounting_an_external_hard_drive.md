---
title: "Mounting an external hard drive"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by malcolm07 on 2007-06-29
I can't figure out how to get Ubuntu to see my new Seagate 160GB external harddrive.

When I type "fdisk -l" I can see that the drive exists as /dev/sdb1 with a W95 FAT32 system. But I can't get Nautilus to see the disk, and I can't get Simple Backup Config to see the disk. In Nautilus, clicking on /dev/sdb1 just gives an error message.

Many thanks in advance for your help!

Malcolm

---

### Post by KIAaze on 2007-06-29
```
sudo mkdir /mnt/ext_HD
sudo mount /dev/sdb1 /mnt/ext_HD

```
This should mount your HD in /mnt/ext_HD where you should then be able to see your files.
(you can change ext_HD to whatever you want by the way)

Devices always need to be mounted before you can use them.

To unmount, it's:
```
sudo umount /mnt/ext_HD
```

---

### Post by mkeithcloud on 2007-06-29
Ok, I have the same problem. If that mounts the drive, is there any way to make it auto mount so Ubuntu recognizes and displays the drive on your desktop upon plugin?

---

### Post by KIAaze on 2007-06-29
First of all, make sure that "Mount removable drive when hotplugged" and "Mount removable media when inserted" in "System->Preferences->Removable drives and media" are checked.

Then you'll have to add an entry in the /etc/fstab file.

Here are some tutorials:
[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")
[http://www.psychocats.net/ubuntu/mountwindows#fstab]("http://www.psychocats.net/ubuntu/mountwindows#fstab")

Here's some more info:
[How to edit and understand /etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html")

I don't know exactly how the "adding to the desktop" works however.
Hopefully, it will be done automatically.

---

### Post by malcolm07 on 2007-06-30
Thank you so much for the help!! When I went back to try to mount the hard drive, it wasn't working, so I did another fdisk and found out that it had "moved" to sdc1, so I see that linux doesn't always call it the same thing. But once I figured that out, I had no problem mounting the drive, and it's merrily backing up even as we speak.

I'll also follow the tutorials about mounting the drive more permanently.

Thanks again for your help.

---

### Post by KIAaze on 2007-07-01
I think that when it changes the name of the device, it means that it hasn't been unmounted correctly (unless you connected another device before it). But I could also be wrong about this. ^^'

I'm currently having this problem with my own external HD. Sometimes it just suddenly disconnects itself.
It seems to be a hardware problem though, since it also happens in Windows.
After such a sudden disconnection, the device is always listed under another name when I do "sudo fdisk -l" again.

What I do now (in Ubuntu), is that I disable the automatic detection and just always manually mount it. Works quite well. I don't use my external HD very often, so manually mounting it doesn't bother me.

---

