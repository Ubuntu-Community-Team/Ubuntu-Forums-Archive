---
title: "Need to repair MBR with no CD drive"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by kramulous on 2007-09-25
Damn this is embarrassing.

I needed to remove kubuntu install (temporarily) and go back to XP.  The machine is an IBM Thinkpad X60 and there is a partition with the 'recovery install' with about 5GB of data.  The X60 has no CD drive.

I needed XP so booted into recovery partition, it formatted drive (this is all the information it gave me, I do not know the status of partitions on the disk) and selected 'restore to factory [setting/default/can't quite remember but was what I wanted].  It worked away.

When it finished it rebooted and then I got the GRUB error 22.

From reading in other threads I realise that I need to repair the MBR, but having no cd drive is causing a bit of a pain.  I had been in the process of getting my usb stick to have ubuntu, but didn't get around to the 'syslinux sf /dev/sdb1' step ... dammit!  This would have been mega sweet.

Any pointers?  (Apart from getting hold of a usb cd drive).  I have usb hard-drives, and nas devices. XP cds, ubuntu/kubuntu cds.

---

### Post by LaRoza on 2007-09-25
The Super Grub Disk can be used from a floppy or USB drive:

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

It works, used it many times.

---

### Post by anaconda on 2007-09-25
USB-stick or a floppy drive would do the trick.
eg. Knoppix can be run from USB-stick,  or if you can boot to any old DOS you can fix your MBR with "fdisk /mbr" (dont know if it works with SATA hd:s?)
And once you get to almost any linex you can eg. install a bootloader, which fits completely to the mbr. all of them can propably boot to windows.

yet another choise is to take the hd out of your laptop, and connecting it to another machine and reapiring the mbr in there. (en external usb enclosure could be of help in here.. costs about 15&#8364; )

PS. Did you know that if you take the hard-disk out of your USB-hd you can put a norma CD/DVD drive in its place? It wont fit to the enclosure, but otherwice it works well.. (used Cd drives cost about 5&#8364;)

EDIT: the super grub disk sounds easier..

---

### Post by kramulous on 2007-09-25
Thanks to both of you.  I'm trying the Super Grub method now.  Was hoping to have it done by now but am having a few minor hiccups ... should be fixed very soon [fingers are crossed].  

I appreciate this help ... will let you know how it went.

---

### Post by kramulous on 2007-09-30
Just a follow up to finish off this thread.  It was fixed on the day I submitted this question but as a courtesy to the above posters for offering a solution I should finish up.

I had trouble with super grub booting from a USB device.  This was most likely a user error.  I'll get it going on a small usb a bit later as I see it as a useful thing to have in my box of useful sh*t.

In the end, I was able to make the usb bootable (into free-dos) using instructions found on [http://www.marlow.dk/site.php/tech/usbkeys](http://www.marlow.dk/site.php/tech/usbkeys).  I then used fdisk from free-dos.  This enabled me to fix the MBR.

Thank you to anaconda and LaRoza.

---

