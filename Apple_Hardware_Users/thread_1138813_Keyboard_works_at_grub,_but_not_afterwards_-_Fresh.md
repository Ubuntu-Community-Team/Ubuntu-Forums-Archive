---
title: "Keyboard works at grub, but not afterwards - Fresh 9.04 install"
date: 2009-04-26
forum: Apple Hardware Users
---

### Post by sunbird on 2009-04-26
Hi all,

I've been struggling to get my fresh install of 9.04 working. I'm running luks for crypted / and swap. Install went fine and keyboard worked, on reboot, keyboard works to get to grub menu, but on prompt for passphrase, no dice.

I've got a macbook pro 3,1. 

Ideas?

Thanks!

---

### Post by Salohcin on 2009-04-27
Same thing happened for me when i copied the fdi file for the synaptics off of the mactel documentation site.  I had to boot into console to remove and then go looking to see where the fault was.  I found some bug reports that seemed to follow the same problem, and they had an alternate fdi attached.  

Don't know exactly how relevant any of this is to you, but if it helps, i'll attach the file im using now.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/337935]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/337935")

---

