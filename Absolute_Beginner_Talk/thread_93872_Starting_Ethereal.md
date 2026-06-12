---
title: "Starting Ethereal"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by alanng on 2005-11-22
I am having trouble starting Ethereal. I used the Synaptic Package Manager and installed the following packages and their dependencies:

ethereal
ethereal-common
ethereal-dev
tethereal

After the installation, I have two Ethereal icons under Application --> Internet --> Ethereal and Ethereal (as root), both of which don't do anything when I clicked on them. Their command are "ethereal" and "gksudo /usr/bin/ethereal" respectively.  

I then tried to  start Ethereal from the terminal, but got the following messages:

<output>
root@raven:~# ethereal
Could not set capabilities: Operation not permitted
root@raven:~# sudo ethereal
Could not set capabilities: Operation not permitted
root@raven:~# gksudo ethereal
Could not set capabilities: Operation not permitted
root@raven:~# tethereal
Could not set capabilities: Operation not permitted
root@raven:~#
</output>

Any advice would be greatly appreciated. Thank you.
- Alan

---

### Post by ranf on 2005-11-23
[QUOTE=alanng]
I then tried to  start Ethereal from the terminal, but got the following messages:

<output>
root@raven:~# sudo ethereal
Could not set capabilities: Operation not permitted
[/QUOTE]
I think I also had that problem months ago (not sure). IIRC I've manually set eth0 into promiscous mode.

---

### Post by spoilerhead on 2005-11-23
same behavior here

but other sniffers have no problem setting the promisc mode :-/

eth0      Protokoll:Ethernet  Hardware Adresse XXXXXXXXXXXXX
          inet Adresse:XXXXXXXXX  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: XXXXXXXXXXXXX Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:12210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23009 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:8463434 (8.0 MiB)  TX bytes:2234748 (2.1 MiB)
          Interrupt:6

spoilerhead@plasmafire:~$ sudo ethereal
Could not set capabilities: Operation not permitted

as you can see, even setting promisc mode by hand doesnt work :-/
(the X'es have been added my myself :-) )

hm, when starting ethereal aos normal user:
spoilerhead@plasmafire:~$ ethereal
(the gui appears!)
open_if: socket: Operation not permitted

hm

---

### Post by ranf on 2005-11-23
I've searched around a bit. Found this on bugs.debian.org:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=321204](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=321204)

---

### Post by alanng on 2005-11-23
Sweet. Thanks for the information. Ethereal is up and running. :D
I googled this for hours and found nothing, I need better searching skills : /

---

### Post by ranf on 2005-11-23
[QUOTE=alanng]Sweet. Thanks for the information. Ethereal is up and running. :D
I googled this for hours and found nothing, I need better searching skills : /[/QUOTE]
Yeah google was not very helpful. The only hint I found in the (German) Kanotix forum. Then I went to bugzilla.ubuntu.com and searched for ethereal. Nothing.
Ok, Ubuntu is Debian based so I tried their bug tracking system. Tada.

---

