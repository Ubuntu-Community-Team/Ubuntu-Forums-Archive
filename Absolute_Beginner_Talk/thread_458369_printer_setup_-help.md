---
title: "printer setup -help???"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by mcmillanje on 2007-05-29
I have a qms magicolor 3100 attached to my pc through a network gateway over ethernet. I can't seem to figure out how to set it up.

I know i can access its internet pull printing page through my browser with 192.168.0.5 (slot five on gateway)

do I set it up as cups ipp://192.168.0.5 ? or ipp://192.168.0.5/magicolor 3100/ ? or something else? I'm completely lost.


edit: I run studioubuntu (feisty), with fluxbox (but still can use gnome...) if that matters.

---

### Post by drs305 on 2007-05-29
I don't use it any longer, but I once had a similar setup and as I recall had it designated as:
ipp://192.168.0.5/printers/Laserjet-1000

I am certainly no expert in printers. One thing I noticed in your post -  there is a space between magicolor and 3100. If you are not getting it to work you probably need to eliminate the space. I looked it up in CUPS and the printer is designated as:  magicolor-3100

Good luck.

---

### Post by mcmillanje on 2007-05-29
thx for the help, but I still can't make it work
in properties when trying to print it says:
Printing: Network host '192.168.0.5' is busy; will retry in 30 seconds...

I don't really understand it... maybe I'll check out the minolta site...

---

### Post by mcmillanje on 2007-05-29
ok, I found the minolta docs, and they said I should use:
ipp://<ip>:80/<name>
and that if the name had a space in it (it did) I should rename it,
I did this using a postscript file like they said,

but ipp://192.168.0.5:80/magicolor-3100 still doesn't work...

---

### Post by Iokua on 2007-05-29
Have you taken a look at the [Network Printing community documentation]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")? It's a great resource.

---

### Post by drs305 on 2007-05-29
I dug up my old notes. Here is how I initially set up my ipp:

```
sudo aptitude install cupsys cupsys-client
```
```
sudo cp /etc/cups/cupsd.conf /etc/cups/cupsd.conf.backup	# Create backup copy of cupsd.conf
```
```
gksudo gedit /etc/cups/cupsd.conf
```
		Edit and add:
		#MyAddition  (Find IP address via  command: ifconfig )
		Listen 192.168.0.5:631	# Listen on the LAN interface, Port 631 (IPP); select appropriate IP add.
```
sudo /etc/init.d/cupsys restart		# CUPS must be restarted for changes to take effect
```
Add printer address:	(Syst, Admin, Printers, New Printer, Network Printer) 
		ipp://192.168.0.5/printers/SuperScript-870

Of course, you would have to change the IP address I used to your own.

---

### Post by mcmillanje on 2007-05-29
well, I did read the docs, and I made sure my cupsd.conf listened to the correct ports... not exactly sure what's wrong. Ah well, I don't have time to do more tinkering today, but I'll get back at it. Thanks for the help.

---

