---
title: "Printer ports"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by TimCor on 2008-01-30
I have a Canon printer (driver available in Ubuntu) which (in windows) is connected by USB to a 'Wireless Linksys print server using port LK981e6f'. The print server is set up with the same SSID etc as the main Netgear router. All works well in Win XP (After changing the printer's port to the above).

In Ubuntu, if the printer is "hard wired" to a USB port on the laptop then all is well, but when used wirelessly in Ubuntu no printer is detected when Add New printer is selected and no 'ports' are shown.

What proceedure should I use, or do I need to "hard wire" my printer each time?

All the best

Tim

I have managed to get most of the OS up and running successfully on both my machines thanks to the help from these forums.

---

### Post by cmnorton on 2008-01-30
Just a guess, but it sounds like you're going to have to give this printer a reserved  DHCP or static address and then create a link through CUPS manager.

---

### Post by TimCor on 2008-01-31
Hi all

Can I just say thanks to this and the other forums for the help in setting things up on first installation.

I set up my printer on a wireless print server using [http://localhost:631](http://localhost:631) (Common unix printing system) which allowed entry in all the required areas.

I have also set up my Bluetooth mouse - which was near impossible in Windows by using the link [http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html) 

So many thanks to all for their help, Now to get using UBUNTU !!

All the best

Tim :)

---

### Post by LowSky on 2008-01-31
I did the same thing TimCor did, CUPS can manage most of the set up for wirelss ad-hoc printing. My laptop can print wirelessly to my desktop's printer with no issues.

---

