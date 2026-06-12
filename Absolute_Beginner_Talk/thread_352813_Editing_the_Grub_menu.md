---
title: "Editing the Grub menu"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by cbow12 on 2007-02-03
I'm still trying to resolve my dual boot problem.
After searching several threads on the issue, I believe I can simply edit my menu.lst file.
Drive 0 Primary boot drive) will be IDE primary where Linux resides, and Drive 1 is SATA drive where Windows XP Pro resides.

I tried to add the following to my menu.lst file:

title          Microsoft Windows XP Professional
root         (hd1,0)
makeactive
chainloader +1

My question is this:
Is this correct, and do I add it first or last?  Also, the menu.lst is read only and won't let me save it.  How do I do that?

---

### Post by taurus on 2007-02-03
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by confused57 on 2007-02-03
See this guide:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by cbow12 on 2007-02-03
OK, I checked all of these threads, and they sounded promising, but ultimately I couldn't get enough info to do anything.
I think the problem is grub can't see the SATA drive where Win XP is.
code: sudo fdisk -l:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14216   114189988+  83  Linux
/dev/hda2           14217       14593     3028252+   5  Extended
/dev/hda5           14217       14593     3028221   82  Linux swap / Solaris

It doesn't even mention the SATA drive.
I think I could edit the menu.lst file all day and it wont help me at all.

Any ideas on how to get grub to see the SATA drive which is NTFS format?

---

### Post by louieb on 2007-02-03
Is the fdisk from the Ubuntu install. There is something very wrong if fdisk does not see the SATA drive.  Try running it from the Live CD. Can you change BIOS to boot the SATA drive?   Did you just install the IDE  drive? 
Don't have a good answer for you. But the first order of business is get the SATA drive working.
Once fdisk can see the drive the we can help you with the GRUB configuration file entry. What you have will most likely work.

---

### Post by ramjet_1953 on 2007-02-04
Try installing the attached software.
It provides several options for editing GRUB and all in a graphical emvironment.

Regards,
Roger :cool:

---

### Post by louieb on 2007-02-04
I just saw your other thread on the dual boot problem. [http://ubuntuforums.org/showthread.php?t=345838](http://ubuntuforums.org/showthread.php?t=345838)
You have an odd setup and may not be able to dual boot with GRUB. Some questions just don't have an answer.

I wish I had see the stuff you posted there before  I made my first reply.
 
> Yes, XP is on the SATA drive, and Ubuntu is on the primary IDE drive. The secondary IDE drive is a DVD burner. I also have a USB external drive that I use for back-ups, but it isn't always on. When it is on, I can see that drive from either operating system.
As it is right now, I can boot into Windows and the system doesn't even see the IDE drive. If I go into the cmos setup, I can change the IDE drive to the primary boot drive, then the system reads the grub file and boots into ubuntu, but doesn't see the SATA drive.
I have to go into the cmos setup and manually change the target boot drive each time I want to switch back and forth.
What I want is a menu option each time I boot to go into XP or Ubuntu, whichever I choose (without changing the cmos setup.)
I'm wondering if Boot Magic would work here?
 		 	 		 		 		 		 		 	 		 			 			
BTW: In the future instead of starting a new thread on the same problem. Go into the original thread and create a new reply with the word "bump" or 'anybody". This will move your thread to the top of the list. 
Please wait 24 hours between "bumps".

---

### Post by cbow12 on 2007-02-05
OK, thanks for the tip.  Actually, this thread was a question about how to edit the Grub file, but it quickly turned into the dual boot issue.
I'm still not sure why Ubuntu can't see the SATA drive with XP on it.  Can Ubuntu see an NTFS formatted drive?  Maybe that is the problem.
Here is something even wierder:  If I have my USB back-up Drive turned on when I boot, the CMOS automatically changes and puts the IDE drive as the boot-up drive, even if I had left it with the SATA drive as the primary boot drive.  To get to XP then, I have to turn off the USB drive and go int CMOS and manually change the primary back to the SATA drive.  Strange, eh?

Anyway, thanks for the comments.  Let me know if anyone has anymore thoughts on the dual boot issue.

---

