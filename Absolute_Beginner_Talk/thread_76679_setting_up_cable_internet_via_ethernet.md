---
title: "setting up cable internet via ethernet"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by gregnorc on 2005-10-15
How would I do this? I'm using a thinkpad 600e with a Netgear FA511 10/100 Mbps wired ethernet card. I unplugged my network cable from my windows box and plugged it into the laptop, but when I try and go online, use apt-get, etc, it doesn't work.

How would I set this up? I tried google with no luck.

Sorry for the crosspost, I didn't notice there was a specfic beginner's board earlier.

---

### Post by Skid on 2005-10-15
Hi,

If your cable modem/router runs a DHCP server, then try the following command to gain an IP lease:

```

sudo dhclient eth0

```

(Presuming your NIC is showing as eth0, which generally it will be.)  When prompted for a password, enter your current *users* password.

---

### Post by John.Michael.Kane on 2005-10-15
Type sudo pppoeconf enter your username then pass. use this method if your ip is not static based. 

to disconnect from the net typ sudo poff.. 


hope that helps

---

### Post by gregnorc on 2005-10-15
Ok, sudo dhclient eth0 that in terminal and got an error: 

etho0:error while getting interface flags: no such device
etho0: error while getting interface flags: no such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device

About to try that ppp thing...

Got this error: Sorry, I scanned your 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for the scan failure may be another running process which controls the modem

---

### Post by Samuel on 2005-10-15
did you reboot your cable modem? mine needs to be restarted when i connect it from one PC to another, just a thought ;)

---

