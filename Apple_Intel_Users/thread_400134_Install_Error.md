---
title: "Install Error"
date: 2007-04-03
forum: Apple Intel Users
---

### Post by Wee_Guy on 2007-04-03
I tried to install Ubuntu, and the majority of the install went fine, but, near the end it displayed an error message whitch read:```
We're sorry; the installer crashed. Please file a new bug report at https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 166, in ?
    main()
  File "/usr/bin/ubiquity", line 161, in main
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 57, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 856, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 628, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1404, in ?
    install.run()
  File "/usr/share/ubiquity/install.py", line 385, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1163, in configure_bootloader
    raise InstallStepError(
InstallStepError: GrubInstaller failed with code 1

```What am i supposed to do (other that report the error) to stop it from doing that again?!?!?
I am getting increasingly annoyed by all the problems that are getting in my way, all i want to do is install Ubuntu on a partition of my external hard drive and use it to dual-boot my iMac!This is the 3rd problem, 1st came no sound on the Live CD, then i had trouble with the partitioner, now i can't even get the installer to run without it shoving a lovely huge error message in my face.

---

### Post by oskarloko on 2007-04-03
Are you on Feisty on Edgy ?

See wini here [https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

Please tell us...
- have you installed rEFIt ?

It's caused by GRUB trying to install onto a MBR that doesn't exists...
You must 
a) see if everithing else is installed (as is near the end I suspect that yes, only look to your partition to ensure this )
b) reinstall GRUB to your external HDD linux partition

---

### Post by Wee_Guy on 2007-04-03
How do i install GRUB? What is rEFIt? (no i don't have rEFIt installed as i don't know what it is.)

Everything else (that the installer installs before GRUB) is still there

---

### Post by oskarloko on 2007-04-03
From here
> 
rEFIt is a boot menu and maintenance toolkit for EFI-based machines like the Intel Macs. You can use it to boot multiple operating systems easily, including triple-boot setups with Boot Camp. It also provides an easy way to enter and explore the EFI pre-boot environment. 

