---
title: "VNC question"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2006-07-04
I want to connect remotely to my mothers PC (an XP) from my Ubuntu. First I installed VNCviewer but when I put in her IP address the connection was refused . A friend told me that in order to connectt with VNC, one PC needs to be a server and one a client (is that true?) . So I installed VNCserver on Ubuntu but when I run 'vncserver' from the terminal nothing really happens it just says :
```
New 'X' desktop is sesho:2
``` (sesho is my user name)
and when I put Ubuntu's ip address in the XP VNC client the connection is refused (160061) .Window's firewall was off at the time.
Basically what I want to know is how to connect remotely from an Ubuntu to an XP ,with the XP requiring little to no work at all (my mother only recently learned to use a mouse)
Thanks

---

### Post by ProjectGod on 2006-07-04
don't know about XP home... but XP pro has under SYSTEM PROPERTIES the REMOTE tab that allows you to enalble RDP connection from other PCs... so enable that first and add any user you wish to add... preferably the adminstrator ;) that's if your mother lets you have her PC's administrator password ;)...

use the APPLICATIONS > INTERNET > terminal server client in ubuntu to connect via an IP address... 

if you've already correctly installed VNC server on your mothers machine use the same terminal server client as above on your ubuntu to connect to XP... 
you'll have to select VNC rather than RDP for the connection type.

one more thing you may need to open up the built in XP firewall so that it allows traffic from your ubuntu machine's IP...

hope that helps! :D

---

### Post by seshomaru samma on 2006-07-04
[QUOTE=ProjectGod]

use the APPLICATIONS > INTERNET > terminal server client in ubuntu to connect via an IP address... 

[/QUOTE]

Thanks, that's what I needed

---

