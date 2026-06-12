---
title: "need help with some newbie problems"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by mister_g on 2007-06-29
I need to resize some of the linux partitions and i found out that i need gparted. I already downloaded it but I don't know how to install it. 

I'm also trying to install ATI drivers for xpress 200. i got the drivers here:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

but I don't know how to install it.

lastly, I'm having problem connecting to a wireless internet connection with a password. But I can connect to unsecured wireless networks, The password is correct

---

### Post by whizbaby on 2007-06-29
Forget the bad habit of searching software all over the net to download and install, this is linux, man ;)

for gparted either open 'synaptic' or type (in terminal)

sudo apt-get install gparted

and it will be installed. The package for your aticard is named 'xorg-driver-fglrx' (sudo apt-get install xorg-driver-fglrx), look on this forum how to configure it after install.

You didnt say anything about your wireless card, so I cant, too :p

Downloading software packages manually from the internet is seldomly needed by linux users...

---

### Post by overdrank on 2007-06-29
> **mister_g said:**
> I need to resize some of the linux partitions and i found out that i need gparted. I already downloaded it but I don't know how to install it. 

I'm also trying to install ATI drivers for xpress 200. i got the drivers here:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

but I don't know how to install it.

lastly, I'm having problem connecting to a wireless internet connection with a password. But I can connect to unsecured wireless networks, The password is correct

Hi and welcome, I believe you need to use gparted from the cd ( it is on the live cd) if you can because you cant modify a partition that is mounted.
If you are using feisty then you should be able to use the restricted drivers for the ati card. It is under system,admin,restricted driver manager.
And I am sorry but I am not good with networking. :(

---

### Post by mister_g on 2007-06-29
> **whizbaby said:**
> Forget the bad habit of searching software all over the net to download and install, this is linux, man ;)

for gparted either open 'synaptic' or type (in terminal)

sudo apt-get install gparted

and it will be installed. The package for your aticard is named 'xorg-driver-fglrx' (sudo apt-get install xorg-driver-fglrx), look on this forum how to configure it after install.

You didnt say anything about your wireless card, so I cant, too :p

Downloading software packages manually from the internet is seldomly needed by linux users...

LOL sorry old habits die hard :)

I tried using the terminal and i got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate

what's this?

---

### Post by shirilover on 2007-06-29
You probably need to enable additional repositories.
See here -> [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by whizbaby on 2007-06-29
> **shirilover said:**
> You probably need to enable additional repositories.
See here -> [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
go for that

---

### Post by mister_g on 2007-06-29
I'm going through the repositories now :)

so essentially I just download what I need? nice...

---

### Post by mister_g on 2007-06-29
how do I find out what make and model of my wireless card in linux? I'm installing this onto a laptop so the wireless card is built into the motherboard right?

---

### Post by Seisen on 2007-06-29
type lspci in the terminal

---

### Post by overdrank on 2007-06-29
> **mister_g said:**
> how do I find out what make and model of my wireless card in linux? I'm installing this onto a laptop so the wireless card is built into the motherboard right?

If you go to terminal located under applications,accessories, terminal  enter the command
[PHP]lspci[/PHP]
Post the output here and we can help you find out what is !

---

### Post by mister_g on 2007-06-29
i also had problems earlier with partition magic and my initial installing of ubuntu:

[http://ubuntuforums.org/showthread.php?t=487382](http://ubuntuforums.org/showthread.php?t=487382)

Not knowing what to do, I just reinstalled the whole OS again. Does linux overwrite previous installations? at bootup with grub, there is this installation of linux, win xp and the previous linux installation. How to I remove the first one?

---

### Post by overdrank on 2007-06-29
> **mister_g said:**
> i also had problems earlier with partition magic and my initial installing of ubuntu:

[http://ubuntuforums.org/showthread.php?t=487382](http://ubuntuforums.org/showthread.php?t=487382)

Not knowing what to do, I just reinstalled the whole OS again. Does linux overwrite previous installations? at bootup with grub, there is this installation of linux, win xp and the previous linux installation. How to I remove the first one?

Hi you are going over to many things. Just pick one topic and then you possibly search the threads and help yourself find what you need. So lets just get the one.:(

---

### Post by mister_g on 2007-06-29
my specs:

video card:
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]

LAN card:
04:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Wireless:
04:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

---

### Post by mister_g on 2007-06-29
> **overdrank said:**
> Hi you are going over to many things. Just pick one topic and then you possibly search the threads and help yourself find what you need. So lets just get the one.:(


sorry getting a little carried away :)

---

