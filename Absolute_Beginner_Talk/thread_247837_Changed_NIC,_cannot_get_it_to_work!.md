---
title: "Changed NIC, cannot get it to work!"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by TeknikL on 2006-08-31
Hey,

I changed the network card in my machine, to a 3com from a AMD PCnet32. The machine of course doesn't see the new NIC. I tried modprobing 3c59x but it doesn't work. Is there a network config script somewhere on ubuntu server that can probe and install the new nic?

This is the latest ubuntu server from the web.

Thanks,

Mike

---

### Post by monktbd on 2006-08-31
Can you see the NIC when you type
> 
lspci

This command lists all your pci devices.
If you can see it like this it also says the exact chipset, but maybe you already did all this and chose the correct chipset driver already with modprobe.

---

### Post by b_martinez on 2006-08-31
Then after the 'lspci' , if the NIC is shown, do the modprobe again, and then
the command

sudo ifconfig

which will show the configuration of all network interfaces, including the lopback. 
 You may even have to go so far as to re-boot.
Bill

---

