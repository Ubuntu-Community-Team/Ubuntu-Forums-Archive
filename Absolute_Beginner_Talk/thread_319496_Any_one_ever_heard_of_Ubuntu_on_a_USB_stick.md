---
title: "Any one ever heard of Ubuntu on a USB stick?"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2006-12-15
Is it easy to do? Is there a specific distro based on ubuntu for this?

---

### Post by ciscosurfer on 2006-12-15
> **systemintheglitch said:**
> Is it easy to do? Is there a specific distro based on ubuntu for this?DSL can do this: [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

I just found this, though: [http://nsaunders.wordpress.com/2006/11/06/a-usb-stick-grub-and-ubuntu/](http://nsaunders.wordpress.com/2006/11/06/a-usb-stick-grub-and-ubuntu/)

Good Luck!  Post back your experience here when you've done it.  I'd like to know how it goes!

---

### Post by TheOtherLinuxFreak on 2006-12-15
i tried dsl and i like it!! it can run inside windows or linx!

---

### Post by systemintheglitch on 2006-12-15
Yah.. but i need gnome.
Someone should make a slimmed down Ubuntu distribution, where you can use synaptic to add whatever apps you want onto the usb.

---

### Post by TheOtherLinuxFreak on 2006-12-15
does dsl-n have gnome?[http://www.damnsmalllinux.org/dsl-n/]("http://www.damnsmalllinux.org/dsl-n/")

Edit: it doesnt have gnome

---

### Post by bodhi.zazen on 2006-12-15
[How to Install Ubuntu to USB](http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html)

---

### Post by ciscosurfer on 2006-12-15
> **systemintheglitch said:**
> Yah.. but i need gnome.
Someone should make a slimmed down Ubuntu distribution, where you can use synaptic to add whatever apps you want onto the usb.You can use [Recontructer]("http://reconstructor.aperantis.com/") to create any rollout you desire.  And the link I provided to you before worked great for me.  Here it is again: [http://nsaunders.wordpress.com/2006/11/06/a-usb-stick-grub-and-ubuntu/](http://nsaunders.wordpress.com/2006/11/06/a-usb-stick-grub-and-ubuntu/)

---

### Post by DoorGunner on 2006-12-16
I found something interesting....It could be a red hearing in all this but I thought i would throw it out anyways.

I  bought a Memorex 1G TravelDrive. It did a weird thing. When I plug it in it pops up with a the normal memory stick icon. However, it also pops up with an extra "cd rom" drive partition every time it is plugged in. 

So with a set of drivers it may be able to fake itself out as a cd rom. Im not sure if it would be seen by the bios for startup purposes. Or perhaps it may not see any usb ports until startup is underway.

Just thinking :-k

---

### Post by skirkpatrick on 2006-12-16
All USB sticks with the U3 mark will look like a CD-ROM drive besides the standard USB drive.  Not sure if you can use that to your advantage or not, I was so ticked off about not being able to disable the CD-ROM drive portion that I took mine back and got a different one.

---

### Post by systemintheglitch on 2006-12-16
> **ciscosurfer said:**
> You can use [Recontructer]("http://reconstructor.aperantis.com/") to create any rollout your desire.  And the link I provided to you before worked great for me.  Here it is again: [http://nsaunders.wordpress.com/2006/11/06/a-usb-stick-grub-and-ubuntu/](http://nsaunders.wordpress.com/2006/11/06/a-usb-stick-grub-and-ubuntu/)

At the end of that tutorial, it says to "grab an iso image".

What do i do with this image.. Do i burn it to a cd, then put the cd into the drive when i boot up to the memory stick? It says that it will "find" the iso image.. What if that image is just sitting onmy desktop? How can it find it no matter where it is? That was unclear. Can you help?



Also, I can't delete a partition because it says none is selected.. And i cant figure out how to select them!!

---

### Post by systemintheglitch on 2006-12-16
> **systemintheglitch said:**
> At the end of that tutorial, it says to "grab an iso image".

What do i do with this image.. Do i burn it to a cd, then put the cd into the drive when i boot up to the memory stick? It says that it will "find" the iso image.. What if that image is just sitting onmy desktop? How can it find it no matter where it is? That was unclear. Can you help?



Also, I can't delete a partition because it says none is selected.. And i cant figure out how to select them!!


Can anyone help me understand what to do?

---

### Post by bodhi.zazen on 2006-12-17
Download an Ubuntu .iso file and copy it to your USB stick.

So you have copied and configured GRUB on your USB stick, copied “boot.img.gz”, “vmlinuz”, “initrd.gz” and copy to the root directory of the stick, now download an ubuntu iso....

from here: [http://www.ubuntu.com/products/GetUbuntu/download](http://www.ubuntu.com/products/GetUbuntu/download)

Pick a version :

6.06 = Dapper = LTS (Long Term Support)

6.10 = Edgy = Newer version. May be less stable.

Pick a mirror from the list......

Boot to your USB stick......

---

### Post by systemintheglitch on 2006-12-17
> **bodhi.zazen said:**
> Download an Ubuntu .iso file and copy it to your USB stick.

So you have copied and configured GRUB on your USB stick, copied “boot.img.gz”, “vmlinuz”, “initrd.gz” and copy to the root directory of the stick, now download an ubuntu iso....

from here: [http://www.ubuntu.com/products/GetUbuntu/download](http://www.ubuntu.com/products/GetUbuntu/download)

Pick a version :

6.06 = Dapper = LTS (Long Term Support)

6.10 = Edgy = Newer version. May be less stable.

Pick a mirror from the list......

Boot to your USB stick......


Do you copy the iso onto the root directory? Where do you put it?

---

### Post by systemintheglitch on 2006-12-17
> **bodhi.zazen said:**
> Download an Ubuntu .iso file and copy it to your USB stick.

So you have copied and configured GRUB on your USB stick, copied “boot.img.gz”, “vmlinuz”, “initrd.gz” and copy to the root directory of the stick, now download an ubuntu iso....

from here: [http://www.ubuntu.com/products/GetUbuntu/download](http://www.ubuntu.com/products/GetUbuntu/download)

Pick a version :

6.06 = Dapper = LTS (Long Term Support)

6.10 = Edgy = Newer version. May be less stable.

Pick a mirror from the list......

Boot to your USB stick......


Also, I don't know how to select a partition on my usb stick to delete.
When i press d, it says none selected (in fdisk).

---

### Post by msak007 on 2006-12-17
Not sure about Ubuntu, but there is a site called [Pen Drive Linux]("http://pendrivelinux.com/") that has tutorials on installing a number of Linux distros on a thumb drive / USB flash drive. Ubuntu is not one of them though.

---

### Post by r4ik on 2006-12-17
Mandriva has one,

[http://www.mandriva.com/en/individuals/products/node_3482](http://www.mandriva.com/en/individuals/products/node_3482)

---

### Post by bodhi.zazen on 2006-12-17
> **systemintheglitch said:**
> Do you copy the iso onto the root directory? Where do you put it?

As far as I can tell put the Ubuntu iso onto the usb device....

---

### Post by systemintheglitch on 2006-12-17
> **bodhi.zazen said:**
> As far as I can tell put the Ubuntu iso onto the usb device....



Ummm.. I don't know what that meant. I could put that iso file on the usb disk in many places.. I'm saying i don't know where to put it. Which directory?

Are you trying to say: "it does not matter which directory" ?

Thanks

---

### Post by Frank Golden on 2006-12-17
> **skirkpatrick said:**
> All USB sticks with the U3 mark will look like a CD-ROM drive besides the standard USB drive.  Not sure if you can use that to your advantage or not, I was so ticked off about not being able to disable the CD-ROM drive portion that I took mine back and got a different one.
[http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html](http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html)

[http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)

[http://cse.msstate.edu/~rwm8/hackingU3/](http://cse.msstate.edu/~rwm8/hackingU3/)

 See above for info and tool to remove the CD partition and restore a U3 drive to a normal drive.

---

### Post by Frank Golden on 2006-12-17
> **systemintheglitch said:**
> Is it easy to do? Is there a specific distro based on ubuntu for this?It is easy to install the liveCD of Ubuntu to a flash drive, in persistent mode. You need a 1GB or bigger drive and your computer needs to be able to boot to USB flash drive.

See this tutorial for complete info
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29)

When done properly when you boot to the USB flash drive it behaves exactly like the Live CD only much faster. Changes made such as adding favorites to Firefox etc will be saved when you close down your Live cd session.

It isn't too difficult, just follow the directions exactly.

---

### Post by skirkpatrick on 2006-12-18
> **Frank Golden said:**
> [http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html](http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html)

[http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)

[http://cse.msstate.edu/~rwm8/hackingU3/](http://cse.msstate.edu/~rwm8/hackingU3/)

 See above for info and tool to remove the CD partition and restore a U3 drive to a normal drive.

Thanks.  I was looking for such information way back when they first came out and couldn't find anything.

---

### Post by DoorGunner on 2006-12-18
Thank you for your reply.... I intend to remove mine

---

