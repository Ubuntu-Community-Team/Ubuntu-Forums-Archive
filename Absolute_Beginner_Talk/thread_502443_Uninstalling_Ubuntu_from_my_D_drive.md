---
title: "Uninstalling Ubuntu from my D drive"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by Hork on 2007-07-16
On my D:\ I have ubuntu and on C:\ I have Windows.

Is it possible to remove everything of Linux from my D:\ Drive and just make it usable by Windows?  I don't have my Windows XP CD (I might, but I'd have to look) so that's no go. :(

---

### Post by MiCovran on 2007-07-16
As I understand, you want to remove ubuntu completely from your computer. The simplest way to do that is by reformatting the D:\, putting the windows install cd and choosing the repair option. Otherwise, GRUB will be left in your master boot record and you won't be able to boot. I don't know how to remove GRUB without windows cd.

---

### Post by Hork on 2007-07-16
Drats, there's no other way possible? :(

---

### Post by bodhi.zazen on 2007-07-16
You can restore the MBR with [supergrub](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by BlueNoteExpress on 2007-07-16
Wouldn't the "fdisk /mbr" command from a Windows command prompt restore the MBR too?

---

### Post by stchman on 2007-07-16
The fdisk /mbr command cannot be invoked using Windows XP as it is not included in XP.  You will either need to make a boot floppy or boot CD with fdisk on it.  You can get the bootdisk files here.

[http://www.stchman.com/tools/bootdisk.zip](http://www.stchman.com/tools/bootdisk.zip)

If you have a floppy drive and XP make a bootable floppy and copy the files here.

If you don't have a floppy then make a bootable CD using K3B and copy the files on there.

[http://www.stchman.com/boot_cd.html](http://www.stchman.com/boot_cd.html)

Is there are particular reason you wish to rid yourself of Ubuntu?  Do you wish to make your PC more vulnerable to viruses and spyware?  If yes then you are on the right track.

---

