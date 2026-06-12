---
title: "How do you share a ubuntu printer for winxp users?"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Lameboy on 2006-10-25
Hi guys, I'm new to ubuntu.

I managed to install a samsung printer on ubuntu, it works and i can print from ubuntu. I now have 5 winxp pro users that want to print to the printer. How do i share a printer in ubuntu so that they can add it in theyre printer list and print to it?

If possible, no command lines please. 
Tx! This is a great site!

---

### Post by HereInOz on 2006-10-25
All I did was to make the /etc/cups/cups.d/ports.conf file read like this:

#Listen 127.0.0.1:631
Listen *:631
Listen /var/run/cups/cups.sock

You then go to the XP boxes and set up the printer as an internet printer, using the IP address of your ubuntu box and telling the xp boxes what port to look for, in this case 631.  Example, if the IP address of your Ubuntu machine is, say, 192.168.1.25:

[http://192.168.1.25:631](http://192.168.1.25:631)

Make sure that your firewall is appropriately configured for the other machines to access your Ubuntu box as well.  Firestarter can help with this if you are unsure about IP tables.

Post back if you have any difficulties.

You may have to install drivers for the printer on each XP box, as well.

---

### Post by Lameboy on 2006-10-25
Wow HereInOz!!!!

You make it look so simple, tx for the detailed reply!

[COLOR="Navy"]#Listen 127.0.0.1:631
Listen *:631
Listen /var/run/cups/cups.sock[/COLOR]

The 127.0.0.1 is that yust a default adress or would that be the ip of your ubuntu machine?

[COLOR="navy"]All I did was to make the /etc/cups/cups.d/ports.conf file read like this:[/COLOR]

[COLOR="Black"]I can only find /etc/cups/[/COLOR]
Then there is a "cupsd.conf" is that the one i need to edit?

Sorry, i feel like a idiot..:(

---

### Post by Lameboy on 2006-10-25
Any body else got some advice?

Plz guys!!!:confused: :confused: :confused:

---

### Post by HereInOz on 2006-10-25
The cups.d directory should be in the /etc/cups directory.  If there is not a cups.d directory that contains ports.conf then I am a little bemused.

Are you running Dapper or Breezy?

It was different in Breezy, but in Dapper, there should be a cups.d folder and that should contain a ports.conf file.

Sorry I can't be of more assistance.

---

### Post by robinl on 2006-10-26
cupsd.conf is the file you want. Remember to modify firestarter/iptables if you have set them.

---

