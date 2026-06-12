---
title: "List of Ubuntu config tools"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by Randy Sparks on 2005-10-03
Does anybody know where I can find a nice neat list of Ubuntu config tools, both command-line and GUI? Perhaps a website that lists them...?

TIA ;-)

---

### Post by lorenco on 2005-10-03
WebMin - Is a cool web based config tool for all distros
KConfig (If you r running Kubuntu)

---

### Post by KingBahamut on 2005-10-03
While its an erstwhile opinion, I dont recommend the use of Webmin.

What are you trying to configure? and on what level? The system? a server daemon? a program?

---

### Post by Ampersand on 2005-10-03
You can find most of the gnome config tools by opening a terminal, typing 'gnome' (don't press enter) and pressing tab twice.

---

### Post by dcraven on 2005-10-03
I'm afraid such a list would be nearly endless, and impractical. Until you get used to the Linux filesystem (there *is* structure to it, believe it or not :)), you're best bet is to ask here or Google for specifics. Linux if very powerful, and with power comes many options and configuration files.

Cheers,
~djc

---

### Post by Randy Sparks on 2005-10-03
I'm not a newbie to Linux. I'm just new to Ubuntu.

In SUSE I can control just about anything using YaST2, in Red Hat or Fedora I can type redhat-config-*blah* (or system-config-*blah*).

For example, if the screen is screwed up, what command under Ubuntu do I use to reconfigure the resolution and so on? What command do I use to configure a wireless network card? Or a printer? 

What I'm saying is that most distros have distro-specific commands to configure hardware. Does Ubuntu have a set of these and, if so, where can I find a list?

Does Ubuntu rely completly on the Gnome config tools?

---

### Post by az on 2005-10-03
Well, you can reconfigure indivicual packages:
Ex:
sudo dpkg-reconfigure xserver-xorg

---

### Post by earobinson on 2005-10-03
gnome_config is a good tool (hope i got it right not on my linux box :()

---

