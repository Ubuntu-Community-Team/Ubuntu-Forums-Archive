---
title: "Commands and Directories"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-04-25
just put this here to answer some questions about the directories and standard commands that are used in Ubuntu.. maybe should deserve a sticky

bin - tools necessary to get the system up and running, and used when repairing system and diagnosing problems

boot - boot loader and config files

cdrom /media/cdrom - symbolic link to cdrom drive

dev - virtual files representing hardware cdrom. hdd's etc

etc - central repository of config files

home - personal directories

initrd.img - symbolic link to ramdisc (used to boot)

lib - shared system files and software

lost + found - (pretty much describes itself, lost files)

media - your mounted hard-drives and cdrom's

mnt - temporary mounting area

opt - optional software

proc - contains data about your system and its status

root - root user directory

sbin - administration programs

srv - network config files

sys - mount point of sysfs (used by kernel to control hardware)

tmp - temporary files

usr -  shared network data

var - used to store data that is constantly updated

Vmlinuz.img - symbolic link to kernel file

Commands:

cp - copy file
mv - move file
mv - rename file mv (old name) (new name)
rm - remove file
mkdir - create directory
rm -rf   - remove directory
cd - change directory
vi - edit text file
less - view text file
lpr - print text file
diff - compare files
find - find files
fsck - check filesystem
ifconfig - view network settings
clear - clear screen

---

### Post by mjm115 on 2006-04-25
> ipconfig - view network settings

This should be ifconfig.

I agree though, this will help beginners.  When I first come to Linux, I had no idea what this stuff meant.

---

### Post by joshrobinson on 2006-04-25
[QUOTE=mjm115]This should be ifconfig.

I agree though, this will help beginners.  When I first come to Linux, I had no idea what this stuff meant.[/QUOTE]

thanks i fixed it

---

