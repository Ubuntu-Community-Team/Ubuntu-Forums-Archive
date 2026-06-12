---
title: "Printer Sharing"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by micrologix on 2006-04-03
Can someone please tell me how to share a printer in Ubuntu using KDE, thanks.

---

### Post by greenstar on 2006-04-04
I am currently attempting the same thing in gnome. Should be much the same for you, aside from the name of your text editor.

I found this in the Wiki under: [**Wiki Front Page**]("https://wiki.ubuntu.com/") -> scroll down to **Resources** heading & click [**User Documentation**]("https://wiki.ubuntu.com/UserDocumentation") -> scroll down to **Hardware & Drivers** heading & click [**Printers**]("https://wiki.ubuntu.com/Printers") -> scroll down to **Sharing Printers** heading & click [**NetworkPrintingFromWindows**]("https://wiki.ubuntu.com/NetworkPrintingFromWindows") where you will find instructions for Sharing your Ubuntu printer with your Windows machines via LAN.

The commands given are for Gnome, so for KDE simply use **kwrite** wherever you see **gedit** in the instructions.

Example:
(borrowed from NetworkPrintingFromWindows page in Wiki)

> 3) Modify /etc/cups/cupsd.conf with your favourite editor (the following examples use gedit)

```
sudo gedit /etc/cups/cupsd.conf
```

In this portion of the instructions, you will change the code to:

```
sudo kwrite /etc/cups/cupsd.conf
```

etc...

Hope this helps, let us know how it goes for you.

Greenstar

---

### Post by greenstar on 2006-04-04
Success!:-D  I actually got a Canon S300 (notoriously resistant to Linux & Ubuntu - driver issue) working well and shared over my LAN, and can print to it from Windows PC's, now to go test printing from my Ubuntu boxes. 

FYI - I installed my S300 with the New Printer button found at System->Administration->Printing. I installed it as a BJC-8200 using the 'BJC-8200' driver, NOT the 'BJC 8200' driver. Be careful, the driver names differ only in the dash or lack thereof. 

Greenstar

---

### Post by micrologix on 2006-04-08
[QUOTE=greenstar]I am currently attempting the same thing in gnome. Should be much the same for you, aside from the name of your text editor.

I found this in the Wiki under: [**Wiki Front Page**]("https://wiki.ubuntu.com/") -> scroll down to **Resources** heading & click [**User Documentation**]("https://wiki.ubuntu.com/UserDocumentation") -> scroll down to **Hardware & Drivers** heading & click [**Printers**]("https://wiki.ubuntu.com/Printers") -> scroll down to **Sharing Printers** heading & click [**NetworkPrintingFromWindows**]("https://wiki.ubuntu.com/NetworkPrintingFromWindows") where you will find instructions for Sharing your Ubuntu printer with your Windows machines via LAN.

The commands given are for Gnome, so for KDE simply use **kwrite** wherever you see **gedit** in the instructions.

Example:
(borrowed from NetworkPrintingFromWindows page in Wiki)



In this portion of the instructions, you will change the code to:

```
sudo kwrite /etc/cups/cupsd.conf
```

etc...

Hope this helps, let us know how it goes for you.

Greenstar[/QUOTE]


Thanks for the info, it worked fine :)

---

### Post by greenstar on 2006-04-09
Originally posted by **micrologix**

>  Thanks for the info, it worked fine :smile:

You're welcome. I enjoy helping out when I can.

Greenstar

---

