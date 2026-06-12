---
title: "Using Ubuntu for first time.  Wireless router issues."
date: 2006-06-20
forum: Absolute Beginner Talk
---

### Post by Cryptopsy on 2006-06-20
Hello. I am an Ubuntu newbie.   I have a notebook that uses a wireless router to connect to the internet.

I recently made a Ubuntu boot disk so I can try out Linux for the first time.  Once I booted Ubuntu up, I went and set up my wireless network settings.

I entered my ssid, WEP key etc.  In the upper right side of the screen it shows "green bars" that which I assume means I am connected.
BUT...

When I open firefox, I can not connect to any websites.  I dont know whats wrong.  This router works fine in XP.


The router Im using is a D-Link DI-624. Any advice would be appreciated.  Thanks!

Ryan

---

### Post by kb3hkg on 2006-06-20
check to see if you are getting an IP address, run the command ifconfig in a terminal.

---

### Post by moffa on 2006-06-20
If you are getting an ip address from the router but still having issues, try

Going to System > Administration > Networking

On the DNS tab Click on Add (Servers) and enter the ip address of your router.

---

### Post by Cryptopsy on 2006-06-20
How do I run the terminal program?

Basically at the moment, I got my hard-wired connection to work on my wireless router.  As in, I have my laptop physically connected to the router.  That worked just fine.  Im just having a helluva time trying to get my wireless ethernet to connect with the wireless router.  It was no problem on XP, but linux seems a bit trickier.

Thanks all

---

### Post by kb3hkg on 2006-06-20
It is your command line, the program itself in gnome is called Terminal, I am using KDE though and don't recall it's location in gnome, can anyone else help out here? if not press Alt + F2 on ur keyboard and type in terminal.

---

### Post by Cryptopsy on 2006-06-20
Ok, Duh, I found it. It was right in front of me. haha

I also found a page on this forum that tells how to set up a wireless card buy extracting files from the windows drivers

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)


I might give that a try once I actually format this computer and install Ubuntu on the hard drive, rather then using a boot disk.

---

### Post by kb3hkg on 2006-06-20
Ndiswrapper is one way to go unless you have a natively supported card.

---

### Post by Cryptopsy on 2006-06-20
What about MADWIFI?

---

### Post by kb3hkg on 2006-06-21
madwifi works great, it is what I use, but as far as I know you can't just use that if you are going the windows drivers route. Madwifi does seem to just work for atheros chipsets though.

---

### Post by Cryptopsy on 2006-06-21
I actually think I might try the MADWIFI routh first.  My wireless car does infact use a Athreos chipset, and is listed as being supported on the MADWIFI website. :grin:

---

### Post by kb3hkg on 2006-06-21
ok then go for it. if you plan on using wep or wpa it can get a bit tricky, but madwifi does work.

---

### Post by Cryptopsy on 2006-06-21
What sort of situations arise if I am using WEP and MADWIFI?

---

### Post by kb3hkg on 2006-06-21
I don't believe it is a madwifi problem, it is just a bit tricky to get WEP or WPA working easily in linux, though vast improvements are being made, and the GTK Wifi project aims to make all of it done through a GUI.

---

