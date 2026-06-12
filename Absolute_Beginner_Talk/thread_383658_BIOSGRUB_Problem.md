---
title: "BIOS/GRUB Problem"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by saxofoner on 2007-03-13
I've had a dual boot system with Ubuntu and Windows for a while, and I recently ruined by Ubuntu partition trying to install Beryl.  So I'm not going to bother with that again.  Anyway, I've always had hard drive issues, I think mostly due to my hard drive SATA cable.  So now I've got a real problem:

        **Whenever I boot, the BIOS/BIOS Setup Menu/GRUB/LiveCD Menus/GRUB all take keyboard commands for about 10 seconds after power on, then they stop.  It's like all input is suspended.  But if I can select Windows from that menu fast enough, it boots, and the keyboard works fine.**  And Windows runs CHKDSK almost every time I boot, but never finds an issue.  So, I was going to use a Live CD to mount my Linux partition (I need help doing that, too...), back up all my stuff, and then totally wipe that Linux partition, and reinstall.  But I can't use my BIOS properly, so I don't know what to do.  Can anybody help me with any part of this?

---

### Post by Najand on 2007-03-13
If windows works and you don't need the old ubuntu, try Windows Recovedry to overwrite your Master BootLoader and after that, try to edit your BIOS setup and install ubuntu after that again. Actually I am so eager to know do you have the same problem using USB keyboards, too?

---

### Post by saxofoner on 2007-03-13
What exactly will Windows Recovery Erase?  I don't want to have little remains of my various OSs scattered about my hard drive...  I haven't tried a USB keyboard actually.  I'll do that later.

---

### Post by Najand on 2007-03-13
Try using USB keyboard first before trying to delete  other things.
I am not sure about Micro$oft products as they are close sources but if you are lucky it just overwrite MBL and you won't see grub anymore after that.

---

### Post by saxofoner on 2007-03-13
But.... *sniff* I like my GRUB...  I just want to fix my Linux partition and make my stupid BIOS take input.  See, it's not GRUB's fault, I don't think.  Even if I go into the normal old BIOS menu where you change boot order and stuff, it still stops responding.  Is that extremely strange?  Or is it some normal error I've never heard of?

---

### Post by Najand on 2007-03-13
Hmm, it might be strange but not EXTREMELY strange. However, what kind of chipset, motherboard and processor are you using?

---

### Post by saxofoner on 2007-03-13
It's NForce4, I believe, an ASUS Mobo A8Nxx series, I can't remember which, with an AMD Athlon  2X Processor.  I can't remember the other details right now, will post later if necessary.

BTW I couldn't find any other instances of this problem on the forums.

---

### Post by Najand on 2007-03-13
Hmm, did you try to update  your BIOS drive, if any newer available? you can use windows so you can install it if there is any. Try to check it out.

---

