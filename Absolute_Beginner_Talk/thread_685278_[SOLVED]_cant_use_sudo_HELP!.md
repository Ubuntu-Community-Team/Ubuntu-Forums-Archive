---
title: "[SOLVED] cant use sudo HELP!"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by brokenhachi on 2008-02-02
ok heres what i was trying to do... 

I was trying to set up hibernate and it tells me in the howto to open visudo and add a line to it.. so i did, but i think i added it wrong. heres what happens when i try to run hibernate

> ~$ sudo hibernate
>>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24


so i tried to go back to visudo to fix the syntax... and...

> ~$ visudo
visudo: /etc/sudoers: Permission denied

~$ sudo visudo
>>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24

~$ sudo -s
>>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24


so i want to fix the syntax error, but i cant get to the file so i cant do anything. how can i get to the sudoers file? as u can see, i couldnt run visudo from my login.. bc i need to be root, so i tried sudo visudo which gives me root priv right? but that didnt work, so i tried to log in as root, but that didnt work either


just for the record, i cant use any sudo command now...


> ~$ sudo apt-get update
>>> sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24


HELP!

---

### Post by dcstar on 2008-02-02
> **brokenhachi said:**
> 
........
just for the record, i cant use any sudo command now...

HELP!

Boot off a Live CD, mount your Ubuntu hard drive partition and manually edit that file - removing the changes you made.

Then do a normal reboot and see if things are better.

---

### Post by brokenhachi on 2008-02-02
ok... is that the only way?

once i boot from the livecd, how do i mount the hdd?

---

### Post by doddo on 2008-02-02
Optionally, booy ur computer into single user mode, it is a bit trickier ´, but here it goes

press ESC when the grub screen appears

then press E to the boot line your booting from

then select the kernel line, press E again

add an argument to the kernel line reading ```
init=/bin/bash
```

then bress return and press b to boot

Instead of using regular boot, with inittab, you will be given a root shell, bash

now remount your partition read/write like this

```
mount -o remount,rw /
```

And then edit the file. I would recommend using visudo to edit the sudoers file.

good luck
:)

---

### Post by doddo on 2008-02-02
> **brokenhachi said:**
> ok... is that the only way?

once i boot from the livecd, how do i mount the hdd?

you open a terminal. then you mount it using

```
mount /dev/sdcX /mnt
```

you have to know which partition to mount, and you have to also know which disk. If you are unsure, just poke around abit, mounting different partitions and disks until you find the right one

Remember to alway umount the disks when done with them

```
umount /mnt
```

This has to be done when you are not preforming any operations on the disks, or when you are inside the disk with your shell

---

### Post by anaconda on 2008-02-02
> **doddo said:**
> Optionally, booy ur computer into single user mode, it is a bit trickier ´, but here it goes

press ESC when the grub screen appears

then press E to the boot line your booting from

then select the kernel line, press E again

add an argument to the kernel line reading ```
init=/bin/bash
```

then bress return and press b to boot

Instead of using regular boot, with inittab, you will be given a root shell, bash

now remount your partition read/write like this

```
mount -o remount,rw /
```

And then edit the file. I would recommend using visudo to edit the sudoers file.

good luck
:)


actually single user mode is the same as "recovery mode", and you should already have recovery mode in your grub boot loader..

Just boot to recovery mode and edit the file with visudo..

---

### Post by nemilar on 2008-02-02
Most likely, the LiveCD will auto-mount your hard drive for you, and put an icon for it on your desktop.

---

### Post by brokenhachi on 2008-02-02
ok i booted in recovery mode and was able to fix it. thanks guys! i appreciate it.



edit: tuxonice still doesnt work though....... anyone know a good, reliable way to get my comp to hibernate?

---

### Post by doddo on 2008-02-02
> **anaconda said:**
> actually single user mode is the same as "recovery mode", and you should already have recovery mode in your grub boot loader..

Just boot to recovery mode and edit the file with visudo..

As I recall it, the recovery option requires administrator password, while single user mode just gives u a bash prompt.

---

### Post by brokenhachi on 2008-02-02
yea i had to put in my administrator pass (my user pass) and then it gave me the command line

---

