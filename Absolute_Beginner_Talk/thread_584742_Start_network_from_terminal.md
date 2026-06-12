---
title: "Start network from terminal"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by richardgundersen on 2007-10-21
Hi

I need to download a package using apt-get and (because I can't start X for various reasons) I need netork access from the terminal. If I boot into say runlevel 3, could someone tell me how to start my network connection please? 

BTW when my system used to work I had to enter a keyring password to get network access (WPA2 wireless). I think that I will need to do this from the command line somehow. 

(my system is all configured correctly apart from X being trashed so I don't think I need to configure any network stuff - I just need to get it started)

Thanks!

---

### Post by richardgundersen on 2007-10-21
I'm guessing I need to do something with iwlist and iwconfig. Basically I just need to do what Gnome normally does automatically for me. 

Pls help!:)

---

### Post by LanDan on 2007-10-21
yup,

this will be old school style for you know ;)

also try "ifconfig"

/etc/init.d/network restart   
iwconfig up
should maybe give you some clue

what do these commands tell you?

---

### Post by richardgundersen on 2007-10-21
Thanks for replying LanDan. I don't have /etc/init.d/network but I do have ./networking. I ran that, and it didnt throw any errors, but I still couldn't ping [www.google.com](www.google.com). 

'iwconfig up' wasn't recognised as a valid option unforunately. 

As an aside the reason I need the network is to reinstall libc6-dev because I think my nvidia driver's kernel interface needs rebuilding (X stopped working after the Gusty Goat upgrade). I did this manally in the end (downloaded the .deb) but I still dont get a working X.

---

### Post by LanDan on 2007-10-21
ppfff its a long time ago i did some wireless so maybe someone knows the answer faster.

but i can try to google aong with you in the meanwhile, what does iwlist say?

---

### Post by LanDan on 2007-10-21
you could also try to get a working X by using the vesa driver

dpkg-reconfigure xserver-xorg

---

