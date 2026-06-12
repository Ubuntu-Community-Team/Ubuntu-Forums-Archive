---
title: "No way to boot from CD or Floppy - help with install?"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by socktan on 2005-10-10
Hi All!

I'm trying to give Unbuntu a go on an older Toshiba 490xcdt laptop, and a have a rather crippling problem for someone completely new to installing any flavor of linux...l

It will not boot from the CD-ROM drive, and it's been that way since I bought the unit a few years ago...  Oh - and cross out any ability to boot from a floppy... I don't have one.

I tried just dropping the hard drive into my desktop computer, boot from the ubuntu disc, and install there...  Sounds simple enough to work...

The installation went okay - I was up and running on the desktop in an hour or so... once I updated everything and surfed around on the net for a bit, it was time to put the drive back into the laptop.

Alas, ubuntu will not boot...



***** snip *****
Uncompressing Linux. . . Ok, booting the kernel.
PCI: Cannot allocate resource region 4 of device :00:00:05.1
audit(1128938983.197:0): initialized
Starting Ubuntu. . . 
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No suck file
Kernel panic - not syncing: Attempted to kill init!
**** end *****


So, my question to the community is - can I repair this install

or

Is there a method to installing without booting from the install CD?



Thanks in advance,

-
Chris.

---

### Post by heimo on 2005-10-10
I think I know what's wrong, but I don't have step-by-step instructions how to fix it.

This:
> pivot_root: No such file or directory
Suggests to me that kernel is trying to mount device that doesn't exist (as a root partition). Basicly, you need to pass kernel a correct root parameter... Using grub command line or grub's configuration file.

... Sorry I'm light on details. Maybe someone else can help you from here. If I'm mistaken (perfectly possible), sorry to mislead you. :) Hopefully you get it solved.

---

### Post by socktan on 2005-10-10
[QUOTE=heimo]
Suggests to me that kernel is trying to mount device that doesn't exist (as a root partition). Basicly, you need to pass kernel a correct root parameter... Using grub command line or grub's configuration file.
[/QUOTE]

Thanks for the suggestion!

Perhaps it's trying to mount the second CD-ROM drive that the desktop has, and the laptop does not...

---

### Post by Efwis on 2005-10-10
The reason that it wouldn't work in your laptop after you put the hdd back in was because ubuntu was installed using the hardware specs of the computer you used to install it.

I ran into a similar problem when my MOBO died on this computer, I had to do a new install since my new MOBO wasn't the same as the original one.

The only reason I am asking this, is because you don't mention trying it. but did you go into your BIOS screen and try making the CD-Rom first boot device??

if not that is how to solve your problem :)

> 
Information from [Linux on the Toshiba Tecra Series](http://www.astro.umd.edu/~teuben/linux/laptop/tecra710.html#bios)

BIOS versions installed on the laptops depend on the laptop model and the date of manufacture. BIOS updates can be downloaded from [Toshiba's support site.](http://www.toshiba.com/tais/csd/support/files/) The most recent BIOS versions available there are shown in the [specifications section](http://www.astro.umd.edu/~teuben/linux/laptop/tecra710.html#spec)
If you need to get into the BIOS setup screens and don't want to boot some Microsoft product just to run TSETUP.EXE, press the Esc key while turning on or resetting your laptop. After the BIOS' system initialization is done, it displays the message "Check system. Press [F1] to continue.". Pressing the F1 key will get you to the BIOS setup screens. Note that local keyboard mappings are not yet in effect.


hope this helps.

---

### Post by socktan on 2005-10-10
[QUOTE=Efwis]
The only reason I am asking this, is because you don't mention trying it. but did you go into your BIOS screen and try making the CD-Rom first boot device??
[/QUOTE]

Yes, I've tried... It's currently configured to boot from CD-ROM->FDD->HDD... even after I pull the HDD out it still refueses to boot from CD-ROM...  it's a very frustrating problem that's caused me grief in the past...  Thanks for the suggestion though! :)

---

### Post by socktan on 2005-10-10
A little update...

I've gone as far as flashing the bios on the laptop in a feeble attempt to enable booting from CD with no success...

In addition to that, I put the drive back into the desktop in which I originally installed ubuntu, and the same error came up with no success booting... 

So... I guess I'm back to square one, and my question is more "How to install without booting from CD-ROM..."

---

### Post by UbuWu on 2005-10-10
Do you have an OS on it right now? windows or linux? can it boot from network?

The following howto's can help in some cases:
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)
[https://wiki.ubuntu.com/Installation/WindowsServerNetboot](https://wiki.ubuntu.com/Installation/WindowsServerNetboot)
[https://wiki.ubuntu.com/Installation/Netboot](https://wiki.ubuntu.com/Installation/Netboot)

---

