---
title: "so, GRUB made my laptop no longer boot"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by dibdib on 2007-09-17
GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

Sure, why not?  Some guy out there has a computer with 145 installed operating systems, and Ubuntu doesn't seem to want to work on mine if I have XP installed.  So can I just kill it now and make my computer work again by booting XP like it used to do?  I think I'm done with Ubuntu.

---

### Post by antoz on 2007-09-17
If you want to go back to your original setup you have to fix your MBR

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by kellemes on 2007-09-17
> **dibdib said:**
> GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

Sure, why not?  Some guy out there has a computer with 145 installed operating systems, and Ubuntu doesn't seem to want to work on mine if I have XP installed.  So can I just kill it now and make my computer work again by booting XP like it used to do?  I think I'm done with Ubuntu.

Yeah, it's all to easy to blame the software..
Before you jump into stuff like this you need to know what you're doing or at least expect crap to happen.

---

### Post by PmDematagoda on 2007-09-17
> kellemes:-

Yeah, it's all to easy to blame the software..

Now don't we all do that?:)

> kellemes:-
Before you jump into stuff like this you need to know what you're doing or at least expect crap to happen.

Agree with you there, you got to expect the unexpected in almost anything, with XP though you can expect it to not to work, while not expecting it solve your problems.:-D

Seriously though, it's never very easy to switch from one OS to another, it takes time and patience, so it may take some time to properly configure Ubuntu but the end result will be worth it.

---

### Post by sporry on 2007-09-17
> **dibdib said:**
> GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

If you haven't done so already, try searching for that error in the Ubuntu search function. You may find something that will help you.

---

### Post by slira on 2007-09-17
> **dibdib said:**
> GRUB Loading stage1.5

GRUB loading, please wait...
Error 17

Sure, why not?  Some guy out there has a computer with 145 installed operating systems, and Ubuntu doesn't seem to want to work on mine if I have XP installed.  So can I just kill it now and make my computer work again by booting XP like it used to do?  I think I'm done with Ubuntu.

Hi
no... if you just format the linux partition, your machine will not boot ](*,)  , because grub changed your MBR and windows is no longer able to boot alone; explanation: grub changes the mbr redirecting to itself (located anywhere in the same hdd or another); then grub manages the boot decisions. This is necessary for dual (or "pluri") boot in machines where windows was installed alone - windows does not assume that other OS might be installed....

you have 2 options:

a) fix MBR using W CD or setup (I never did it...) and give up linux :(

b) install ubuntu (and grub) as it should (then edit menu.lst and you can decide the default boot, time-out, order of OS, etc.) - this is the solution I have used for a couple of times during first ubuntu experiences. Do not give up... you will see that ubuntu is a fine OS :)

(another possible solution: try super grub) :confused:? search in google - first 3 results!=D>

Hope it works
slira

---

### Post by philipho on 2007-09-17
I dont know what you did to GRUB but if your MBR is pointing to the wrong partitions, you computer will not boot. For red hat linux it is rather easy to fix this problem, just boot into rescue mode using the cd and reinstall GRUB. The procedure should be the same for Ubuntu. If you want to know the detailed procedure, pm me. 

But the MBR takes up 512 bytes. If the information from the first 440+ bytes is corrupted, you can just reinstall GRUB. However, the remaining space contain important information on the locations of disk partitions. If this area is corrupted, reparing the MBR wont be easy.

---

### Post by raul_ on 2007-09-17
[http://www.uruk.org/orig-grub/errors.html]("http://www.uruk.org/orig-grub/errors.html")

Super Grub Disk is worth having

---

### Post by dibdib on 2007-09-17
Well I blame the software only for the fact that all I did was install the OS off the disc then reboot.  Call me crazy, but when you install a fresh OS I kind of sort of just a little in the ever-so-slightest expect for it to be able to boot afterward.  It's never happened to me before installing XP anyway.  In fact I did so just the other night and it booted fine.

Anyway yes, I was searching around on Google for terms like ubuntu+grub+error 17 and so forth but despite lots of problems wasn't turning up much in the way of solutions.  In any case, while just bored I restarted my system a few times and on the latest one it started.  So I'm going to think long and hard about whether to delete it, because the only thing I possibly hate more than softaware inexplicably breaking is software inexplicably unbreaking.  Things shouldn't be changed by not doing anything to your system, particularly when you were unable to even access your system.

---

### Post by uglykigjoe on 2007-09-17
> **dibdib said:**
>  Call me crazy, but when you install a fresh OS I kind of sort of just a little in the ever-so-slightest expect for it to be able to boot afterward.  

Boy.. thats the case of fresh install.
Dual-boot is a different story. Btw have you really tried Supergrub Disk?

---

### Post by aJayRoo on 2007-09-17
It may be worth noting that I get an GRUB error 17 when I attempt to boot my machine with an external hard drive or iPod plugged in. Try booting without usb storage devices (pen drives, external HDs, iPod etc.) plugged in and see if you can determine whether or not the error is down to this.

---

