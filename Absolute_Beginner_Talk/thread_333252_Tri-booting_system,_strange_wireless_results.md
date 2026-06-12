---
title: "Tri-booting system, strange wireless results"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Risotto on 2007-01-07
A couple of days ago, I decided to try out Edgy and Fedora Core 6 :???:  as I'm starting to get more confident with Linux.

I tri-partitioned my hard drive and have the three sitting nicely alongside each other, booting happily.  :cool: 

Dapper still connects to the internet via my wireless card and my BT Home Hub but the other two OSes won't.  I've set up the wlan0 on Edgy exactly the same as Dapper, but nothing.

Any help much appreciated.

---

### Post by orb9220 on 2007-01-07
Are using network-manger applet in edgy? If you are for mine which is a atheros chip based d-link gwl-510b wireless card. I had to go to a term and gksudo gedit /etc/network/interfaces
and comment out all the lines except the first line which is auto lo like this:

> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

and reboot then it works for me. I have to do this everytime I do a clean install.
For Fedora Core 6 I don't know. 

Sorry couldn't be more help.

---

### Post by Risotto on 2007-01-07
Many thanks Orb.

I looked in the interfaces file and realised that the wireless password was incorrect (it was hidden in the network manager).  Doh!!!

So Edgy's working now!  I'll see if it's the same problem with Fedora and if not, I'll stick to Ubuntu I think!!

Thanks again.

---

### Post by Risotto on 2007-01-07
Oh no, it's still not working correctly in Edgy.  I've tried to update several times using 

> sudo apt-get update

and it freezes for no apparent reason part way through.  Synaptic does the same.

---

