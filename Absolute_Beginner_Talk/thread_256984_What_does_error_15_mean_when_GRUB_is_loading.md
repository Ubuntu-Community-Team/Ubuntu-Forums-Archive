---
title: "What does error 15 mean when GRUB is loading?"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by *Zebedee* on 2006-09-13
Hello all....  :) 

I have changed motherboards, now twin MMX 233, inserted original hardrive, rebooted, GRUB loading stage1.5., GRUB loading, please wait.... Error 15  ! :confused: 
So reinstalled Dapper Drake 6.06LTS from live cd, waited, waited some more, rebooted......Error 15  !!
](*,) 
On a positive note, I did manage to recover one of the hardrives from my sfdisk adventure!  :p 

Could somebody out there please tell me what Error 15 is, what it affects and if possible how to fix it?? Pleeease ;) 

Thankyou in advance,
Kind regards,
Zebedee

---

### Post by kuja on 2006-09-13
Last time I got an error 15, I believe it was a result of the drive setup and or partion setup being changed to something that isn't the same as what it was before, or something along those lines. 

To fix it you'll probably have to reinstall grub, overwriting the MBR. I think. I'll post again in a bit, as soon as I remember how to do that ...
Edit: I think you can do that with sudo grub-install (in a terminal). Give it a try.

---

### Post by Sef on 2006-09-24
> GRUB Error 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

[Grub Errors]("http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors")

---