[http://refit.sourceforge.net/]("http://refit.sourceforge.net/")

Install rEFIt on MacOsX. It's a generic bootloader for Intel Macs, as they dont use MBR... it uses EFI

See on Wikipedia and seek instructions on ubuntu wiki.

[http://en.wikipedia.org/wiki/Extensible_Firmware_Interface]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface")

[https://help.ubuntu.com/community/MacBook]("https://help.ubuntu.com/community/MacBook")

Good hunting ! ! !




And let's us know.

---

### Post by ronocdh on 2007-04-03
Well... OP Wee is trying to install to an external drive on an iMac, so I don't really think the Macbook guide is particularly well suited to this situation. rEFIt may still do you well, but the GRUB/LILO issue is still going to be a bitch.

Just occurred to me that perhaps Oskar was pointing you to the GRUB kludge in the Macbook guide... I triple boot my MBP and that's what I used! Not sure of the practicality for use on an external, though... =/

---

### Post by oskarloko on 2007-04-04
Well, here it's

[https://wiki.ubuntu.com/iMacIntel?highlight=%28iMac%29](https://wiki.ubuntu.com/iMacIntel?highlight=%28iMac%29)

that sends you to MacBook wiki...

What I've noticed is that 2 problems are causing boot failture:

1- A bootloader-chooser, say as a bootloader that helps you choosing the OS you want to boot
On IntelMacs, the EFI bootloader automaticaly boots onto MacOsX, there's no option avalible
For this, rEFIt will suit extreme well, as it can detects others OS, even on an external HDD ( or on a CDROM )

When the external HDD is plugged, it will let you choose Ubuntu or MacOsX ( and xp if you've it)

2- Making the linux partition enable to boot the Ubuntu system itselft. For this, GRUB must be installed onto the linux partition (with kernel and options you desire ) NOT on the primary hard disk ( the laptop hdd )

Here talks about breezy on a external HD of a classic-Pc... but may help

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)



Ok, please try and tell us... 

\\:D/

---

### Post by Wee_Guy on 2007-04-05
I don't think that i need a boot-disk chooser, as i can choose by holding down [alt]/[option] at startup, and i will be booting into Mac OS X most of the time, so i don't want this to pop-up every time i boot.

Where can i get GRUB(apart from cafè's and resteraunts and other food-places)? and how do i install it?

---

### Post by Wee_Guy on 2007-04-05
I have found GRUB (i'm going to eat dinner soon), but i don't know how to install it(it would be hady if you just ate it;)).

---

### Post by Wee_Guy on 2007-04-06
Does anybody know how to install GRUB?

---

### Post by danb35 on 2007-04-06
Here's how I did it (from memory, hope I'm not missing any steps):
[LIST=1]
[*]Use BootCamp to make a "Windows" partition
[*]Install rEFIt onto the hard drive
[*]Boot from the LiveCD, install Ubuntu into the space occupied by the "windows" partition
[*]Reboot, use the rEFIt partition tool to sync the GPT and MBR partition records
[*]Reboot from the LiveCD
[*]Open a terminal window
[/LIST]

You'll then run the following commands to get in to your mostly-installed system (assuming your root partition is on /dev/sda3 like mine was):

```
$ sudo mkdir /mnt/root
$ sudo mount -t ext3 /dev/sda3 /mnt/root
$ sudo mount -t proc none /mnt/root/proc
$ sudo mount -o bind /dev /mnt/root/dev
$ sudo chroot /mnt/root /bin/bash

```

At this point, you'll be logged in as root on your newly-installed system.  Now, run
```
# grub
grub> find /boot/grub/stage1
```

Grub should return the partition (in GRUB notation) where it found the file.  For me, it returned (hd0,2).  Then, do
```
grub> root (hd0,2)
grub> setup (hd0,2)
grub> quit
```

Finally, you'll need to create the menu.lst file Grub uses to create the menu.  There's a script to do this called, I think, update-grub.  Run
```
# update-grub
```

Once that completes, you should be able to reboot.  The rEFIt menu will let you boot Linux, which will take you into the GRUB menu, and the boot your new Ubuntu system.

---

### Post by Wee_Guy on 2007-04-07
Thanks, danb35. I have encountered a couple of problems when trying to follow your instructions:
1)The rEFIt installer tells me that it will only work on Intel Macs, despite my Mac being a _Intel_ Core Duo iMac!
2)When i batter ahead anyway (running rEFIt off a CD), when i get to here:> At this point, you'll be logged in as root on your newly-installed system.  Now, run
          ```
# grub
grub> find /boot/grub/stage1
```It tells me that it is guessing something about BIOS drivers and it doesn't do anything(i know that it says that it will take a while, but i left it running for about a hour and it was still the same).

By the way, the partion wasn't created by B.Camp, it was created by Disk Utility, will that make a difference?

---

### Post by cyberdork33 on 2007-04-09
If you know what partition is your linux root partition then you don't need that command. (It is probably (hd0,2) as well if you only have OSX and Ubuntu on the main hard drive.)

---

### Post by Wee_Guy on 2007-04-09
No, Ubuntu is on my external HD, with OS X on my internal HD.

How do i find out what my root Ubuntu partition is?

---

### Post by cyberdork33 on 2007-04-09
Well in that case I am going to *guess* that it is (hd1,0). (If your ubuntu root in the first partition)

Do this:
```
sudo fdisk -l
```

and it will list your partitions.

If you do not know how Grub's partition syntax works, It starts counting partitions at 0.
So: 
(hd0,0) = /dev/sda1
(hd0,1) = /dev/sda2
(hd1,0) = /dev/sdb1 (NOTE: Your second hard drive might not be sdb. Grub does not count your Optical drive.)

---

### Post by oskarloko on 2007-04-10
Wellcome to EFI BIOS mess !!

As I think, it's becuase GRUB can link properly with video hardware on EFI BIOS. GRUB is prepared for classical tipical-PC BIOS.

GRUB2 / PUPA
[http://www.gnu.org/software/grub/grub-2-faq.en.html](http://www.gnu.org/software/grub/grub-2-faq.en.html)

and ELILO
[http://elilo.sourceforge.net/cgi-bin/blosxom](http://elilo.sourceforge.net/cgi-bin/blosxom)

are suposed to be compatible with EFI, but there aren't stable yet ( I think )

There's no easy answer, I'm afraid....

---

### Post by cyberdork33 on 2007-04-10
As long as your tables are in sync it doesn't matter.

---

### Post by Wee_Guy on 2007-05-26
Well, i think that i'm going to try installing Boot Camp,then installing Ubuntu from there, trouble is, BC isn't going to let me partition and install on my external HD, it only lets me do so on my smaller internal one. :(

---

