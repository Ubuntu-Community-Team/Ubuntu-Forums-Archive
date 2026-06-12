---
title: "How do I make a boot floppy to install xbuntu?"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by pjewett on 2006-10-15
I have an older Toshiba Portege that can't boot from a CDROM. How can I make a bootable floppy so I can install xbuntu? If it's not possible to do so does anyone know any other small distro's that will run on 64megs RAM?

Thanks in advance.

---

### Post by bodhi.zazen on 2006-10-15
See here: [Boot from floppy](https://help.ubuntu.com/community/SmartBootManagerHowto)

---

### Post by pjewett on 2006-10-15
I've done that and successfully booted from floppy into the Smart Boot Manager's menu but it's not showing my cdrom which is visible when I boot into Windows.

Have I done something incorrectly?

---

### Post by bodhi.zazen on 2006-10-15
The only other intial thought i have is to update your BIOS...

You can also try this:  [Install without a CD](http://ubuntuforums.org/showthread.php?t=28948)

---

### Post by pjewett on 2006-10-15
Thanks anyway for the help. I'm a newbie and that linked option looks a bit over me. I really just want to get a distro installed so I can start learning but haven't been able to find one that I can get to install.

I'll look elsewhere.

Thanks again.

---

### Post by bodhi.zazen on 2006-10-15
Try qemu or DSL.

quem: [QEMU](http://www.h7.dion.ne.jp/~qemu-win/)

DSL: [DSL](http://www.damnsmalllinux.org/download.html)

Windows version[](ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/)
Download Directory: dsl-embedded.zip
[or Click here](ftp://ibiblio.org/pub/Linux/distributions/damnsmall/current/dsl-embedded.zip)

Note DSL will run WITHIN WINDOWS, uses qemu, and is very easy.

---

### Post by pjewett on 2006-10-15
I tried DSL...figure that one was my best hope. I'm able to boot from the floppy I created but get the following messages:

You passed an undefined mode number.
Press return to see video modes available. SPACE to continue

When I hit continue I see the Welcome To DSL message and then get:

Can't find KNOPPIX filesystem, sorry.
Dropping you to a (Very limited) shell.
PRess reset button to quit.

---

### Post by bodhi.zazen on 2006-10-15
> **pjewett said:**
> I tried DSL...figure that one was my best hope. I'm able to boot from the floppy I created but get the following messages:

You passed an undefined mode number.
Press return to see video modes available. SPACE to continue

When I hit continue I see the Welcome To DSL message and then get:

Can't find KNOPPIX filesystem, sorry.
Dropping you to a (Very limited) shell.
PRess reset button to quit.

I would advise you run DSL-embedded. It runs within windows, no need to boot to DSL (from floppy).

---

