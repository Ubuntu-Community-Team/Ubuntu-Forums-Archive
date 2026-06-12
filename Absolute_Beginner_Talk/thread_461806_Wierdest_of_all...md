---
title: "Wierdest of all.."
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by flaZh on 2007-06-02
Hi.

I'm new to Ubuntu, I have used RedHat, Gentoo before, and I'm a moderate user.

I've tried to install Ubuntu several times now, first time I got pretty far, but all of a sudden, after turning my back to the comp for a short time, my machine was off! I WTFed and grub failed on reboot(lilo didn't get set up properly), so I thought ow well, I'll just install again. And now it shuts down randomly(anywhere from when I press install(first option and a few minutes into the install)), and I don't get far. It recieves the shutdown command all of a sudden on clear screen, and it simply shuts down.. Can anyone explain why?

Help appreciated.

-flaZh

---

### Post by wormser on 2007-06-02
We need more information to help you.  What are the specs of your computer and is there an error message?

---

### Post by flaZh on 2007-06-02
It's a laptop. Anything in spesific u need to know? 2GHz, 2gb ram, nVidia 6600 Go. No error messages, no.

---

### Post by happy-and-lost on 2007-06-02
Try running the live cd with the option *acpi=off*

---

### Post by flaZh on 2007-06-02
Thanks, the install went well now.

But when booting up, there's some critical errors that makes the laptop shut down. And it is all about my ACPI Critical Point something, and it shuts down. How to turn it off, recoverymode kernel did not work, and the normal one get errors when trying to get X up at first, and then shuts down, prolly when it comes to the ACPI.

Also some errors about read-only file system.

Need further assistance.

---

### Post by happy-and-lost on 2007-06-03
You need to permanently add *acpi=off* to the kernel line.

To boot into your system in order to do so, press e on your default ubuntu entry on the grub menu, edit the kernel line to include acpi=off.

This will hopefully enable your system to boot, from where you can open a terminal, type *sudo gedit /boot/grub/menu.lst* then scroll down to where it says *# defoptions=quiet splash* and alter it to say *# defoptions=quiet splash acpi=off*

Then run in the Terminal *sudo update-grub*

And you should be done.

---

### Post by Maconvert on 2008-04-11
So, what was the result?
Did you get your computer to stop randomly shutting off?

That's what mine is doing and I'm even more sure now that this is an Ubuntu problem.

---

### Post by Maconvert on 2008-04-14
Hello,

Well, it looks like this fixed it. My computer has been running just fine for 24 hours (it usually died within anywhere from 30 minutes to 8 hours). I'll keep an eye on it and let everyone know how I make out.

Cheers.

---

### Post by bubba_169 on 2008-04-14
Is your fan working. Critical point could mean the temperature before your laptop burns...

---

### Post by Maconvert on 2008-04-14
My fans are working (they are always running at approximately 2700 rpm).

My temperature sensors ssem to be working as well, with the CPU temperature usually somewhere between 30'C and 35'C and the MB temperature usually about 29'C.

Cheers.

---

