---
title: "Hard drive partitioning"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by Carnage21 on 2006-10-02
I currenty have Ubuntu 6.06 on my computer. Recently, I installed windows on my hard drive. However, it now automatically sends me to windows instead of giving me a prompt to change OS's. I have included a linux swap partition but it doesnt give the option to boot linux. Please tell me how to fix this.

---

### Post by PPAAUULL on 2006-10-02
The Problem is that Windows likes to pretend that it is the only operating system on the computer. I would guess that you have to either reinstall Grub or reinstall Ubuntu.

---

### Post by jd65pl on 2006-10-02
You should check this page out on the wiki for repairing grub after an install of windows

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

J

---

### Post by Mr Frosti on 2006-10-02
Windows is best installed first because it will automatically replace the bootloader on the hard drive with its own bootloader (and not make entries for any other operating system). The best thing to do is reinstall Ubuntu, or if you are an expert, reinstall the GRUB bootloader on your Ubuntu partition.

---

### Post by fatsheep on 2006-10-02
First go into synaptic package manager and make sure "grub" is installed.  If it isn't, install it now.  If that doesn't fix the problem then please post the output of this command:

> cat /etc/fstab

---

### Post by PPAAUULL on 2006-10-02
Just a question, but doesn't the Vista bootloader allow Other OS's an entry on it?

---

### Post by imaginos on 2006-10-02
Windows installation replaced your previous MBR content which loaded GRUB, with it's own MBR content that calls ntldr (windows loader). One possible solution is to chainload GRUB from ntldr, like this.

Boot from live Ubuntu CD, then copy boot sector of a Ubuntu partition to a file (446 bytes long). It could be done like this:
```
dd if=/dev/hdaX bs=446 count=1 of=lin_boot.bin
```
X=number of your linux partition.

Then copy that little file on windows partition C:\ (via floppy disk, since windows ntfs partitions are not writeable by default) and add a line in the file c:\boot.ini, like this:
```
c:\lin_boot.bin="Ubuntu"
```

lin_boot.bin is that 446 bytes file made from boot sector of Ubuntu partition.


More informations could be found here:
[http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd](http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd)

---

