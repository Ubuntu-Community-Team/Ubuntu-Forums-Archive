---
title: "Kubuntu 14.04 on imac 2009 without refit/refind dual boot OSX installation"
date: 2014-12-29
forum: Apple Hardware Users
---

### Post by opoq on 2014-12-29
Quick question regarding the installation:

I've used this guide, since it gives instruction to have an installation w/o refit/refind: [https://help.ubuntu.com/community/MacBookPro11-1/Saucy](https://help.ubuntu.com/community/MacBookPro11-1/Saucy)
> 
[LIST=1]
[*]Enter live mode (i.e. "Try Ubuntu").  You need to perform post-installation checks and fixes. 
[*]Click  "Install Ubuntu" to start installation.  Follow the instructions.  When  it asks you for how to install onto the disk, you could choose to  install "Alongside with MacOS" or choose the last option to set up the  partitions yourself.  Make sure /dev/sda1 is mounted as /boot/efi (an  EFI boot partition). 
[*]After installation, do NOT restart.  We need to fix the EFI boot order information.  Open a terminal, and type the following 
```
sudo apt-get install efibootmgr
sudo efibootmgr
``` 
[/LIST]

Installation process went w/o trouble. This is where I'm stuck: 
```
kubuntu@kubuntu:~$ sudo efibootmgr
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
kubuntu@kubuntu:~$ sudo modprobe efivars
kubuntu@kubuntu:~$ sudo efibootmgr
Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
```

A few notes:
Even though I've created two new partitons from within OSX at the end of the hdd, installation would not give the option to install "Alongside with MacOS"; so I went for manual:
/dev/sda4 is swap (no option to format); /dev/sda5 is root (formatted to ext4) 
> Make sure /dev/sda1 is mounted as /boot/efi (an  EFI boot partition)It was not possible to specify a mountpoint here, however it was recognized as EFI boot partition in the Edit Partition dialogue.

How to proceed with efibootmgr? I'm still in the original boot-from-live-CD-session

---

### Post by opoq on 2014-12-29
Being a little impatient, I've closed the live cd session, and the started the imac with no options: OS X started as if nothing changed. After a reboot from OSX, I've held down the Alt-key and got *Windows* as one of the four (besides OSX, OSX recovery, bootable USB-stick that was still attached) options to boot. This started Kubuntu as required. Success at least for the installation and being able to boot both OS without refit/refind.

Though, when [FONT=courier new]
cd /boot
sudo mkdir efi
sudo mount /dev/sda1 /boot/efi

sudo apt-get install efibootmgr
sudo efibootmgr[/FONT]
it would return
[FONT=courier new]Fatal: Couldn't open either sysfs or procfs directories for accessing EFI variables. Try 'modprobe efivars' as root.[/FONT]
again.

Why is it not possible run efibootmgr from the final system?

---

