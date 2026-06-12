---
title: "FFR: How I installed Ubuntu 7.10 - It wasn't easy!"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Mats_swe on 2008-01-18
For Future Reference (maybe):

I have a [Fujitsu-Siemens Laptop Amilo Pa2510]("http://extranet.fujitsu-siemens.com/VIL/dmsp/d7/08/ds_amilo_pa_2510.pdf") and now have Ubuntu 7.10 installed. It didn't go easy (as some people in the forum might Know by now - here is the hole story:

One winter day in Edinburgh I sat down hopefull and enthusiastic by references that it only takes about 30 minutes to install Ubuntu - Perfect, I really need it know for my studies.

I'm not going to tell you about all the live cd:s I have tried and how it all failed. This is the straightforward (which I wanted to know before this adventure):

1. Start the live CD.
2. Choose "Start or Install Ubuntu".
    After a while it stops on "Running local boot scripts (/etc/rc.local) [OK]
3. Press ALT-F2 to get a command line.
4. Type ```
Sudo apt-get update
Sudo apt-get install xorg-driver-fglrx
Sudo depmod -a
```
This will download all the drivers for my ATI Radeon Xpress 1200 video card.
5. Type ```
Sudo nano /etc/X11/xorg.conf
```.
Now you can edit the file. I just changed keyboard layout from "us" to "se" (beacuse I have a swedish keyboard layout) and changed the driver for the vidoe card from "vesa" to "fglrx"
6. Save by pressing F2, choose Yes and press Enter
7. Type
```
sudo nano /etc/usplash.conf
```
8. Edit the file and use 1024x768 (or what you know your screen can handle)
```
Startx
```

Now it starts and I can get into Ubuntu from the live CD.

9. Install. Follow the directions and reboot.

    When I start and choose Ubuntu from the GRUB I only get a blank
    black screen. Do this:

10. Directly when it goes blank type
      CTRL-ALT-F1

11. It stops on "Running local boot scripts (/etc/rc.local) [OK]"
12. Press ALT-F2 to get a commando line.
13. Login with your choosen username and password.

14. Type
```
Sudo apt-get update
Sudo apt-get install xorg-driver-fglrx
Sudo apt-get install linux-restricted-modules-generic restricted-manager
Sudo depmod -a
```
It downloads the drivers for my video card.
Why couldn't I do this from recovery mode? It couldn't connect to internet then. It said "Could not resolve gb.archive.ubuntu.com" and "Failed to fetch http://gb.archive.ubuntu.com/...../..."

15. Type
Sudo nano /etc/X11/xorg.conf
Edit the driver from "ati" or "vesa" to "fglrx".

16. Type
```
startx
```

17. Everything is correct now? YES!
 
Maybe this will help someone...

---

### Post by gn2 on 2008-01-18
Did you try the Alternate CD?

---

### Post by mali2297 on 2008-01-18
Congratulations! =D>

Nice instructions. You should change *Sudo* to *sudo* though. (Commands in Linux are case-sensitive.)

---

### Post by Mats_swe on 2008-01-18
> **gn2 said:**
> Did you try the Alternate CD?

Yes I did. I installed it, but couldn't start because the boot script couldn't run. When I then tried to download things it didn't work, I don't know why - It couldn't connect.

---

### Post by Mats_swe on 2008-01-18
> **mali2297 said:**
> Congratulations! =D>

Nice instructions. You should change *Sudo* to *sudo* though. (Commands in Linux are case-sensitive.)

Thanks, It may sound quite easy and straightforward but I had no idea about any of the commands a few days ago...

I guess I'm just used to starting a sentence with a capital letter, but of course it should be - sorry about that.

---

### Post by DuncanG on 2008-01-25
```
sudo nano /etc/usplash.conf
```

That was the key, change the default resolution to 1024x768 after installing drivers, and I get the logon screen without having to press CTRL-ALT-F8. Many thanks.

---

### Post by hakuryu on 2008-01-27
I just managed to get Ubuntu 7.10 installed un my amilo PA2510 thanks to your excellent solution! Thank you very much, that saved me a lot of work that I need to put on my studies. Now I just need to get the Linux set up for my local Windows network and install my printer, but that shouldn't be too difficult.

I bow to you
Anders

---

### Post by Natanael_L on 2008-02-16
You totally RULEZ! :P
You made Ubuntu work on my laptop!

*BUT...!*
My WLAN card (Atheros AR5007EG) won't work... :(

---

