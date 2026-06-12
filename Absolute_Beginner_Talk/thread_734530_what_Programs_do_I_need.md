---
title: "what Programs do I need?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-03-24
AS a real newbie, I am a little confused in regard of what programs do what, and which ones I actually need. I am running Gutsy Gibbon 64 bit 

For instance, what is Samba, and do I need it to gain access to my home office network? 

My windows setup was, 

Desktop to the router via usb, 
Laptop to the router via wireless
Both computers to the HP all in one printer via wireless
Ad Hoc network with an external HD available across the network
Canon printer usb to the desktop, via the netwrok for the laptop.

Now that I have Ubuntu on the desktop (2nd HD), but not able to change the laptop over yet, I have found that

a) I cannot access the ad hoc network from the desktop
b) I cannot access the HP printer from the desktop
c) the laptop cannot access the canon printer
d) the laptop cannot access the desktop or external disk if I am on the ubuntu partition.

Is Samba the correct program to resolve these issues, and if so, where can get the approriate installation and configuration information? 

Other than that, the system is fabtastic, way faster than windows,  with so much more flexibility, even if the learning curve is a bit steep, thats what a challeneg is lol

Any assistance gratefully accepted
 :)

---

### Post by joshrobinson on 2008-03-24
samba is the windows networking protocol, smb is probably what your used to seeing it as, it lets you share folders and printers over a network

you can open, system > administration > shared folders

and it will prompt you to install samba
you can add shared folders there, and the ability to set your workgroup name

---

### Post by tropdoug on 2008-03-24
Thanks for that, I have now installed samba. Do you know how I add the printer, and connect to home network?

---

### Post by joshrobinson on 2008-03-24
so your desktop computer, that can connect to the internet fine? you said it connects to the router by usb, i wasnt sure if that was working fine

and you want the laptop and the desktop to share files and a printer?

---

### Post by tropdoug on 2008-03-24
Yes thats correct. Firefox, evolution working fine, and all packages have been updated. I was expecting something like the windows network setup, where you can add the home office network and then add individual devices to the system through the network, but cannot find anything. I have tried adding another printer, but the dialogs don't give me the options I think I need.

Currently the printer is on  its own IP address 10.1.1.2 and the router is 10.1.1.1 The network is SSID with WPA authentication. and I have all those details, but not sure how to use them in Ubuntu. 

Douglas

PS I have succesfully added the laptop to a netwrok link so I can access that.

---

