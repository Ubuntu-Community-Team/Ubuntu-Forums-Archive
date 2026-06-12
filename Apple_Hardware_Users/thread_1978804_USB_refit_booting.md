---
title: "USB refit booting"
date: 2012-05-12
forum: Apple Hardware Users
---

### Post by Garrett_44 on 2012-05-12
Hi

I've managed to install Ubuntu on a usb stick and made it bootable on a mac mini via the refit boot loader.  I used a live cd to do this and also installed a ubuntu partition on the mac mini at the same time.  Everything seemed to go fine.  I reboot get my efi menu with four options, OSX, Linux on HD (mac mini hd icon), Linux on HD (usb hd icon) and Legacy OS.  Choosing ether Linux works fine. 

Testing the usb ubuntu installation on another mac, I installed refit boot loader and booted into it which was fine but the changes I made had not carried across (i left a txt file on the desktop).  I thought this was persistence but it's not, if I mount the usb drive on the first mac booted into ubuntu on the hard drive I can see my text file in my profiles desktop on the usb drive so what seems to be happening is the first mac prefers to boot into the macs hard drive ubuntu installation even though I choose the usb one - what's going on here?  It must be something small if I can boot fine on the second mac.

Garrett

---

### Post by Garrett_44 on 2012-05-14
Bump, still stuck with this issue.

---

### Post by DoubleClicker on 2012-05-16
Can you give a little more info:

What's the models number on the macmini?
what''s the model nuberon the second mac?
Does the USB stick have a GUID partition table (GPT) ?

where do you have grub installed on the USB stick?
where do you have grub installed on the each of the macs ?
for each install are you using grub-efi or grub-pc?

---

### Post by Garrett_44 on 2012-05-17
Hi

Thanks for replying.

>What's the models number on the macmini?
>what''s the model nuberon the second mac?

Both Mac Mini's are identical apart from the Ubuntu partition:

macmini4,1
Intel Core 2 Duo
2.4Ghz
MM41.0042.800


>Does the USB stick have a GUID partition table (GPT) ?

Yes, 1000mb Swap Partition and the remaining 7019mb Ext4 file system


>where do you have grub installed on the USB stick?

at /


>where do you have grub installed on the each of the macs ?

The rEFIt folder (called efi) is directly in the Macintosh HD where the installer put it.


>for each install are you using grub-efi or grub-pc? 	

grub-efi I think (it's the rEFIt from here: [http://sourceforge.net/projects/refit/files/rEFIt/0.14/rEFIt-0.14.dmg/download](http://sourceforge.net/projects/refit/files/rEFIt/0.14/rEFIt-0.14.dmg/download))

Garrett

---

### Post by Garrett_44 on 2012-05-21
Bump again.

---

