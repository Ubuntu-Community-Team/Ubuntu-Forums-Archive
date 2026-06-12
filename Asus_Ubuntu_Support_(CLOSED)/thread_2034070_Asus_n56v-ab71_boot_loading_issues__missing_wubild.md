---
title: "Asus n56v-ab71 boot loading issues / missing wubildr.mbr"
date: 2012-07-27
forum: Asus Ubuntu Support (CLOSED)
---

### Post by antihero898 on 2012-07-27
So I just got a brand new laptop, an Asus n56v-ab71 that is running windows 7 home premium 64 bit and I am new to Ubuntu. 
I burned the latest version of Ubuntu as a live cd to a dvd, but am forced to install wubi and then reboot through that.
Of course, I get the error stating I am missing wubildr.mbr, and that it is corrupt. I initially tried to do this as a dual boot with windows, 
but then partitioned my hard drive into two parts, and installing using the windows installer onto another partition.
I still seem to get the same issue. The machine is a UEFI machine, but I am able to disable/ enable UEFI boot from cd.

The thing that makes me mad is that through the bios of this machine, it forces you to create a path and how to boot,
instead of just being able to select the cd drive. I have tried to research for hours, almost two days, and have 
found either nothing or way too much and am at a complete dead end. It would be a great help if anyone could
 help me as I am very interesting in using Ubuntu. All of my friends that are in computer science majors with
 me love it and recommend I go for it.

---

### Post by oldfred on 2012-07-28
Welcome to the forums.

You say you are forced to install wubi? I am not sure wubi works with UEFI Windows as it has to use the Windows boot loader to start. It may work if you manually create the boot files, but I am not sure that is possible with wubi.
I did find this. Do these files exist?
> In C:\ubuntu\winboot you will find a copy of wubildr and wubildr.mbr.
  Copy them to C:\ and restart the system, you may have to use BCDedit first if entry is missing.
 
                

With UEFI you should be able to create a dual UEFI boot. The installer installs in the mode you boot the installer, so if you want UEFI you boot installer in UEFI mode, otherwise boot in BIOS mode.

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

I do not think this works with UEFI wubi.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

