---
title: "Another timid noob with a question"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Jim D v2.0 on 2006-10-17
I am a newbie to Linux, and somewhat timid about the great unknown, so please be gentle.

I tried out the Live CD from ubuntu and was quite impressed so I decided to do an install.

Currently I have Win2K installed on a 40GB drive (primary master) and a 160GB drive for data, documents and miscellaneous stuff (primary slave). I disconnected those two drives and installed ubuntu 6.06 Linux on a different 40GB drive (secondary master). The CD/DVD drive is on the secondary slave.

I have been using the ubuntu Linux installation now for about a week and need to get back to windows for some work. I like Linux and do not want to uninstall but some things need to be done yet in windows.

Here is my question: What will happen if I re-connect my windows drives without disconnecting the drive containing Linux and then boot? And is this a good idea? I would like to be able to dual-boot.

I have been searching for an answer to my question, but so far no luck for my particular situation. If these questions have been answered somewhere else would someone point me in the right direction?

---

### Post by Aberrix on 2006-10-17
If you hook back up the windows drive it will probably boot straight into windows.

If you want to get a choice (win or ubuntu), you'll probably have to install GRUB on the windows drive (mbr).

---

### Post by randiroo76073 on 2006-10-17
Check this thread, should find the answer :)
[http://www.ubuntuforums.org/showthread.php?t=275661](http://www.ubuntuforums.org/showthread.php?t=275661)

---

### Post by Tomosaur on 2006-10-17
Since Windows is on the Primary master, Windows will boot up, ignoring Linux. You may want to install Grub so that you can choose on startup, or you can use a BBS popup system (if you have one) to select which drive to boot from.

---

### Post by Jim D v2.0 on 2006-10-17
Thanks for the help, it is greatly appreciated.

---

### Post by megamania on 2006-10-17
I've been doing as suggested in the link above for years with no problem: I just jump into the bios and select the hard disk I want to boot from. 
One hard disk is fixed, while the other one is in a removable tray, so I can take it out anytime (for example, when reinstalling on the primary h.d.).

It works flawlessly and you don't have to mess with Grub (not that it is a mess, but I prefer to avoid it if I can)...

---

### Post by caravel on 2006-10-17
If you want to avoid installing the bootloader over your windows mbr, you can install each driver separately and use the bios to switch OS.  Some bios's come with the F8 boot menu (as article), so it is easy enough to do.

On the whole it's easier to install GRUB to the active windows partition.  If you need to remove GRUB for any reason and restore the windows bootloader you can do it by booting from your windows installation CD, running setup and going to the recovery console, logging in and entering 'fixmbr' and/or 'fixboot'.

---

