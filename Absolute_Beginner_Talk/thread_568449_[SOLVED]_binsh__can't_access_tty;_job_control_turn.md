---
title: "[SOLVED] /bin/sh:  can't access tty; job control turned off (initramfs)"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-05
Busybox V1.1.3(debian 1:1.1.3-5ubuntu4) Buit-in shell (ash)
Enter "Help' for a list of built-in-comands

/bin/sh:  can't access tty; job control turned off
(initramfs)



I can't get the Ubuntu Live CDROM to work with 2 PC's I have.
Anyone know of a solution?  Its pretty wide spread on the Internet that many many people are having this problem.

Thanks

Carl

---

### Post by overdrank on 2007-10-05
> **cwmoser said:**
> Busybox V1.1.3(debian 1:1.1.3-5ubuntu4) Buit-in shell (ash)
Enter "Help' for a list of built-in-comands

/bin/sh:  can't access tty; job control turned off
(initramfs)



I can't get the Ubuntu Live CDROM to work with 2 PC's I have.
Anyone know of a solution?  Its pretty wide spread on the Internet that many many people are having this problem.

Thanks

Carl

Hi could you give some specs on the system?

---

### Post by Wynne G Oldman on 2007-10-05
> **cwmoser said:**
> Busybox V1.1.3(debian 1:1.1.3-5ubuntu4) Buit-in shell (ash)
Enter "Help' for a list of built-in-comands

/bin/sh:  can't access tty; job control turned off
(initramfs)



I can't get the Ubuntu Live CDROM to work with 2 PC's I have.
Anyone know of a solution?  Its pretty wide spread on the Internet that many many people are having this problem.

Thanks

CarlImmediately after the CD has started booting, insert a blank floppy into the FDD. Take it out when you get to the desktop, and carry on installing.

---

### Post by Pumalite on 2007-10-05
You can also try to boot the Live CD with this:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

### Post by cwmoser on 2007-10-05
Neither of these work.

Neither the floppy disk trick nor the modprobe piix

This PC is an AMD Athlon 2000+, AGP Video card, 768MB RAM, ASUS motherboard.

Carl

---

### Post by overdrank on 2007-10-05
> **cwmoser said:**
> Neither of these work.

Neither the floppy disk trick nor the modprobe piix

This PC is an AMD Athlon 2000+, AGP Video card, 768MB RAM, ASUS motherboard.

Carl

Ok what type video card, nvidia, ati? Also did you run checksum on the cd if you burned the cd.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by cwmoser on 2007-10-05
I tried to boot the Ubuntu live cd using two different ATI Video cards (AGP).

I tested the Live CDROM and it is good.

The PC boots Windows XP just fine.

Carl

---

### Post by overdrank on 2007-10-05
> **cwmoser said:**
> I tried to boot the Ubuntu live cd using two different ATI Video cards (AGP).

I tested the Live CDROM and it is good.

The PC boots Windows XP just fine.

Carl

Ok have you tried F6 and remove quiet splash from the kernel line to see any errors? And you may add noapic to the line and then press enter.

---

### Post by Pumalite on 2007-10-05
[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

---

### Post by cwmoser on 2007-10-06
I removed "quiet squash" and added "noapic" at the end of the options line and Ubuntu stats booting  with a lot of text messages.  Then I get a black screen with nothing on it.

Any other suggestions?

Thanks much.

Carl

---

### Post by overdrank on 2007-10-06
> **cwmoser said:**
> I removed "quiet squash" and added "noapic" at the end of the options line and Ubuntu stats booting  with a lot of text messages.  Then I get a black screen with nothing on it.

Any other suggestions?

Thanks much.

Carl

Hi, you can try and remove the splash again and add vga-771. And if you get a black screen then use the ctrl,alt, F1 keys at the same time and see if this will get you to the command prompt.

---

### Post by cwmoser on 2007-10-06
OK, now I have got Ubuntu to install.  For those who have similar install issues, this is what I have learned from the contributors on this thread:

Using the Live CDROM:
- press F6 for options and add:  noacpi to the end of the options line.
- when a blank black screen appears, press Ctrl+Alt+F1 to get a command line console-- then press Ctrl+Alt+F7 to get the Ubuntu Gnome desktop GUI to appear.
- Then Click on the the Install icon to install Ubuntu to your Hard Drive.

Thanks to everyone on this thread for the solution.  If you hear of others getting this type error, pass on what we have learned.

Carl

---

### Post by overdrank on 2007-10-06
> **cwmoser said:**
> OK, now I have got Ubuntu to install.  For those who have similar install issues, this is what I have learned from the contributors on this thread:

Using the Live CDROM:
- press F6 for options and add:  noacpi to the end of the options line.
- when a blank black screen appears, press Ctrl+Alt+F1 to get a command line console-- then press Ctrl+Alt+F7 to get the Ubuntu Gnome desktop GUI to appear.
- Then Click on the the Install icon to install Ubuntu to your Hard Drive.

Thanks to everyone on this thread for the solution.  If you hear of others getting this type error, pass on what we have learned.

Carl
Great glad to hear its working, could you mark this thread as solved
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Good luck!

---

### Post by geeree on 2007-10-07
> **cwmoser said:**
> OK, now I have got Ubuntu to install.

This solution doesn't work for me on a Core 2 Duo machine with Windows Vista in one of the partitions. Worse, I don't even understand this problem? Any pointers?

Girish

---

### Post by Pumalite on 2007-10-07
You can always try Alternate CD.

---

