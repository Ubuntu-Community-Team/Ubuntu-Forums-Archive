---
title: "Accidental Deletion of Menu.lst"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by snapcase16 on 2007-07-16
As the title indicates, I have accidentally deleted my /boot/grub/menu.lst file. When I boot my computer, I'm met with a Grub prompt. I'm currently using an Ubuntu 6.06 live cd to access the affected computer. In my attempt to fix Grub, I've followed this guide: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351). I followed the guide both with and without chrooting. It appears to work, but when I reboot the computer I am met with the same prompt. Does anyone have any idea how to remedy this? Thanks in advance!

---

### Post by tcoffeep on 2007-07-16
In terminal, does the command :

```
sudo update-grub
```

work?

---

### Post by snapcase16 on 2007-07-16
Unfortunately, it does not. This is what I receive back:

```
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ...
No GRUB directory found.
 To create a template run 'mkdir /boot/grub' first.
 To install grub, install it manually or try the 'grub-install' command.
 ### Warning, grub-install is used to change your MBR. ###

```

---

### Post by tcoffeep on 2007-07-16
Did you try doing the grub-install or mkdir /boot/grub?

---

### Post by snapcase16 on 2007-07-16
I tried both grub-install and mkdir /boot/grub. When I did mkdir /boot/grub, this is what I received: 
```

ubuntu@ubuntu:~$ sudo mkdir /boot/grub
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ...

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

I thought that the problem was solved at that point so I rebooted the computer and I was faced with the same Grub prompt. When I run grub-install:
```

ubuntu@ubuntu:~$ sudo grub-install
install_device not specified.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

```

I'm not sure what it is I need to specify.

---

### Post by tcoffeep on 2007-07-16
What if you try that tutorial...

Because so far it seems like you didn't have a directory *shrugs*

I've had the same problem when I installed Debian overtop of Ubuntu, and when I deleted Debian, Ubuntu wouldn't boot. So I had to do a complete reinstallation. :P

I'm used to it though. I play with the inner-workings, so I reinstall religiously :D

---

### Post by snapcase16 on 2007-07-16
Thanks for the advice; I'll see what I can figure out. I have a bad habit of forgetting to back up important files and folders before I start playing with them. That's what precipitated this fiasco.

---

### Post by tcoffeep on 2007-07-16
You know how to make back-ups right?

---

### Post by avik on 2007-07-16
I don't know if this will help, but have you tried [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")?

---

