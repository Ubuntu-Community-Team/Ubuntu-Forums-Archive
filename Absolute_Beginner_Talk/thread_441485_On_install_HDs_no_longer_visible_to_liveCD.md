---
title: "On install HDs no longer visible to liveCD"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by ginestre on 2007-05-12
I stopped the first attempt at a dual boot installation o Feisty on a machine with XP as I wanted some help, which the forum generously gave. I stopped immediately prior to the partitioning,  at  a point where the partition manager had already seen the HDs installed, but had not acted.

Encouraged by the help received from the forum, I decided to go all the way, and started over with the live CD. Except that now the HDs are no longer visible to the live Cd or the partition manager!

Where have they gone?

---

### Post by taurus on 2007-05-12
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Happy_Man on 2007-05-12
So you mean that you were absolutely sure you didn't actually tell it to do anything, and clicked the "x" up in the corner of the install program? Right? Have you tried using the command 
```
sudo mount /dev/sda
```
from the LiveCD? We will need some more info than this....

---

### Post by ginestre on 2007-05-12
No, I did nothing; windows still boots happily. Simply this time round the partotion editor windoe where it says 'tell me what you want to do' (or words to that effect) is completely unpopulated. Before it had stuff in it. But first time round I quit at this point ,  so had done nothing: and this time round I can't do anything because the window is unpopulated

Can I run the sudo mount /dev/sda command from the live CD without risking damage to the windows partition?

---

### Post by Happy_Man on 2007-05-12
Yes, all that command is telling the LiveCD to do is to mount that partition so that you can access it through the file manager.

---

### Post by ginestre on 2007-05-12
Well. I went to the machine to load the live CD again, so as to try the sudo, and this time got an error message that is entirely new:

/bin/sh: can't access tty: job control turned off
inittramfs [33.q6749] ata1.00 failed to set xfermod (err_mask=0x40)

is this part of the same issue?

---

### Post by ginestre on 2007-05-12
however, on a new reboot the live cd worked out OK. Maybe the above was just a glitch. 
In a terminal, running sudo fdisk -l gives me the list of 
/dev/sda1  NTFS
/dev/sda2  fat16
/dev/sda3  fat16
/dev/sda4  fat16

---

### Post by bjigbs on 2007-05-12
Im actually having the same problem as mentioned above, and having no luck finding a fix for it mine doesnt go away and I cant even get to a terminal

any help would be appreciated

---

### Post by bjigbs on 2007-05-12
also it keeps trying to access my floppy drive, when I unplug it it doesnt go to the

/bin/sh: can't access tty: job control turned off
inittramfs [33.q6749] ata1.00 failed to set xfermod (err_mask=0x40)


it simply locks and and after removing quiet splash from in boot option it just keeps trying to access HD0, maybe thats the problem my drives start at hd1 according to the bios???

thanks again guys

---

