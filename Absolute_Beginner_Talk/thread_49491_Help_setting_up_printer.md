---
title: "Help setting up printer"
date: 2005-07-16
forum: Absolute Beginner Talk
---

### Post by freakzilla on 2005-07-16
Please help direct me on how to install a printer on my ubuntu system.  I'm new to linux, although i did try fedora core 2, so you'll have to keep the directions simple.  

The usb printer is a HP deskjet 832C and it is connected to my LAN through a DLink DP-301U print server so my XP laptop can also have access.  I've assigned the printer a static ip ***.***.*.***.

I tried >system>administrator>printing to setup in ubuntu.  I installed the suggested hpijs driver. I tried selecting cups network printer under connection tab and entering the printer IP address in the URI field.  While printing a test page I get the status message "Ready: Network host '***.***.*.***.' is busy; will retry in 30 seconds..."

Other than this difficulty i've had no problems with ubuntu.  Everything has been smooth to setup.

Thanks

---

### Post by freakzilla on 2005-07-19
Any ideas?

---

### Post by aysiu on 2005-07-19
Have you tried installing it as a local printer (USB instead of serial port), not as a network printer?

---

### Post by freakzilla on 2005-07-23
Thanks for the suggestion.

I used these settings:

- Select "Network Printer" and select "Unix Printer" as the type. (instead of default "CUPS")
- In the "host:" box, type the IP address of the print server. Queue set to "lp" (lower case) for my dlink.
- Select the Printer manufacturer and the model from the lists.

This thread might be useful to other people with the same question and Dlink print servers. "http://www.ubuntuforums.org/showthread.php?t=32692" 

I'm really starting to use ubuntu more than xp.  Transition isn't the smoothest but pretty fun to learn as you go. \\:D/

---

### Post by courtier on 2007-07-18
I think this may help you if, like me, your printer is working from a windows network through a printer server like the D-Link DP-301U.

I have three windows computers using a D-Link DP-301U network printer port to share a Samsung ML-1210 printer. To connect an ubuntu linux portable to use the same printer on the windows network I did the following using gnome, but only after considerable trial and error:

1) System-Administration-Printers-New Printer
2) Printer Type Radio button-network printer-Drop Down Box-TCP/Socket, HP Direct, Raw Connection
Forward
3) Host 192.168.0.7 (in my case more commonly 192.168.0.10, and I could not use the d-link port name)
4) Port 2100 (entered for me but agrees with d-link web browser setup page)
Forward
5) Select manufacturer of printer from Drop Down Box
6) Select Model from list or use a disk
Forward
7) Choose name-description-location
Apply
Your printer will appear as ready in the Printers window

To alter these settings with immediate effect right click on your printer and use properties-connection

It took me a while to work this out but then I am a newbie

---

