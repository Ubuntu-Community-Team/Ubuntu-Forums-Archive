---
title: "Ubuntu install does not recognise RAID array."
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by Seb Spiers on 2005-08-21
I have a raid0 array inmy machine running on an Adaptec ATA 1200A RAID controller card.

When I boot from the install CD it simply shows me the disks on the controller, not the array.

I am asuming this is because it does not have the correct drivers, but I am unsure how to a) aquire the correct drivers & b) use the drivers during the installation process.

I have data on the array (windows installation, data, etc) and have left a 80Gb area free for Ubuntu so I dont want to lose the array.

Newbie walkthrough would be much appreciated. :)

---

### Post by Seb Spiers on 2005-08-22
](*,)

---

### Post by poofyhairguy on 2005-08-22
[QUOTE=Seb Spiers]

I am asuming this is because it does not have the correct drivers, but I am unsure how to a) aquire the correct drivers & b) use the drivers during the installation process.
[/QUOTE]

I'll be honest....when drivers for a device in Linux exist, they work out of the box. This simply means that currently UBuntu will not work with that device.

Don't panic though, there is hope. Download the Breezy live CD:

[http://cdimage.ubuntulinux.org/releases/breezy/colony-2/](http://cdimage.ubuntulinux.org/releases/breezy/colony-2/)

See if that sucker works for you. Then download the installer and see if the breezy can use the hardware. Breezy has a much newer kernel with tons of new drivers, it just might work. Then if it works either:

A. Install Breezy on there and deal with some bugs till its released (october)

B: Wait till Breezy is released. 

I helped the best I can, I wish I could do more. Have a nice day.

---

### Post by Seb Spiers on 2005-08-22
[QUOTE=poofyhairguy]Download the Breezy live CD:

[http://cdimage.ubuntulinux.org/releases/breezy/colony-2/](http://cdimage.ubuntulinux.org/releases/breezy/colony-2/)

See if that sucker works for you.[/QUOTE]What is breezy?  I want to use ubuntu :(

---

### Post by Seb Spiers on 2005-08-24
Ok I tried breezy.  That didnt see my array either! :(

---

