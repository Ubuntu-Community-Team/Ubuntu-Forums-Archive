---
title: "WIRELESS: where do i start?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by mills on 2007-04-21
how do i get Ubuntu to see my wireless card?

lspci doesn't see any network controller

but my router seems to detect my wireless card

what do i do now?

wireless card = D-Link dwl-g510
feisty

---

### Post by szymon_g on 2007-04-21
what shows iwconfig ?

---

### Post by mills on 2007-04-21
alex@alex-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

alex@alex-desktop:~$

---

### Post by mills on 2007-04-21
as you can see the router detects a wireless connection but ubuntu seems oblivious to it

---

### Post by szymon_g on 2007-04-21
hm... you have to install drivers for it (if exist) or use ndsiwrapper (or something with similar name ;P). but don't ask me for more :-/. for this ndsw<something> you need windows' drivers.

---

### Post by mills on 2007-04-21
iam not sure what drivers i need. lspci is supposed to tell me

---

### Post by st33med on 2007-04-21
Just download ndiswrapper. It should help.

---

### Post by mills on 2007-04-21
installed ndiswrapper and not alot happening

in fact nothing happening

is ndiswrapper supposed to show up in one of the menu's?

---

### Post by thomasbaker on 2007-04-21
what kind of computer do you have???

---

### Post by mills on 2007-04-21
fujitsu siemens scaleo

intel pentium 4
ati 9200se

```
alex@alex-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 51)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0d.0 Modem: Smart Link Ltd. SmartLink SmartPCI562 56K Modem (rev 04)
00:14.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
alex@alex-desktop:~$ 
```

---

### Post by DeadEyes on 2007-04-21
Is your wireless card the D-Link DWL-G510 AirPlus G?
And are you running 6.10 or 7.04?
In 6.10 I had to do a lot of messing about to get it to work [this]("http://ubuntuforums.org/showthread.php?t=132980") link helped a lot.

In 7.04 after an upgrade everything was messed up because of all the editing to files I'd done to get wireless working in 6.10. However after doing a clean install I was able to do a manual network config and everything just  worked.
My /etc/network/interfaces file has the following entry

iface ra1 inet static
address <my ip>
netmask 255.255.255.0
getway <my router ip>
wireless-essid <my essid>
wireless-key <my key>

auto ra1

---

### Post by mills on 2007-04-21
iam in feisty and just checked my interface file and it looks good

auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp






iface ra1 inet static
wireless-essid SpeedTouchC78D2E
wireless-key secret:P
address 10.0.0.138
netmask 255.0.0.0
gateway 192.168.1.254

auto ra1




iface eth0 inet dhcp

auto eth0

---

### Post by DeadEyes on 2007-04-21
lspci doesn't appear to be showing up you card, do you have dual boot with windows to check if it can see it? You might want to try sticking it in an other pci slot see does that make any difference.

---

### Post by DeadEyes on 2007-04-21
Also try
sudo iwconfig ra1
to see if that looks ok 
and 
iwlist ra1 scan
to see if your card can detect APs

---

### Post by mills on 2007-04-21
tried the different slot and windows doesnt see it either and the out of the above is...

alex@alex-desktop:~$ sudo iwconfig ra1
Password:
ra1       No such device

alex@alex-desktop:~$ 
alex@alex-desktop:~$ iwlist ra1 scan
ra1       Interface doesn't support scanning.

alex@alex-desktop:~$

---

### Post by mills on 2007-04-21
ok i feel like a right *%$*  

just got a little stressed and decided my card needed a little encouragement by way of a good punch and i felt the card move in about a mm then i pushed the other side its gone in aswell and 
behold a wireless connection is found:oops: :oops::oops:

but still cant connect to the wireless network

---

### Post by mills on 2007-04-21
ok switched to dhcp and iam now wireless, told you it was easy lol

cheers for the help deadeyes and everyone else, next time feel free to call me mr numpty

---

### Post by st33med on 2007-04-21
Heh, always check to see if your wireless card is fully in, people. :)

---

### Post by DeadEyes on 2007-04-22
> **mills said:**
> just got a little stressed and decided my card needed a little encouragement by way of a good punch
A new twist on the old favourite, that is technically known as gravity maintenance. :)

---

