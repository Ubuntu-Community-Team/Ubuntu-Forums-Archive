---
title: "Dual boot with a twist"
date: 2012-12-22
forum: Any Other OS
---

### Post by kervil on 2012-12-22
Some time ago my parents killed their PC, so I've left them with my old Toshiba notebook running Xubuntu distro. Recently I've purchased a Asus Nexus 7 tablet and, while I'm visiting for xmass, tried to setup some kind of connection sharing with the notebook. This failed, as Android devices cannot connect to ad-hoc. So, my next idea was to dual boot with Windows XP. I have created an NTFS partition using GParted, but the attempt to install Windows failed, due to "BootMGR is missing" error. Here's where the twist comes in: the DVD drive in this notebook is broken and all I have to work with is 1GB usb drive. I have and *iso of my windows copy, I can download and create a bootable USB of any diagnostic/repair software you can name, but here's the problem of having one usb drive comes in. So, whan can I do with what I have? Is there a way to create a dual boot USB drive with some kind of diagnostic tool, that will set the MBR for Windows install AND the Windows installation on it (I use WinUSB)? Or can I try some other way around it?

ANY help is greatly appreciated ;)

---

### Post by Supercomputerpower on 2012-12-22
use grub as bootloader [http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)
first install windows on the entire disk then a linux distribution ubuntu and redhat wil give you the option install side by side and you can choose the partition size and will automatically create a grub bootloader multiboot is done.;)

i hope this wil help to solve the problem [http://download.cnet.com/EaseUS-Partition-Master-Home-Edition/3000-2248_4-10863346.html?tag=mncol;1](http://download.cnet.com/EaseUS-Partition-Master-Home-Edition/3000-2248_4-10863346.html?tag=mncol;1)

[http://download.cnet.com/Easeus-Partition-Recovery/3000-2248_4-75279786.html]("http://download.cnet.com/EaseUS-Partition-Master-Home-Edition/3000-2248_4-10863346.html?tag=mncol;1")

---

