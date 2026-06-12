---
title: "Install"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by slutbit on 2008-01-26
I have asked questions before with this account but they have disappeared so i ask again. Im totally new at ubuntu, but have used linux, unix or sth at the uni. Just want to install for programming from my own computer.

Some questions:

1.
How do one install c- libraries like GNU scientific library GSL from [http://www.gnu.org/software/gsl/](http://www.gnu.org/software/gsl/)
"Installation instructions can be found in the included README and INSTALL files." But they have forgotten to write the installation instructions in those files. It just says:
/usr/bin/ld: cannot find -lgsl
collect2: ld returned 1 exit status
when i try to compile with gcc


2.
How does one install programs, like Kdevelop. I tried installing it on Add/Remove Apps. and it says:

"The list of applications is not availabe
Click on 'Reload' to load it. To reload the list you need a working internet connection."

Dont know what availabe is but i click reload and then something happens but it surely does not get installed.Its the same thing with most of the applications provided by the ubuntu community: They are not avalibe


3.
Tried to play a dvd on movieplayer last evening, but it needed some codex but it was not possible to install them, and i wouldnt dream of trying to install vlc-player

"Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.
Please install the necessary plugins and restart Totem to be able to play this media."

So i tried to follow the instructions on, but i didnt manage of some reason.
[http://www.gnome.org/projects/totem/#codecs:popcorn:](http://www.gnome.org/projects/totem/#codecs:popcorn:)

And as always the question...
"Q: Why does seeking with the keyboard keys (Left and Right arrow) in Totem not seek the same amount of time in either direction?"
...is ofcourse more frequent then "How do i install?"


4.
I have tried to get the wireless connection to work even though i use wired internet now. I saw somewhere somebody mention System->Administration->Network and there clicking  wireless sth, but it doesn't exist anything like that.


I have alot more questions but i dont remember them now, i dont think anything has worked properly in ubuntu at all in the beginning. Is it like this for everybody who starts using ubuntu 7.10? I have even reinstalled it now, cause nothing worked last time either.

---

### Post by dstew on 2008-01-26
> i dont think anything has worked properly in ubuntuWhat are the speciifications of your hardware (processor, speed, memory size)?

---

### Post by slutbit on 2008-01-27
Its a new laptop, 1.7 Ghz celeron something with 1Gb ram.

---

### Post by dstew on 2008-01-28
> How do one install c- libraries like GNU scientific libraryInstall the packages **build-essential** and **linux-headers** for your particular kernel using Synaptic. You can get the kernel version using the command **uname -r**. That will get you started. Other more specific libraries can usually be found in Synaptic.> How does one install programsI use Synaptic. You need to go to the Settings tab to enable the software repositories that you need, like multiverse and universe.> Tried to play a dvd on movieplayer last evening, but it needed some codexCodex packages are also installable from Synaptic.> I have tried to get the wireless connection to workPost the output of the commands **lspci** and **iwconfig** onto the forum to get started.

---

### Post by slutbit on 2008-02-03
Ok i found synaptic, very good for me! I can mention that wireless works on winxp which is also installed on this laptop.

writing lspci gives:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


iwconfig gives:

lo        no wireless extensions.

eth0      no wireless extensions.



//Thanks

---

### Post by dstew on 2008-02-04
I do not see a wireless card listed there. Is your wireless connection a USB device?

---

### Post by slutbit on 2008-02-04
no, its not usb connection. Its a newly bought laptop and I installed xp and ubuntu over vista. In xp i had to download the drivers from toshiba homepage(I have a toshiba). The drivers was not available for unix or ubuntu, just vista and xp. And it was properly installed on xp but i dont know how to or where to look for drivers for ubuntu. I assume ubuntu dont think i have any wireless hardware cause it cant find the drivers.

---

