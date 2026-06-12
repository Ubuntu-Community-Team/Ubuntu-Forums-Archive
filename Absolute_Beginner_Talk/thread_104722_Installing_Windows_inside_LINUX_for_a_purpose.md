---
title: "Installing Windows inside LINUX for a purpose"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by kenweill on 2005-12-16
Is it possible to install a fresh copy of windows 98/xp inside WINE?

I really need windows inside linux for me to connect to the internet. The software that comes with my modem is windows based. And should have the accelerator/driver that comes with my modem in order for me to connect to the internet. Its a satellite modem. Windows based.

I tried using WINE but it produces an error looking for windows and IE.

The connection/authentication is very different. It won't even work with a router. The ISP said that it should have the accelerator to be connected to the internet with their device.

How can I install a fresh copy of windows inside linux?

---

### Post by Mustard on 2005-12-16
I'm no expert on linux, but I can't see how you are going to do that succesfully using wine.

Wine doesn't emulate windows.  What it does it take the calls that windows usually makes to itself and redirects them to the linux equivalent.  Essentially you are still going to have a functional modem setup using linux for wine to be able to call the modem and use it.

What is the brand of modem you are using?

---

### Post by ninotob on 2005-12-16
You might want to look at:  [http://www.win4lin.com/](http://www.win4lin.com/)

It's non-free software.  Once upon a time I used it but it was more of a hassle than it was worth to me ultimately -- it might be different now, but it used a custom kernel so I had to manually update it when changes came out.  It did however run windows just fine -- you do need to have a windows install disc as well.  

I don't know whether it would work with the sattelite gear or not -- they have some forums so I'd ask around there before buying if you decide to go that route.

---

### Post by drummer on 2005-12-16
You can also do a search for vmware player and how to install windows in it. There are a couple threads about it and numerous articles on the internet. Athough you wouldn't have internet access in Linux, only in the virtual computer run by the vmware player.

Maybe also give crossover office a shot; it's non-free, but there's a trial version.
If you post the details of the modem you're using maybe someone else will have a solution, or have had the same problem.

---

### Post by GreyFox503 on 2005-12-17
You should try to get your driver working under Linux if at all possible.  Windows itself cannot be installed under WINE, WINE is supposed to emulate Windows.

If you use a virtual machine software like VMWare to install Windows, then your internet connection will only be able to be used by Windows, and not Ubuntu anyway.

---

### Post by kenweill on 2005-12-17
[QUOTE=Mustard]
What is the brand of modem you are using?[/QUOTE]

Gilat Satellite Modem 360.

When I do ipconfig /all under windows. it displays the ipaddress, dns, and gateway. but i cannot ping all those numbers(ip) except my ipaddress. Its a dhcp anyway.

It needed an accelerator/driver, which is windows based:
Internet over Satellite Accelerator
and
Internet Page Accelerator.

Those accelerator connects, or i guess authenticates to another ip add.

I tried setting it up on ubuntu but it would just produce an error, NO DEFAULT ROUTE. and the GATEWAY UNREACHABLE or something like that.

---

### Post by BLTicklemonster on 2005-12-17
This is what you need.

[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

---

