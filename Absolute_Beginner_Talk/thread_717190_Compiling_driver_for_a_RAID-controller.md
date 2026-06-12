---
title: "Compiling driver for a RAID-controller"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by C.D on 2008-03-06
Hello, penguins!

I'm a totally new to the linux concept. I've installed the desktop version - which by the way was a surprisingly smooth procedure!
I've played around with basic commands, and installed a couple of apps through the Package Manager.

The main reason why I'm using linux, is because windows won't let me access my RAID5 array - giving me a bluescreen of death for no reason. Having tested my hardware, googled and camped on forums like a madman - I am now facing my last potential solution ..

I've downloaded some files from highPoint (got a RocketRaid 2320, btw) from HPT's website [here]("http://www.highpoint-tech.com/USA/bios_rr3320.htm").
I grabbed the "open source" one, since I'm clueless.
next, I did the following:
```

clas@Ubuntu:/media/sdb1/SCSI/product/rr232x/linux$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /media/sdb1/SCSI/product/rr232x/linux/.build/os_linux.o
  CC [M]  /media/sdb1/SCSI/product/rr232x/linux/.build/osm_linux.o
  CC [M]  /media/sdb1/SCSI/product/rr232x/linux/.build/div64.o
  CC [M]  /media/sdb1/SCSI/product/rr232x/linux/.build/hptinfo.o
  CC [M]  /media/sdb1/SCSI/product/rr232x/linux/.build/config.o
  LD [M]  /media/sdb1/SCSI/product/rr232x/linux/.build/rr232x.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /media/sdb1/SCSI/product/rr232x/linux/.build/.him_rr232x.o.cmd for /media/sdb1/SCSI/product/rr232x/linux/.build/him_rr232x.o
  LD [M]  /media/sdb1/SCSI/product/rr232x/linux/.build/rr232x.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
clas@Ubuntu:/media/sdb1/SCSI/product/rr232x/linux$ 

```
Basically changing the directory to where the makefile is, and running the 'make' command - exactly what it says in the radme file.

I've searched the forum and googled alot, trying to find a guide or some solid material describing how to compile a driver. Either it's too advanced, or it's not matching my case.

Hardware seems to be a great issue in linux. I must say, Linux is incredibly smooth! I've used windows all my life, but a few hours on linux has changed so much! I'm just hoping that there is a way to get my hardware to work properly.

Any help will be greatly appriciated! :smile:

---

### Post by C.D on 2008-03-06
delete

---

### Post by C.D on 2008-03-07
Okay, so luckily for me, someone else has tried and succeeded in getting the RocketRaid 2320 to work.
I followed his steps in **[this](http://ubuntuforums.org/showthread.php?t=311723&highlight=RocketRaid+2320)** thread. AFter going through the whole thing, I still got the same warning when doing 'make' - however, 'make install' worked, and since I got no errors, I rebooted.

Now I get the *Error 15: File not found* when I boot up, so I can't boot Ubuntu. I've googled, and the suggestons I've got so far, is that disks have changed position. How do I fix this, is it bad? What did I do wrong here?

---

