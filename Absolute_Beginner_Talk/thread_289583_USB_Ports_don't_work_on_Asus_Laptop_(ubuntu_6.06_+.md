---
title: "USB Ports don't work on Asus Laptop (ubuntu 6.06 +updates)"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by pjotter on 2006-10-31
Hi All,

I have a Asus A6000 entertainment series latop and have problems getting the usb-ports to work. I tried the Dutch forums (my language) but I couldn't get solutions.

No usb-devices do work or are recognized, I guess, cause i'm new to linux systems. 

In kernel "lsusb" and "dmesg | grep usb" do not return anything, I just get the next empty command line (~$).

I followed the actions described in: 
[http://www.ubuntuforums.org/showthread.php?t=70915&highlight=USB+Ports+-Working%21](http://www.ubuntuforums.org/showthread.php?t=70915&highlight=USB+Ports+-Working%21)
so I added "acpi=off apm=on" at the end of the  line:  
"kernel /boot/vmlinuz-2.6.15-27-368 root=/dev/hda8/ ro quiet spalsh"

I have a optical wired mouse (brand: Genius), when I press a mouse-button the laser-light reacts.

I don't know what to do/try  now, can somebody please help me?

I hope so, thanx for reading anyway,

Pjotter

---

### Post by pjotter on 2006-10-31
The device manager shows 4 General ID for reserving resources by pnp motherboard registers. It indicates that these devices (and drivers) are unknown.
I have 4 usbslots, so I checked and installed several USB-utilities with the package manager, but still no result.

Any idea?

---

### Post by qscgz on 2006-10-31
[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

[https://wiki.ubuntu.com/LaptopTestingTeam/Asus](https://wiki.ubuntu.com/LaptopTestingTeam/Asus)

:KS

---

### Post by pjotter on 2006-10-31
thank you for your reaction qscgz,
I have seen the links, but the reports show me that USB-mouse worked fine. 

Any other suggestions? I'm running desperate....:(

hope so, 
thnx

---

