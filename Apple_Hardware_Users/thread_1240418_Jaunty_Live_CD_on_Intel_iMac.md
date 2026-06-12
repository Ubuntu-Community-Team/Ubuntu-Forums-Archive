---
title: "Jaunty Live CD on Intel iMac?"
date: 2009-08-14
forum: Apple Hardware Users
---

### Post by ShinHadoken on 2009-08-14
Hello all!

Alright, I'm taking a (very remedial) computer class in order to meet grad requirements. We have 28 iMacs, dual-core I believe. What I want to do is bring an Ubuntu Jaunty live CD to boot into the Mac and get root access, and add my user to the sudoers file, that way I have access to sudo from the terminal (or graphical interface, what do I care?). Is this possible? If so, what preparation do I take on the Mac? What architecture/x-bit Ubuntu ISO do I need to burn? How do I actually boot into Ubuntu (ex. boot keys, etc) Forgive my unfamiliarity with Macs, that's why I want to be able to sudo, at least I'm at home in the terminal.

Thanks!

---

### Post by ShinHadoken on 2009-08-14
BumpP (Bring up my post, please)

---

### Post by P4man on 2009-08-15
Im not sure I understand.. you want to "hack" the apple's, by giving your user account in OS-X sudo power, is that it ? If you just want sudo in the livecd, then, its just there. No password needed, just type sudo -i in the terminal and you are root, but of the live session, not OS-X of course.

As to what cd you need, just the regular i386 one afaik. No idea how to make a mac boot from cd though.

---

### Post by bobmiller1969 on 2009-08-15
Simply hold down the c key to boot from the live CD. Also, holding down the option key will allow you to choose which drive to boot from. Either will work.

---

### Post by ShinHadoken on 2009-08-15
> **P4man said:**
> Im not sure I understand.. you want to "hack" the apple's, by giving your user account in OS-X sudo power, is that it ? 

In effect, yes. Thanks Bob for the hot key. So I simply need a 32bit x86 Jaunty disc, put it in the Mac, hold down alt (option) to choose it and boot into it, change the file, and shut it down?

---

### Post by moldor on 2009-08-16
Ah, I don't think so....  If the Mac hard drives are formatted as HFS+, I'm not sure Ubuntu has the drivers already to read that.

And then if shadow passwords are installed, no editing will work. Of course, booting on an OS X install CD and running Disk Utility will allow you to reset the root pssword.

But I didn't tell you that...:-)

I'll test what you want to do on my MacbookPro in the morning.

:lolflag:

---

### Post by ShinHadoken on 2009-08-16
Alright, thanks! Let me know what you come up with.

---

