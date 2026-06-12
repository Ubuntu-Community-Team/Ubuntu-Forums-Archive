---
title: "Wireless PCI card install"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by abbrew on 2006-05-03
I am trying to get  D-Link wireless card to work.  I checked the wiki and see that it should work out of the box.  I watched my friend install this same card a little while ago on his ubuntu system, but he clicked on windows device configure or something odd like that.  I just can't find that on any of my menus.  I think this card should take a simple click of an activation button or something like that from what I can remember from my friend's install.

---

### Post by Sandlst on 2006-05-03
[QUOTE=abbrew]he clicked on windows device configure or something odd like that.  I just can't find that on any of my menus.[/QUOTE]
I'm pretty sure the program he used was ndiswrapper or ndisgtk, to get it you can open a terminal (Applications/Accessories/Terminal) and put in:```
sudo apt-get install ndisgtk
``` After it is installed, you can start it by going in under (System/Administration/Windows Wireless Drivers)  On the driver cd that came with your card (for windows) there is a .inf file somewhere on the cd, put your cd in, then when installing a new driver from ndisgtk, browse to /meida/cdrom/ and search for the .inf file.  After selecting it, the driver should show up in the window, with a 'Hardware Present: Yes' line under it.  If that works, going to (System/Administration/Networking) you should find the wireless card listed.

This method should work if you have some type of internet connection at present; if not, I think the packages to install are on the installation cd-if you need to do this, go under (System/Administration/Synaptic Package Manager) click edit; then add cd-this should allow the following instructions work even without an internet connection, good luck!

---

### Post by abbrew on 2006-05-04
Thanks.  The card is showing on the network devices list now.  I think I need to do something with my router though because Firefox isn't loading webpages.  But thank you very much for your help I'm glad to get it working.

---

