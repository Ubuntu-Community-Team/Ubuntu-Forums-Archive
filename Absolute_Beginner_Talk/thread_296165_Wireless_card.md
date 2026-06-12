---
title: "Wireless card"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by ordan on 2006-11-09
Hey All.

Totally new to Ubuntu, just installed the first linux system in my life. :p 

All is working well except I am not able to connect to the internet using either d-link dwl-g122 or SMC EZ connect smc2662w.

I have Ubuntu 6.10 and the cards are seeing by the computer but no connection.

Pease help...

Boaz

---

### Post by wieman01 on 2006-11-09
What's the output of (command line...):
> iwlist scan

---

### Post by ordan on 2006-11-09
boaz@Boaz-Linux:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

boaz@Boaz-Linux:~$

---

### Post by ordan on 2006-11-09
Sorry, no card was connected when i did the iwlist. Now it is and here is the outcome of the order:


boaz@Boaz-Linux:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

rausb0    Scan completed :
          Cell 01 - Address: 00:14:51:6E:26:D5
                    Mode:Managed
                    ESSID:"Ordan Extreme"
                    Encryption key:on
                    Channel:1
          Cell 02 - Address: 00:11:24:A8:78:A6
                    Mode:Managed
                    ESSID:"Ordan Extreme"
                    Encryption key:on
                    Channel:1

boaz@Boaz-Linux:~$

---

### Post by jstew on 2006-11-09
Both of those cards are USB wifi devices, correct? Unfortunately the support for these devices is not quite there yet in linux.

You could try using the windows driver with ndiswrapper:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by jstew on 2006-11-09
Hmm... looks like you're one step ahead of me. 

Could you post the output of iwconfig also? Are you associated to an AP?

---

### Post by wieman01 on 2006-11-09
Oh oh, Ralink. Good luck. The native Linux driver is a bit of a pain, but if you only need WEP (encryption) it'll be fine.

Please post the contents this file:
> sudo gedit /etc/network/interfaces
I assume your ESSID is "Ordan Extreme" and you have DHCP & WEP (encryption/authentication) enabled, correct? If you plan to use WPA, this will be somewhat tricky.
[U][B]
EDIT:[/B][/U]
Have you tried out Gnome's networking applet yet? It seems your card has been detected so the applet will do the job if you use WEP only.

---

