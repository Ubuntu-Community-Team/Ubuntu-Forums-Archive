---
title: "Macbook touchpad and keyboard don't work in software but ok in Bios"
date: 2017-03-29
forum: Apple Hardware Users
---

### Post by matthekc2 on 2017-03-29
Macbook touchpad and keyboard don't work in software but ok in Bios and on liveusb  It was probably either an update, I recently rebooted after one, or some people said booting with a usb device in can cause this issue.   I did that as well, but I would guess the usb problem would be a hardware issue.  I have an external mouse and it works fine and I can use the onboard software keyboard to enter commands so hurray for that :) I tried adding noefi acpi=on in the kernel boot params and updating grub cause someone said that worked for them.  This did not work for me... Any suggestions?

---

### Post by matthekc2 on 2017-03-29
The left shift doesn't seem to let me into grub to pass parameters either... so I don't think it's the display server.

---

### Post by matthekc2 on 2017-03-29
Changed my default kernel to the old version... it works now.  First, make a backup copy of /etc/default/grub. In case something goes wrong, you can easily revert to the known-good copy.  sudo cp /etc/default/grub /etc/default/grub.bak  Then edit the file using the text editor of your choice (ie. gedit, etc.).  sudo gedit /etc/default/grub  Find the line that contains GRUB_DEFAULT - this is what you'll want to edit to set the default. You must know the full name of the kernel you want - e.g. Ubuntu, with Linux 3.13.0-53-generic - along with the full name of the "advanced menu" - e.g. Advanced options for Ubuntu.  You then combine those two strings with > and set GRUB_DEFAULT to them as: GRUB_DEFAULT="Advanced options for Ubuntu>Ubuntu, with Linux 3.13.0-53-generic" (including quotes).  Save it, then build the updated grub menu.  sudo update-grub

---

### Post by matthekc2 on 2017-03-29
2015 retina mac no keyboard touchpad after update... look here :)

---

