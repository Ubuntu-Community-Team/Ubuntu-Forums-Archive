---
title: "Triple boot help"
date: 2008-07-28
forum: Apple Hardware Users
---

### Post by Houli on 2008-07-28
I have a Mac Mini. Leopard is installed and I wanna do a tri-boot. OS X, Windows XP and Ubuntu. Are these the right steps?

Leopard installed.
Use bootcamp to install Windows.
Make partition for Linux.
Install rEFIt and enable it.
Restart with Live CD in.
Boot it up and select install.
Go through the install process normally?
Done?

Anybody wanna help?

---

### Post by cyberdork33 on 2008-07-28
Just follow the install guide in the Macbook Pro wiki. It is the same.
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Personally, since you have Leopard, I would just use Disk Utility to create all your partitions before you do anything else. No need to use the Boot Camp assistant.

You must make sure that the windows and Ubuntu root partitions are in the first 4 otherwise you will have problems.

My suggested partitioning scheme:
1. EFI (Already there)
2. HFS+ / OSX (Already there)
3. ext3 / Ubuntu root partition
4. Windows (FAT32)
5. swap (not really required, but suggested)

Also, during the ubuntu install, you should make sure to install GRUB to the Ubuntu partition instead of the MBR (else windows will otherwrite it. This is selected under the "Advanced" button near the end of the installation.

---

### Post by Houli on 2008-07-28
Cool thanks I just read about that MBR thing. I can´t wait to have it all done.

---

