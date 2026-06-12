---
title: "Oldies but Goldies. from win to linux and back"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by ^_^ on 2006-03-27
i've just installed ubuntu (reinstalled cause i've used it before) but i got an error with the grub loader. it said it detected ubuntu as being the only operating system on my box. so i've used lilo instead, and installed in in the MBR. and when i restart my pc it starts linux automatically and i don't see a menu allowing me to choose which os to boot. (as you can pretty tell so far i am a linux newbie)

ahm, can i change the boot loader settings somewhere? can i make it detect my win os? or, do i have to reinstall/repair my old win instalation? yea, i know, window sucks, but i need to backup some important files i have on my C drive before formatting that drive...and i saw that's what xp does when you install(that's normal) or repair(i don't think this is normal anymore) your win installation.

ok. if this can't be done, then, can anyone pls tell me how can i mount my windows drives in ubuntu so i can at least copy those important files in my home dir or any other one(where i have access, f course) and burn those on a cd... 

can anyone help, pls?

---

### Post by emmanuel on 2006-03-27
[QUOTE=^_^]
can anyone help, pls?[/QUOTE]

surprising grub didn't work!?
well yes you should be able to get back your windows in the boot line quite easily.
the file to change is /etc/lilo.conf
you get info about that file with the command: man lilo.conf (IIRC, grub is on my computer).
once you change the lilo.conf file, run "sudo lilo" at the prompt for it to update the boot sector with your changes.

if i remember well, you must tell lilo the partition where to find your windows installation.[COLOR="Silver"]
this depends if it's on the same hard disk or another hard disk than the linux install.

if it's on the same hard disk, it's probably a IDE on the primary master:
/dev/hda

running "sudo cfdisk /dev/hda"
will list you the partitions on that drive, and you can find your windows partition.

if it's on another hard disk, do the cfdisk on the right disk.

hda primary master
hdb primary slave
hdc secondary master
hdd secondary slave

hope it's not too confusing![/COLOR]

(the command suggested by next poster, "sudo fdisk -l" is smarter to find which partition is your windows installation on: use that instead)

---

### Post by akiro.yamamoto on 2006-03-27
Can you please post the output of the following command.
```
sudo fdisk -l
``` It should tell us if you have over written your Windows partition or not and it will
allow us to give better advice by referencing your actual partition configuration.

LILO:
Lilo stores it's configuration settings in /etc/lilo.conf by default. You can read that file for set-up options
and configuration settings.
The following will provide more indepth info about lilo.
```

man lilo
info lilo

```

---

### Post by akiro.yamamoto on 2006-03-27
The command must be entered in the terminal.....
In Gnome
Click on Applications >> Accessories >> Terminal

BTW:
If you have already installed GParted you can use that instead.

---

### Post by ^_^ on 2006-03-27
10x for the replies guys. i will test all what you've said in 3 hours or so. i'm not home right now, and i'll let you in with what happens after i run those commands

10x again

---

### Post by akiro.yamamoto on 2006-03-27
Ubuntu comes installed with a Help System.
Under Gnome use: System >> Help.
It provides a basic guide for typical problems you may encounter.

---

### Post by ^_^ on 2006-03-27
one more question, actually 2...

i've downloaded the latest version of firefox. (i'm using the ubuntu 5.04 | hoary hedgehog release) 

1.how do i update my current version of firefox?

2.i saw that code::blocks(the latest stable release) is only available for ubuntu 5.10...will it also work on 5.04?
cause i will need an c++ ide i can work with. and i think code::blocks is pretty cool. got any other sugestions?

---

### Post by emmanuel on 2006-03-27
[QUOTE=^_^]
i've downloaded the latest version of firefox. (i'm using the ubuntu 5.04 | hoary hedgehog release) 

1.how do i update my current version of firefox?
[/QUOTE]

if you are using 5.04. you can download firefox from getfirefox.com and use the version you downloaded from there. it will work perfectly fine.

if you want to have the firefox from ubuntu to be a newer version then then you'd have to upgrade to ubuntu 5.10, but also 5.10 has firefox 1.0. only ubuntu dapper, the development release, has firefox 1.5.

