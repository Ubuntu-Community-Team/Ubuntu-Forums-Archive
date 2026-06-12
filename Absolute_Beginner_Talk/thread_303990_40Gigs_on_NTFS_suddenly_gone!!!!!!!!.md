---
title: "40Gigs on NTFS suddenly gone!?!?!??!?!?!??!?!"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by leetrefz on 2006-11-21
> chief@chief-toshiba:~$ sudo qtparted
Password:
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
No Implementation: Support for opening ntfs file systems is not implemented yet.



yet qtparted still shows it being as full as before, but
/media/hda5 appears empty suddenly (rocking back and forth in fetal position)

all I did was try to play a file, switch sessions, and bam! my life is over. Why god why?!?!? WHY!??!?!??!?!? 

just ordered a dvd-burner to back it up... it would have come next week
I'm going back to the Mennonite colony.

---

### Post by jd65pl on 2006-11-21
You could try booting with a live CD, mounting the drive to see if the data is recoverable.

---

### Post by leetrefz on 2006-11-21
ok, a reboot did the trick,

thank you, you may now return to your lives.

I'm checking if my user name can be changed.

---

### Post by PriceChild on 2006-11-21
Unless you use ntfs writing then Linux **cannot** touch your ntfs drive.

---

### Post by leetrefz on 2006-11-21
well that's what I thought. thanks.
My heartrate is normal again.

---

### Post by Ben Sprinkle on 2006-11-21
On the other hand if you do want support [click here](http://ubuntuforums.org/showthread.php?t=217009) to find out how. Kind of risky though.

---

### Post by leetrefz on 2006-11-21
thanks, think i'll back it up and reformat. xfs I guess is the way to go? same disk, no other OS around. not after xubuntu.

---

### Post by Ben Sprinkle on 2006-11-21
XFS?
It's EXT3 for Ubuntu. :)

---

### Post by leetrefz on 2006-11-21
Had the option in qtparted on the live cd.... 
wikipedia:
> XFS has been merged into the mainline Linux 2.4 (as of 2.4.25, when Marcelo Tosatti judged it stable enough) and 2.6 kernels, making it almost universally available on Linux systems. Installation programs for the SuSE, Gentoo, Mandriva, Slackware, Fedora, Ubuntu and **Debian** Linux distributions all offer XFS as a choice of filesystem.

Sounded like it might be better than ext3. whatever works I guess.

---

### Post by Ben Sprinkle on 2006-11-21
Oh, ext3 for me. :)

---

