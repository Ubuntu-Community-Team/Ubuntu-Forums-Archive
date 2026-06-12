---
title: "not entering dapper after feisty dual boot"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by madmetal on 2007-02-07
i have a hard disk with 6.06.1 (32bit) installed and running fine.
on a second half i installed 7.04 (64bit) which runs great and i am writing from within.
but now when i am trying to enter dapper i got an error message after checking root system

request_module: runaway loop modprobe binfut-464c
request_module: runaway loop modprobe binfut-464c
request_module: runaway loop modprobe binfut-464c
request_module: runaway loop modprobe binfut-464c (not sure for the last word)

from feisty i can see and change my files at dapper disk.

can i fix it and enter normally at dapper?

:(

---

### Post by Sef on 2007-02-07
From [ussg.ui.edu]("http://www.ussg.iu.edu/hypermail/linux/kernel/0102.3/0006.html").

A part of it:  > binfmt-464c is ELF -- it means your kernel came across an ELF
executable and was unable to execute it so it tried to load the ELF
binary format module. Since you have ELF compiled into your kernel
already, this didn't work.

My guess is that you have a corrupt ELF executable on your system,
which your ELF loader refuses to load. Every time someone tries to
execute it, your kernel will do a 'modprobe -k binfmt-464c'. 

From [handhelds.org]("http://www.handhelds.org/hypermail/familiar/45/4572.html"):

> Also, there is no binfmt-464c module, this message means you're trying to
run a binary that's been compiled for wrong system architecture, ie. i386
instead of the ARM processor that's in iPAQ. 

So what I understand is that your system can't handle both a 32-bit and 64-bit system on one hard disk.   If that is incorrect, could someone please correct me.

---

### Post by madmetal on 2007-02-07
well i will try the solution the post suggests and i hope it works.
how can this problem have been caused by feisty installation?

---

### Post by madmetal on 2007-02-07
> **Sef said:**
> From [ussg.ui.edu]("http://www.ussg.iu.edu/hypermail/linux/kernel/0102.3/0006.html").

A part of it:  

From [handhelds.org]("http://www.handhelds.org/hypermail/familiar/45/4572.html"):



So what I understand is that your system can't handle both a 32-bit and 64-bit system on one hard disk.   If that is incorrect, could someone please correct me.

well i also guess that the problem is 32/64bit one..
but i have two hard disks , one for 32bit and the other for 64bit.
another thing is the master/slave thing.
32bit is slave to 64bit master..
well any suggestions for help..

---

### Post by Sef on 2007-02-07
You can't mix 32 and 64-bit systems on one disk or maybe even on one computer.

---

### Post by madmetal on 2007-02-07
> **Sef said:**
> You can't mix 32 and 64-bit systems on one disk or maybe even on one computer.

well a thing to remember.. :( 
i am now taking /home back up and going to reinstall the 32bit only.

---

### Post by madmetal on 2007-02-11
well after making aaaall type of combinations i think that the problem is caused by feisty and master/slave drives.
i can have edgy on master and dapper on slave , dapper to both , edgy on slave and dapper on master , but if i install feisty (and i tried x86 also) at one then i cannot enter the other due to grub error..

---