so your best choice is to download firefox "by hand" and run it as you would in windows and wait for dapper to be released june 1, then think whether it's worth to upgrade to get firefox 1.5 "officially" from ubuntu (probably not worth it if it's just for that reason).

altogether i think it's OK: either firefox 1.0 from ubuntu or download yourself firefox 1.5.

[QUOTE=^_^]
2.i saw that code::blocks(the latest stable release) is only available for ubuntu 5.10...will it also work on 5.04?
cause i will need an c++ ide i can work with. and i think code::blocks is pretty cool. got any other sugestions?[/QUOTE]

no idea if it'll work on 5.04. probably not... it could also run and be unstable in strange ways... upgrading to 5.10 is still an option. kdevelop could be an option, maybe eclipse too. i'm not sure whether eclipse does C++ though.

---

### Post by ^_^ on 2006-03-27
here's the output of the sudo fdisk -l command on the terminal

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        1305    10474380    f  W95 Ext'd (LBA)
/dev/hda2   *        1306        3916    20972857+   7  HPFS/NTFS
/dev/hda3            3917        6527    20972857+   7  HPFS/NTFS
/dev/hda4            6528        9964    27607702+   7  HPFS/NTFS
/dev/hda5               2        1305    10474348+   7  HPFS/NTFS

i installed linux on the D drive and windows is on the C drive

and here's the content of the lilo.conf file

boot=/dev/hda

# Specifies the device that should be mounted as root. (`/')
#
root=/dev/hda2

what should i set these lines to?
please note that win is installed on c, so hda1. if i set other=/dev/hda1 what must i set boot= to then?
# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3

---

### Post by emmanuel on 2006-03-27
[QUOTE=^_^]here's the output of the sudo fdisk -l command on the terminal

what should i set these lines to?
please note that win is installed on c, so hda1. if i set other=/dev/hda1 what must i set boot= to then?
# If you have another OS on this machine to boot, you can uncomment the
# following lines, changing the device name on the `other' line to
# where your other OS' partition is.
#
# other=/dev/hda4
#	label=HURD
#	restricted
#	alias=3[/QUOTE]

i'm surprised there's no "image=" line in your lilo.conf?
otherwise, in my opinion (you might want to wait a bit after my answer, maybe more knowledgable people will answer), uncomment the "other" part, channing hda4 to hda1, also change the label from "HURD" to "dos" (just to make it clearer).
then run ```
sudo lilo
```

then reboot, when lilo comes up press shift: a prompt should appear. when it does, type "dos" inside, and press <enter>. it should boot windows.
if when rebooting you don't press anything it should boot linux.

you can also use 
```
prompt
timeout=5
```
lines in the lilo.conf so you're asked everytime but do that later. i also don't see a "label" line in your lilo.conf so i'm not sure what you would have to type to get linux. anyway after "timeout" you'd get linux though.
see
[http://www.die.net/doc/linux/man/man5/lilo.conf.5.html](http://www.die.net/doc/linux/man/man5/lilo.conf.5.html)
[http://www.redhat.com/support/resources/faqs/rhl_general_faq/s1-bootloader.html](http://www.redhat.com/support/resources/faqs/rhl_general_faq/s1-bootloader.html)

---

### Post by ^_^ on 2006-03-27
well, there is an image field in the lilo.conf file

here's the entire content of the file...
boot=/dev/hda
root=/dev/hda2
map=/boot/map
delay=20
vga=normal
default=Linux

image=/vmlinuz
        label=Linux
        read-only
        initrd=/initrd.img

image=/vmlinuz.old
        label=LinuxOLD
        read-only
        optional
        initrd=/initrd.img.old

---

### Post by ^_^ on 2006-03-27
great

i can't change the contents of lilo.conf because i don't have permissions

what is the default username and pass for ubuntu? cause i haven't specified one when i installed it and i see that the owner of lilo.conf is root, so i'm assuming admin name is root, but i don't know the password...is there a default value for it?

---

### Post by icyisamu on 2006-03-27
add a 'sudo' infront of the command you are using.

eg. to edit a file

```
sudo gedit something
```

You will then be prompted to enter a password. If you are the only user and created this account when you installed ubuntu, just type in your current password.

---

