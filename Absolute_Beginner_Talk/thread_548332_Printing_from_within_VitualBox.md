---
title: "Printing from within VitualBox"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by avanrens on 2007-09-11
How do I use share my printer from VirtualBox running Windows XP with the  printer in the host system (tp0)

---

### Post by bsharp on 2007-09-13
I have never done this before because i have never tried printing from virtualbox, but I imagine that you would set up a printer share in Ubuntu and add a networked printer to the XP virtual machine like you would for a separate comp.

---

### Post by stinger30au on 2007-09-13
i thought when you open up the Virtual box progam, you can configure certain aspects of it like what usb devies etc to use.
isnt there an option to let you select your host printer as default printer?

---

### Post by getmeoutofhere on 2007-09-13
.

---

### Post by getmeoutofhere on 2007-09-13
At a guess, you first have to capture the relevant USB port, via the settings on VirtualBox.  Then install the printer on Windows - presumably it's not going to recognise the Ubuntu settings? However if Windows captures the USB port, it presumably won't be available to Ubuntu?

---

### Post by Jose Catre-Vandis on 2007-09-13
And what if you have a network printer and you can only get your VMs working with NAT?

---

### Post by avanrens on 2007-09-13
The USB icon for the printer is grayed out. I think this because Linux has the USB port mounted. In Virtual Box ver 1.4 I was able to print but in ver 1.5 it's grayed out. I might have unmount the particular USB but I don't have a clue how to that.

---

### Post by jba6511 on 2007-09-13
i had to add a new filter under device filters and it recognized it. I also had to create a usbfstab user and then give them permission to use the device first. More info on this can be found with a search.

---

### Post by avanrens on 2007-09-14
I found out how to do it here:
[http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04](http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04)

---

