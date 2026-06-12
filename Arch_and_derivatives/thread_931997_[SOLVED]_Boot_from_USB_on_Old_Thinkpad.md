---
title: "[SOLVED] Boot from USB on Old Thinkpad"
date: 2008-09-27
forum: Arch and derivatives
---

### Post by semitone36 on 2008-09-27
Hey all

Im trying to install Arch on an old OLD thinkpad (from 2000) from a USB stick.  The problem is that booting from a USB or external hard drive arent options under its BIOS.  How can I configure the boot sequence so that it will boot from the stick?

---

### Post by Sef on 2008-09-27
moved to arch fourm.

---

### Post by mips on 2008-09-28
> **semitone36 said:**
> Hey all

Im trying to install Arch on an old OLD thinkpad (from 2000) from a USB stick.  The problem is that booting from a USB or external hard drive arent options under its BIOS.  How can I configure the boot sequence so that it will boot from the stick?

If the BIOS does not support it then I don't think it is possible to simply boot of a usb stick. Does the laptop have a floppy/stiffy drive? You might be able to load usb drivers that way and then access the usb stick.

---

### Post by K.Mandla on 2008-09-28
I think Slax used to have a boot CD that would poll the USB ports and boot from them, if told. I don't recall ever getting it to work though. ...

---

### Post by mips on 2008-09-28
> **K.Mandla said:**
> I think Slax used to have a boot CD that would poll the USB ports and boot from them, if told. I don't recall ever getting it to work though. ...


His cd-rom does not work.

---

### Post by semitone36 on 2008-09-28
> **mips said:**
> His cd-rom does not work.

Haha youve been in my other threads.  Ill explain better.  I have 2 laptops.  One, an ASUS FT3, runs Ubuntu and is my main comp.  However there is something wrong with the laser in the CD drive so that it cant read or burn DVDs.  Since both the core and the ftp Arch .isos are over 80 MB they are too big to burn to a CD and my ASUS cant work with DVDs at the moment.  So my only other option (short of using the desktops at the library) is to use a stick

My other laptop, a Thinkpad from 2000, runs Windows ME and I would rather have Arch on it.  It doesnt have a floppy drive unfortunately. I was hoping that someone might know how to manipulate the BIOS  menu but if not that is alright Ill just grab some DVD-Rs and head to the library lol.

---

### Post by mips on 2008-09-28
> **semitone36 said:**
> However there is something wrong with the laser in the CD drive so that it cant read or burn DVDs.  Since both the core and the ftp Arch .isos are over 80 MB they are too big to burn to a CD and my ASUS cant work with DVDs at the moment.  

I'm not following this. Can you burn normal CDRs? If 'yes' then the arch .iso will fit on a normal cdr as they are both smaller than 700MB. No need for DVDs.

---

### Post by semitone36 on 2008-09-29
Wow. You know I never cease to amaze myself.  Sorry everybody I read the disk wrong without thinking. (80 MINUTES not 80MB *slams head on desk*)

Well ASIDE from that does anybody want to give a go at the original question in case somebody else has a similar problem?

P.S. Thanks mips lol....](*,)

---

### Post by mips on 2008-09-30
If the BIOS does not support USB booting then it will not work. If you have a floppy drive it might be possible to boot of a floppy and load USB drivers that way so you can access the usb stick. I have never tried this and do not know if it wil work. This was the method used in the old days with cd-roms that were not bootable.

Another option is to install Arch directly off a hard drive partition.

[http://wiki.archlinux.org/index.php/Install_from_USB_stick](http://wiki.archlinux.org/index.php/Install_from_USB_stick)
[http://wiki.archlinux.org/index.php/Hard_Disk_Installation](http://wiki.archlinux.org/index.php/Hard_Disk_Installation)

---

### Post by semitone36 on 2008-09-30
Thanks for the links.  I also found through some of my other threads that UNetbootin [http://lubi.sourceforge.net/unetbootin.html]("http://lubi.sourceforge.net/unetbootin.html") helps with installation from the HDD.

---

### Post by C.S.Cameron on 2008-09-30
Yes it is easy to boot a Flash drive from CD.
See 
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
I've tried it, it works great.
CD ends up with about 7 megs of data on it.

---

### Post by mips on 2008-09-30
If the BIOS supports it you could also do PXE booting over the LAN card.
[http://en.wikipedia.org/wiki/Preboot_Execution_Environment](http://en.wikipedia.org/wiki/Preboot_Execution_Environment)
[http://www.kegel.com/linux/pxe.html](http://www.kegel.com/linux/pxe.html)

---

