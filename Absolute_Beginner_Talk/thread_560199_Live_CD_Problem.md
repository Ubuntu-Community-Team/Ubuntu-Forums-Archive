---
title: "Live CD Problem"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by jon_1690 on 2007-09-26
I want to try out Ubuntu off of a live CD but I get this error when I attempt to boot:

BusyBox v1.1.3(Debian1:1.3-3ubuntu30) Built-in shell (ash)

/bin/sh: Can't access tty; job control turned off

(initramfs)

:confused:

Any help will be appreciated. Thanks.

---

### Post by weedeatr on 2007-09-26
what is the specs of ur pc or laptop?

---

### Post by overdrank on 2007-09-26
> **jon_1690 said:**
> I want to try out Ubuntu off of a live CD but I get this error when I attempt to boot:

BusyBox v1.1.3(Debian1:1.3-3ubuntu30) Built-in shell (ash)

/bin/sh: Can't access tty; job control turned off

(initramfs)

:confused:

Any help will be appreciated. Thanks.

Hi and welcome, could you give us some specs on the system?

---

### Post by overdrank on 2007-09-26
> **jon_1690 said:**
> I want to try out Ubuntu off of a live CD but I get this error when I attempt to boot:

BusyBox v1.1.3(Debian1:1.3-3ubuntu30) Built-in shell (ash)

/bin/sh: Can't access tty; job control turned off

(initramfs)

:confused:

Any help will be appreciated. Thanks.


Hi you can try this, when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add **break=top** then press enter. When you receive the error again at the prompt type **modprobe piix** and  then enter and then type **exit** then enter again this should continue the livecd to boot.

---

### Post by jon_1690 on 2007-09-27
Thanks. I'll try that. 

Here  are the specifications to my desktop, guys:

HP Pavilion 7840
Intel Celeron processor 
764MHz, 384 MB of RAM.
30GB Hard Drive

I'm running Windows XP Home Edition
Version 2002
SP2

---

### Post by jon_1690 on 2007-09-27
Awesome! Dual-boot is functioning nicely. Thanks a lot for your help! Very much obliged!

---

