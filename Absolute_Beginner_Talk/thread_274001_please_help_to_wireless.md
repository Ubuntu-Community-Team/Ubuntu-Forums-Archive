---
title: "please help to wireless"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by majoorpa on 2006-10-09
I am a newbie to linux who came from windows xp background.

I have been trying to go wireless.
My system PIV 3.2GHz, 1028MB RAM, Packard Bell Easynote 5315. I am trying to get on wireless with Belkin 75D7011. My OS is Ubuntu 6.06 LTS updated to 9/10/06. I have installed ndiswrapper-utils and followed as per the instructions from several website sources. The command 'sudo ndiswrapper -l' gives me the following result:

Installed ndis driver present:
bcmwl5    driver present

I understand it should also say 'hardware present'. So it means my OS has not configured my pcmcia hardware. I tried the command 'lspci' and got the following result:

0000:02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Hence I understand the OS is recognizing the card but probabily not starting it. I tried 'modprobe -l' command and it is not listing in that one. Can some one please help me?

---

### Post by bigspottycat on 2006-10-09
I had a similar problem setting up my belkin F5D7011 wireless card. This is my first reply so let me know if it needs clarifying. Unfortunately I am also a newbie so I don't understand exactly how it works but this is how I got my card working:

I used the instructions from here: [http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom)
NB: must be done from 'clean install'.


This is my version of those instructions:
Uncomment (remove the #) from ubuntu repositories in sources.list:
sudo nano /etc/apt/sources.list
 
Download wl_apsta.o from somewhere and unzip to Desktop if needs extracting.

Then in the terminal type:
sudo apt-get install bcm43xx-fwcutter (may need to locate and download this with google)

Then in the terminal type:
sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
(substitute Desktop for whichever folder contains wl_apsta.o)

Then in the terminal type:
sudo bcm43xx-fwcutter -w /lib/firmware/2.6.15-25-386 ~/Desktop/wl_apsta.o
(substitute2.6.15-25/386 with most uptodate directory in lib/firmware) and substitute Desktop with whichever folder contains wl_apsta.o)

Then in the terminal type:
sudo apt-get install network-manager-gnome
Reboot for settings to take effect. Wireless connection should appear on applet but may need WPA keycode depending upon your router.

Hope this helps.

---

### Post by majoorpa on 2006-10-09
Wow my wireless is working flawless. I am posting this message through my wireless. I followed the exact step by step as adviced by 'bigspottycat'. Thank you very much.

This is the first time I am asking for help from linux community. It is impressing to get exact information I required with in an hour. Thanks a lot. This will encourage me stay with linux for long.

If any one require wl_apsta.o, the following is the link:
[http://boredklink.googlepages.com/wl_apsta.o]("http://boredklink.googlepages.com/wl_apsta.o")

Thanks again

---

### Post by FrankVdb on 2006-10-09
I'm also new to Linux and I'm very much impressed too...

I remember buying my first computer, a Commodore 128, in 1985 as a 15-year old. My mother was a divorced woman and couldn't afford to buy luxury stuff like computers for us, so I worked in the holidays to save money. The joy I felt when writing my first simple programmes is something I still remember...

It took me a lot of time to get Linux installed on a two-year old machine, but thanks to the Ubuntu community I got it up and running. The first time Ubuntu started up flawlessy on that computer, I felt the same joy coming up as 20 years ago.

Life can be great.

---

