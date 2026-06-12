---
title: "Taking Grub off and starting computer normally."
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by afropete14 on 2007-06-12
Ok it looks like Ubuntu is not going to work on my computer so last night i formatted the partition Ubuntu was on and when I restarted it said something about not finding Grub.  I restarted it again and it said it couldn't find the system disk.

Help!

I am guessing grub just wants to keep working but i just don't know how to turn it off.

---

### Post by Inxsible on 2007-06-12
Ubuntu on install overwrites the MBR with GRUB. Since you removed Ubuntu, you will need to re-write MBR with NTLDR, which is the Windows version of GRUB - so to speak.
 
Search the forums on how to install NTLDR. Give in key words like MBR, NTLDR. I am sure you will find lots of helpful threads which detail the process.

---

### Post by netwerx on 2007-06-12
If you put XP back on your machine, you will need to boot off your XP disk.
on the first menu, pick "R" for recovery console.

Once at the command line, type "fixboot" and confirm your ok with it running.
After that, run "fixmbr"
again, confirm.

That will get a MS friendly boot sector back on the drive.

---

### Post by afropete14 on 2007-06-12
Ok i did like you said and it says press any key to boot from cd (so I press a key) and then it goes . . . . Grub loading stage 1.5
grub loading please wait
error 17

this is drving me crazy!

---

### Post by afropete14 on 2007-06-12
THANK YOU THANK YOU THANK!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  I tried a new keyboard and there you go it started!  If Ubuntu would have only worked that would have made it even better.

---

