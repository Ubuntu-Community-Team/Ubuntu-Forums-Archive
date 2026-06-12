---
title: "Linux as a Gateway"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by mAkKoOo210 on 2007-06-04
How do I setup my Linux configuration to make my Ubuntu computers work as a Gateway for a Windows one?
I searched some guides but they're confused
:D

---

### Post by viciouslime on 2007-06-04
Did you try this one? [https://help.ubuntu.com/community/InternetConnectionSharing]("https://help.ubuntu.com/community/InternetConnectionSharing")

Failing that, I believe there is a way to do it using firestarter and its gui, but i have never used it so i don't know how exactly, worth searching for though, or even just installing it and having a go. :)

---

### Post by mAkKoOo210 on 2007-06-04
> **viciouslime said:**
> Did you try this one? [https://help.ubuntu.com/community/InternetConnectionSharing]("https://help.ubuntu.com/community/InternetConnectionSharing")

Failing that, I believe there is a way to do it using firestarter and its gui, but i have never used it so i don't know how exactly, worth searching for though, or even just installing it and having a go. :)
I'm looking at the guide. I have a Usb modem, so I use a PPP interface, right?
Firestarter is a program? I can't try it now because my modem today seems to don't see the network using Ubuntu (I opened a thread for this), now I'm on Xp:(

---

### Post by viciouslime on 2007-06-04
Yes firestarter is in the repos, "sudo apt-get install firestarter" or use synaptic. I have never used it, but I have read that you can share a connection with it :)

---

### Post by viciouslime on 2007-06-04
Ok, I've just tried installing it out of curiosity and sure enough the first time you run it you get a step-by-step setup process one of these steps lets you enable internet connection sharing.

---

### Post by mAkKoOo210 on 2007-06-04
well I installed firestarter, but during the configuration it asked me which is the network device, if eth0 or ppp0. I connect through an Usb Adsl modem, and I'm in a lan network using a crossed cable. which is the device I use to connect to the internet? and to the Lan?

---

### Post by mAkKoOo210 on 2007-06-04
Firestarter says that eth0 is not ready...I tried all the options in the link you gave me, but nothing seems to work.
when I type:> sudo dpkg-reconfigure dhcp3-server
then I get:
> * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                           [fail] 
invoke-rc.d: initscript dhcp3-server, action "start" failed.

What happens?

---

