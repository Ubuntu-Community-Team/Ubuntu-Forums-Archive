---
title: "networking and shared printer"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by susbut on 2006-05-10
I have recently converted to ubuntu after 20 years of being a windows user. I am absolutely happy to join the community and have not had any serious problems whatsoever. There is two things though - that I can't get going. In my family we have 3 computeres on a local network. The 2 are windowsusers and then me. my internet connection works perfectly through the router. But i cannot establish my computer as part of the network, they cannot see me, and I cannot see them. The printer is connected to my computer, and used to be shared, so the others could use it. I don't know how to share the printer in Ubuntu. I would be very happy to receive some help in these matters - which would mean, that my happiness about linux will reach the top.

---

### Post by skippy81 on 2006-05-10
Maybe your workgroup name isnt set up correctly. First make sure you have samba installed. Use a terminal (Applications > Accessories) and type in 

>  sudo apt-get install samba

Retrieve the name of the workgroup from one of your windows PCs.  If it is MSHOME, then don't bother with these steps:

Open a terminal window and type:
> sudo gedit /etc/samba/smb.conf

Scroll down a bit and change "MSHOME" to the name of your workgroup, then hit save.  

Next restart samba

> sudo /etc/init.d/samba restart

Then try and access the windows PCs through "network servers" under the places menu.

---

### Post by adam.tropics on 2006-05-10
Thw wiki is an invaluable thing, put it in your favourites!!

[The printer thing!]("https://wiki.ubuntu.com/NetworkPrintingWithUbuntu")

For the rest of the Ubuntu - Xp networking stuff, see if you have Samba installed, if not, then fire up Synaptic and install it, and search the Breezy Desktop forum for help setting it all up....Many have been here before you, trust me!

---

### Post by susbut on 2006-05-12
Thank You very much for very usefull advice. I moved the printer to a Windows pc, and followed instruktions. In a matter of 20 minutes printer and network was up and running. Ubuntu had no problems in detecting printer and network places. The wiki will be one of my favourites for sure. I am very happy to be here.

---

### Post by ed_d on 2006-05-12
Wiki looks easy enough, but if you have 2 PCs in the house, on the network, do you just configure the Ubuntu as the printserver alone, and it will still print like normal?

---

