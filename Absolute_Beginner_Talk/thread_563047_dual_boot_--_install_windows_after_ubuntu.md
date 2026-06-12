---
title: "dual boot -- install windows after ubuntu"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by insub2 on 2007-09-29
Ok ok.  here is teh deal:
I installed linux thinking that'd be a-ok.  and it is.  been using it with joy for a couple of months.......except that new ipod classic doesn't like linux one bit.
i need itunes (unless i get this working: [http://ubuntuforums.org/showthread.php?t=556612]("http://ubuntuforums.org/showthread.php?t=556612")).  so i need windows.

i set up the NTFS partition and have a windows disk ready to go in the drvie when i realized windows does that MBR thing that will overwrite grub leaving me with just windows.

I know i could do that then re-install linux.  but it was a mild headache (ati and broadcom...need i say more?)

My question is:
how do i install windows AFTER linux?

THNX

---

### Post by kellemes on 2007-09-29
Remember, when preparing your partition scheme.. Windows insists on installing on the first partition of the first hard disk.
The easiest way to fix your bootloader after Windows has trashed it.. is to use [SuperGrubDisk]("http://supergrub.forjamari.linex.org/"), download/burn the iso and boot with it after installation of Windows..

---

### Post by oilchangeguy on 2007-09-29
windows mbr will overwrite grub. you can use the live cd to restore grub. search the forum for a how to on restoring grub. (i'm not on my main computer, and don't have the link available)

---

### Post by MrHippocampus on 2007-09-29
The basic steps are these:

1. Install windows (with a pre-made partition ready as youve done)
2. Restore grub using ubuntu livecd (instructions [here/]("http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub"))
3. Add in your new windows installation to the grub menu (it wont be picked up automatically)

---

