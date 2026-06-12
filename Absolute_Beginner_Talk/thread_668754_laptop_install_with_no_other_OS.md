---
title: "laptop install with no other OS"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by chipboy on 2008-01-15
I have a Compaq laptop with no existing operating system and I think the cd drive is shot because I can't get Windows or Ubuntu to load from cd on it. How would I load Ubuntu from a portable hard drive I have that I can connect to the laptop USB port? The documentation I read assumes I already have Windows. Thanks.

---

### Post by blueridgedog on 2008-01-15
This site has two options:

[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

and this site has an elaboration of solution two from above:

[http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive](http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive)

Each of these looks complex and assumes you have access to another system, a working network and a TFTP server.

Perhaps others have other options.

---

### Post by chipboy on 2008-01-16
Thanks but I don't have any of those things. Is it even possible to boot from a USB? I could buy one of those $20 usb cd rom drives on ebay if that will help.

---

### Post by stchman on 2008-01-16
> **chipboy said:**
> I have a Compaq laptop with no existing operating system and I think the cd drive is shot because I can't get Windows or Ubuntu to load from cd on it. How would I load Ubuntu from a portable hard drive I have that I can connect to the laptop USB port? The documentation I read assumes I already have Windows. Thanks.

There are methods that will allow you to run the installer from a flash drive.  Only problem is does that laptop BIOS allow booting from a USB device.  If that is the case you can also connect an external CD drive to the USB.

---

### Post by chipboy on 2008-01-21
I don't think so unless a USB has to be connected for that option to show up. I'll check that next. If I can't get it to workon the laptop  is it possible to load Ubuntu on a secondary hard drive on my old desktop? I have an extra 12gb drive on there with nothing on it.

---

### Post by bobdebouwer on 2008-01-21
how big is the hard drive on the laptop?

If you have a connector connect it to the pc
then repartition with 2 partitions 1st only needs to be 700meg (i say first so that you can boot from it)
copy contents of the "live cd" to the smaller partition
plug back into laptop
boot from smaller partition
install to larger partition


You could connect either via a usb 2.5" case or mini ide to ide adapter or firewire 2.5" case, lots of options.


Finally once you have everthing installed you can either repartition or leave it incase you need to format reinstall.

David

---

### Post by chipboy on 2008-01-21
I'm sorry I'm not very computer savvy. The laptop has 80gb I think but it has no OS at all on it. I don't have anything to connect it to the old desktop with but even if I did I don't know how to partition hard drives. Are there step by step instructions anywhere? I think I'm in way over my head.

---

### Post by az on 2008-01-21
It would be simpler to remove the drive from the laptop, plug it into a usb adapter (enclosure) and install ubuntu onto it.  

Boot the ubuntu disk from another machine and tell it to install Ubuntu onto the external drive.  Tell it to put the bootloader on it, too.

Then, put the drive back into the laptop. 

You will need to boot into recovery mode and reconfigure the Graphics server:

dpkg-reconfigure -phigh xserver-xorg

You only need to do that once.

---

### Post by blueridgedog on 2008-01-21
However, that said, he could simply buy a USB cdrom versus a USB hard drive enclosure, and when the dust settled he would have Ubuntu installed and a CDROM.

They are pretty cheap: 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827106097](http://www.newegg.com/Product/Product.aspx?Item=N82E16827106097)

(even for a CD/DVD burner)

---

### Post by chipboy on 2008-01-21
My bios doesn't allow me to boot from a usb though.

---

