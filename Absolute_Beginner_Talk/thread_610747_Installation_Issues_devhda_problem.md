---
title: "Installation Issues: dev/hda problem"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by strfish7 on 2007-11-12
Hello,

Well, I've run out of ideas, so please help if you can.  Trying to install Ubuntu on an old AMD K7 1.2 Duron processor.  I apparently successfully installed Feisty from the CD, but upon boot it produces the following:

ACPI:  unable to locate RSDP
Alert!  /dev/hda1 does not exist.  Dropping to a shell!

Any suggestions? 

(edit) Thanks again for this helpful forum...just nosing around and formulating the problem gave me another idea to try, which worked!

---

### Post by overdrank on 2007-11-12
> **strfish7 said:**
> Hello,

Well, I've run out of ideas, so please help if you can.  Trying to install Ubuntu on an old AMD K7 1.2 Duron processor.  I apparently successfully installed Feisty from the CD, but upon boot it produces the following:

ACPI:  unable to locate RSDP
Alert!  /dev/hda1 does not exist.  Dropping to a shell!

Any suggestions?  Thanks in advance.

Hi and welcome, how did you install, via the live cd or the alternate cd? DO you have more than one drive and did you install the grub on a different drive?

---

### Post by strfish7 on 2007-11-12
Thanks for your response...I installed the live CD, and I only have one hard drive.

---

### Post by overdrank on 2007-11-12
> **strfish7 said:**
> Thanks for your response...I installed the live CD, and I only have one hard drive.

Ok you were able to partition the drive and then complete the install and the system asked you to reboot? And there were no other issues using the live cd?
Also there is no other OS on the drive?

---

### Post by strfish7 on 2007-11-12
Correct...I got through the install and this would be the first reboot.  Not a dual-boot install; no other OS.

---

### Post by overdrank on 2007-11-12
> **strfish7 said:**
> Correct...I got through the install and this would be the first reboot.  Not a dual-boot install; no other OS.

Sorry for the delay but I have not encounter this error before. I will have to search a little more. :(

---

### Post by strfish7 on 2007-11-12
Yikes, I hope I haven't stumped the community on my first post! I really do appreciate the help...thanks.  (Edit)  Ok, I have solved this issue.  I had 2 CDW drives connected, and I disconnected one of them and reinstalled using the live CD.  Success!

---

