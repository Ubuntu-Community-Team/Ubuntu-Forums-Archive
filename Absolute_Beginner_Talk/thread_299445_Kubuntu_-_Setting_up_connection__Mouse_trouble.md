---
title: "Kubuntu - Setting up connection / Mouse trouble"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Verminox on 2006-11-14
Hello. I'm new to the linux world... been using Windows for quite a few years... I just installed Kubuntu 6.06 LTS which I will be using as dual boot along with WinXP.

Anyhow, I was able to figure out most of the configuration settings by doing the obvious but I'm a little stuck at setting up a network connection. I'm using a broadband connection, and my ISP has given me the following information (along with my user account details):

IP Address
Subnet
Gateway
DNS

In Windows I would just create a new connection and in the TCP/IP settings I would enter the given values and then login to my ISP account using the dialer. However I have no clue how to go about doing this in Kubuntu. 

I managed to get to the Network configuration, entered the subnet and gateway address in the (hopefully) appropriate fields and the DNS addresses (2 of them) under "Domain Name Services" and the IP address in the properties of the ethernet device that was detected (sorry if I'm using some wrong terms, I rebooted and forgot what exactly it was called).

However, this did not do what I needed, I could not download/use the dialer via Konqueror as I would have in the Windows scenario with Firefox, so I have obviously done this wrong. Any help?




Another thing, the mouse that is connected in the PS/2 port does not get detected at all under Kubuntu, although it works fine under Windows. The keyboard that is conencted via PS/2 works fien in both. I tried using my old USB mouse and that worked in both as well... but I would really rather use the newer PS/2 one. 

Is there any way to make Kubuntu scan for undetected hardware and/or test if any device is connected into the PS/2 slot for the mouse?

I know this is really very minimal information I'm giving, I'm sorry, but I'm not really good with hardware. If any more information would help, let me know. 

Help is appreciated :)

---

### Post by dillbertdabomb on 2006-11-14
try cleanin out your ports-it just might help!

---

### Post by encompass on 2006-11-14
did the mouse work on your live cd?

---

### Post by Verminox on 2006-11-15
no actually it did not work on either live cd (ubuntu or kubuntu).

Now, when I start the computer (power on) the red light under the PS/2 mouse lights up, which means it is indeed working.

Then I get to the screen where I choose which OS I want to continue with. If I choose Windows XP, the mouse continues to work. But if I choose Kubuntu, then when Kubuntu is loading there is one line that says "Loading hardware drivers..... ok" and that is when the red light under the mouse goes off and it does not work once KDE is loaded.

So I realised this must be a problem with my mouse driver but it is just a plug and play device, I didn't get any driver CDs with it (and I don't think you need them for mice anyway). I checked up the driver details under windows and it just gives me the two files:
C:\Windows\system32\DRIVERS\i8042prt.sys
C:\Windows\system32\DRIVERS\mouclass.sys

The second fileis also in the list of my USB mouse drivers, so I guess that isn't a problem, I don't know if it is something with the other driver files that does not work under Linux.

---

