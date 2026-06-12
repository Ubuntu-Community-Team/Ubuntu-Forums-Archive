---
title: "Run off USB drive"
date: 2008-03-31
forum: Apple Intel Users
---

### Post by shortylonglegs on 2008-03-31
I have been using Ubuntu on my Dell for a while and like it, but I have to use a macbook for school.  I personally don't like the OS and was hoping to use Ubuntu from my USB drive [4gb].  I followed [these directions]("http://www.instructables.com/id/Boot-and-Run-Ubuntu-from-a-Flash-Drive/") to get it on my drive, but the computer does not recognize it while booting.  I have looked around and it appears this is the default, but did not find how to change it.  Is there a way to boot directly from USB on the macbook?  Could I boot from a disk that will then run from the USB, like slax?  Or is there virtual machine software anyone knows of I can run in OSX off a different partition of my flash drive, then from there run Ubuntu.  Any ideas?

---

### Post by cyberdork33 on 2008-04-01
Running Linux off a USB/Firewire drive does not seem to work correctly on Macs (See link in the FAQ).

For your situation, I would actually recommend using a VM in OSX. There are several to choose from (Parallels, VMWare Fusion, VirtualBox [free], Q [free]). The only problem here would be if you require 3d acceleration for anything since this is not supported on any VM (not in linux anyway).

---

### Post by shortylonglegs on 2008-04-01
Q seems to be working.  Thanks for the help.

---

### Post by cyberdork33 on 2008-04-01
> **shortylonglegs said:**
> Q seems to be working.  Thanks for the help.
Just because I care... :) I would definitely suggest trying VirtualBox on OSX, as I think it takes advantage of the Virtualization Extensions of the Core2 CPU. I don't think that Qemu does...

---

### Post by shortylonglegs on 2008-04-01
I tried Virtualbox, but I don't have admin rights since its a school computer.  I am able to run Q right of my flash drive and so thats the one.

---

### Post by mrsteveman1 on 2008-04-02
I haven't had any real problems running legacy (mbr) operating systems from USB sticks on my intel mini, as long as there is MBR boot code on the stick it seems to have no trouble booting it.

---

### Post by cyberdork33 on 2008-04-02
> **mrsteveman1 said:**
> I haven't had any real problems running legacy (mbr) operating systems from USB sticks on my intel mini, as long as there is MBR boot code on the stick it seems to have no trouble booting it.
I think that the Minis and the older Macbooks seem to not have as much an issue. and work as expected. It has been suggested that it is an Apple firmware bug.

---

### Post by mrsteveman1 on 2008-04-02
Yea apple does have some firmware issues, my aluminum keyboard startup keys still dont work on this mini because the EFI driver for the keyboard doesn't load, hence startup keys dont work, grub menus cant be navigated, etc.

---

### Post by cyberdork33 on 2008-04-02
> **mrsteveman1 said:**
> Yea apple does have some firmware issues, my aluminum keyboard startup keys still dont work on this mini because the EFI driver for the keyboard doesn't load, hence startup keys dont work, grub menus cant be navigated, etc.I did not know that was still an issue for people. This was solved for most with a firmware update long ago. (it was a bug with the old white keyboards too).

---

### Post by mrsteveman1 on 2008-04-02
Yea it's been an issue with some Minis and iMacs ever since the aluminum keyboard was released last year.

My theory is that the EFI driver isn't loading for the keyboard, maybe because the firmware thinks its only a USB hub for some reason. The ports get power but the keyboard itself, including the caps lock light (this is the clue), do not work until an OS kernel loads its own keyboard driver. 

There's a lot of threads about it on apples forum.

---

### Post by cyberdork33 on 2008-04-02
sounds similar to the previous problem though. have you tried unplugging and replugging the keyboard at the bootloader screen? that used to work for me on my iMac (of course, this was with the older keyboards).

---

### Post by mrsteveman1 on 2008-04-02
I haven't tried that (nor did i think of it), it may work. If it does, it will be a HUGE help to me as well as a lot of other people.

---

