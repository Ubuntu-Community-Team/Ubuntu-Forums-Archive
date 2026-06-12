---
title: "Nvidia Geforce 6100 problems"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Sio on 2007-03-21
I am running Ubuntu Edgy 6.10 and I can not get the damn thing out of 600x480.... im going to need detailed instructions because i am very new to linux. I believe I have found the drivers through Automatix but i believe it is something to do with the xorg which i know nothing about yet. Could someone please give me some help?

---

### Post by overdrank on 2007-03-21
> **Sio said:**
> I am running Ubuntu Edgy 6.10 and I can not get the damn thing out of 600x480.... im going to need detailed instructions because i am very new to linux. I believe I have found the drivers through Automatix but i believe it is something to do with the xorg which i know nothing about yet. Could someone please give me some help?

Hi and welcome if you go to applications,accessories,terminal  and type in this command  sudo dpkg-reconfigure xserver-xorg  you can then add the resolution you want. Also you want to go to the screen resolution under system, preference and make sure that the check box for default is not checked. Hope this helps good luck!

---

### Post by Pizarro on 2007-03-21
I had trouble getting my geforce nvidia card to work but I installed Envy from the web site here [url]http://www.albertomilone.com/nvidia_scripts1.html. It did everything for me and gave a geforce control panel as well as sorting out the drivers.:)

---

### Post by Sio on 2007-03-22
still no luck

---

### Post by NikoC on 2007-03-22
Perhaps posting the contents of your xorg.conf file might shine a light on the problem(s) you are facing! Open a terminal and do:

gedit /etc/X11/xorg.conf

Post the contents of the file here!

---

