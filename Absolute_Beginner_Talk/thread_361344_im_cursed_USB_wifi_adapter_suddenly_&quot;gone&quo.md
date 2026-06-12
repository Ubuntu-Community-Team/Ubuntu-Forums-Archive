---
title: "im cursed: USB wifi adapter suddenly &quot;gone&quot;"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by xSauronx on 2007-02-14
Ive got an Asus WL-167g USB adapter ive been using for weeks now without a problem. This is with Xubuntu 6.10 on an Inspiron 1000

Ive been sick from work, and the thing has been connected all day, every day, since friday without a problem. I wanted to check a BIOS setting this morning for something, rebooted, and now iwconfig no longer sees my adapter :(

lsusb shows its there. i havent changed *any* system settings that should affect this. but iwconfig no longer sees the device "rausb0" and Im not sure where to start to get it working again, but I *need* this for work this week when i go back because im doing an install for a customer of a couple of WAPs and need to be able to roam their house to test the signal :/

any ideas?

---

### Post by ukripper on 2007-02-14
> **xSauronx said:**
> Ive got an Asus WL-167g USB adapter ive been using for weeks now without a problem. This is with Xubuntu 6.10 on an Inspiron 1000

Ive been sick from work, and the thing has been connected all day, every day, since friday without a problem. I wanted to check a BIOS setting this morning for something, rebooted, and now iwconfig no longer sees my adapter :(

lsusb shows its there. i havent changed *any* system settings that should affect this. but iwconfig no longer sees the device "rausb0" and Im not sure where to start to get it working again, but I *need* this for work this week when i go back because im doing an install for a customer of a couple of WAPs and need to be able to roam their house to test the signal :/

any ideas?

paste your output of iwconfig and interfaces file located in /etc/network/interfaces

---

### Post by xSauronx on 2007-02-14
> **ukripper said:**
> paste your output of iwconfig and interfaces file located in /etc/network/interfaces

iwconfig returns:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.


----------


there should be "rausb0" listen with all pertinent wireless information :/

cat /etc/network/interfaces    returns:

auto lo
iface lo inet loopback


auto eth1
iface eth1 inet dhcp
wireless-essid Ostia


auto ath0
iface ath0 inet dhcp





iface eth0 inet dhcp
address 10.121.1.203
netmask 255.255.255.0
gateway 10.121.1.1






















































































iface rausb0 inet dhcp
wireless-essid Ostia
wireless-key s:





auto eth0

auto rausb0
:::::;


just like that, not sure why all of the blank space in it. its also no longer under the "network settings" panel

oddly enough, adding an older adapter i had once tried to get working with ndiswrapper (to no avail) *does* come up under iwconfig when i plug it in, and under my network settings panel. it wont connect, being a lousy piece of hardware and all ;)

---

