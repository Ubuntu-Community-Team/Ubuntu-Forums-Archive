---
title: "Need help installing ubuntu...sooo baaddd"
date: 2010-10-21
forum: Apple Hardware Users
---

### Post by edysing on 2010-10-21
Dear all ubuntu experts,

I am a newbie in linux OS, i already installed a couple ubuntu for my PC and netbook successfully.

But I have an old Powerbook G4 12" with nvidia graphics :( 
the specs are:
1. Speed 867 Mhz
2. Memory 640 Mb
3. DVD slot loading but not working anymore :(
4. OS Leopard 10.5.8

I've tried so many times to install many version of Ubuntu and failed, I use lili usb creator, i use external cd or dvd rom with firewire or usb. Nothing works. Because everytime i start up and i push "C", it continues to boot with leopard. If i use "option", it recognized the linux live cd, but can not boot from it.

Please all the expert, i needed so bad, i don't mind not using leopard, because leopard can not support new codec for multimedia, like mkv file and it is so slow.

Greatly appreciated.

---

### Post by alexandari on 2010-10-21
So you say it wont boot the installation?

---

### Post by edysing on 2010-10-21
Yes, it won't boot to linux live cd. I've tried many version from 9.04 up to 10.10. alternate or not. still won't boot. I've done zapping the pram. nothing seem to work.

Please help :(

---

### Post by linuxopjemac on 2010-10-21
MintPPC is your friend.

---

### Post by edysing on 2010-10-21
> **linuxopjemac said:**
> MintPPC is your friend.

I've tried it just now, 

"couldn't locate Partition can't open: usb0/disk@1:2,\\yaboot"

i format the usb disk with windows to FAT32.

am I wrong? i don't have gParted or any linux os, all i got now window 7 and Leopard.

Thanks for the suggestion though :)

---

### Post by utilitytrack on 2010-10-21
> **edysing said:**
> I've tried so many times to install many version of Ubuntu and failed

OMG. Ubuntu has not support of PowerPC processors. Try use Debian, it has full support of your notebook: 
[http://www.debian.org/ports/powerpc/inst/pmac]("http://www.debian.org/ports/powerpc/inst/pmac")

Good luck!

---

### Post by edysing on 2010-10-21
> **utilitytrack said:**
> OMG. Ubuntu has not support of PowerPC processors. Try use Debian, it has full support of your notebook: 
[http://www.debian.org/ports/powerpc/inst/pmac]("http://www.debian.org/ports/powerpc/inst/pmac")

Good luck!

Really? but at the ubuntu web, there is still iso for powerpc mac.
Which debian? 5.06? how do i install it? it even won't boot from cd. thanks.

I've tried to understand the installation process, but it is to hard for me to understand. Is there another alternative? USB Lili?

---

### Post by linuxopjemac on 2010-10-21
You have to dd the iso to the usb, from a Linux / unix / OSX box. Read my instructions.

---

### Post by utilitytrack on 2010-10-21
> **edysing said:**
> Really? but at the ubuntu web, there is still iso for powerpc mac.

Sorry me, my bad. I missed this: [http://cdimage.ubuntu.com/ports/releases/maverick/release/]("http://cdimage.ubuntu.com/ports/releases/maverick/release/")

---

### Post by linuxopjemac on 2010-10-21
Maybe you can also do it from within Windows:
[http://www.commandlinefu.com/commands/view/660/rip-an-iso-from-a-cddvd-using-the-freeware-dd-for-windows](http://www.commandlinefu.com/commands/view/660/rip-an-iso-from-a-cddvd-using-the-freeware-dd-for-windows)
[http://wiki.archlinux.org/index.php/Putting_installation_media_on_a_USB_key#The_Flashnul_Way](http://wiki.archlinux.org/index.php/Putting_installation_media_on_a_USB_key#The_Flashnul_Way)
Google a little about dd in windows

---

### Post by edysing on 2010-10-21
> **linuxopjemac said:**
> Maybe you can also do it from within Windows:
[http://www.commandlinefu.com/commands/view/660/rip-an-iso-from-a-cddvd-using-the-freeware-dd-for-windows](http://www.commandlinefu.com/commands/view/660/rip-an-iso-from-a-cddvd-using-the-freeware-dd-for-windows)
[http://wiki.archlinux.org/index.php/Putting_installation_media_on_a_USB_key#The_Flashnul_Way](http://wiki.archlinux.org/index.php/Putting_installation_media_on_a_USB_key#The_Flashnul_Way)
Google a little about dd in windows

Sorry man, tried it, i don't understand the steps, that is why i choose ubuntu, because it is the easiest to install.

Thanks though.:)

---

