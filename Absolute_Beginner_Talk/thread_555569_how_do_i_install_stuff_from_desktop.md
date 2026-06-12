---
title: "how do i install stuff from desktop?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by creegun on 2007-09-20
hey, ive downloaded to my desktop 3 programs.
avant browser, msn messenger and some game.
but whenever i doubleclick to install it opens an error window with the following messege:

"Cannot open /home/creegun/Desktop/ab-setup(avant).exe: No application suitable for automatic installation is available for handling this kind of file."

i understand that i cant run 'exe' files, but how will i install those things?

---

### Post by overdrank on 2007-09-20
> **creegun said:**
> hey, ive downloaded to my desktop 3 programs.
avant browser, msn messenger and some game.
but whenever i doubleclick to install it opens an error window with the following messege:

"Cannot open /home/creegun/Desktop/ab-setup(avant).exe: No application suitable for automatic installation is available for handling this kind of file."

i understand that i cant run 'exe' files, but how will i install those things?

Hi and welcome these links may help
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
Avant
[http://awn.wetpaint.com/page/Ubuntu?t=anon](http://awn.wetpaint.com/page/Ubuntu?t=anon)
Gaim is located under applications, internet, Gaim. It is a instant messenger.

---

### Post by tenjin1 on 2007-09-20
can you please post the exact names with file extension of the files you downloaded? Then we can go from there on how to install them.

---

### Post by ukripper on 2007-09-20
FOr MSN -
```
sudo apt-get install amsn
```   -- Make sure universe repo is ticked in synaptic package manager

For AVANT - [http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository)

And for some GAME - depends on what is this **some** game?

---

### Post by creegun on 2007-09-21
thanx for the links.
ive had another problem now, i have to install my wireless internet(program called 'open one'). cant belive it didnt come to my mind before, but im gonna try creating a repository to the install cd  (i probebly mixed terms now, nvm)

abot the game its a 2d mmorpg/MUD game called rpgwo(rpg world online), but screw that now i have much more urgent matters.

gonna check round the forum to see whats this wine thing i keep seeing all over the place

---

### Post by ukripper on 2007-09-21
information for wine and guide to install on ubuntu - [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

And what about your Wireless ..Are you conected to internet using wirless? Open one???

---

### Post by creegun on 2007-09-21
allright heres the wireless i have:
named 'level one' or slomething like that
WPC-0300
WNC-0300
11g wireless LAN

thats whats written on the install CD anyhow...
ive tryed to create a repository to this install cd but for some reason it dont allow the cd i enter to be used or something, even the one i installed ubuntu with.

how the hell am i seppose to intall my internet???

---

### Post by ukripper on 2007-09-21
ok. Could you post output of the following command after typing in the terminal window -
```
lspci
```

We need to find the chipset your wireless card is using.

---

### Post by creegun on 2007-09-21
creegun@creegun-desktop:~$ lspci 
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge 
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge 
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge 
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge 
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge 
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge 
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge 
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) 
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) 
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) 
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) 
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South] 
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60) 
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78) 
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02) 
creegun@creegun-desktop:~$

---

### Post by creegun on 2007-09-22
bump

---

### Post by creegun on 2007-09-23
bump
ive gave the code like you asked, now what?

---

### Post by ukripper on 2007-09-24
Can you also post output of the follwoing commands -

```
sudo gedit /etc/network/interfaces
```


```
sudo ifconfig
```

```
lspci -v | less
```

---

### Post by creegun on 2007-09-24
heres the first:

auto lo

iface lo inet loopback



auto eth0

iface eth0 inet dhcp



auto eth1

iface eth1 inet dhcp



auto eth2

iface eth2 inet dhcp



auto ath0

iface ath0 inet dhcp



auto wlan0

iface wlan0 inet dhcp



and the second:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


and the last one:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by ukripper on 2007-09-24
and how about third?
```
lspci -v | less
```

---

### Post by creegun on 2007-09-24
i did write it:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by creegun on 2007-09-27
well, i have to go tommorow for about a week.
please post what i need to do next untill i get back...:confused:

---

