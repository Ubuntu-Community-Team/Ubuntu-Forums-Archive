---
title: "Installing Ubuntu 10.04 PPC on External Harddive"
date: 2010-07-13
forum: Apple Hardware Users
---

### Post by flatlined on 2010-07-13
I'm trying to install Ubuntu 10.04 PPC on to an Western Digital External USB 1TB drive to run on a:

eMac G4
1ghz 
1GB RAM

I would like to only use like 40GB of the 1TB External. I get to the part where I can Manual edit partition tables and am lost on how to do this.

Is there a Step By Step guide somewhere or can someone help me with what to do at this step?

Thanks

---

### Post by cj.surrusco on 2010-07-13
You basically just need to do a normal install, and there's tons of articles on that. I'm assuming that no other OS's are installed on the external hard drive? 

You need to create a 40GB partition by resizing the existing partition and creating a new one in the empty space. You can do this with GParted. [*This*]("http://www.ehow.com/how_4927652_install-ubuntu-external-hard-drive.html") may help you with that step.

Then, go back to the installation and when you get to the part to manually select partitions, choose to mount / on the new partition.

---

### Post by flatlined on 2010-07-13
OK Thanks

Also what should I format the Partition as if I want to use it as a bootable drive in Disk Utility? I have it formated now as FAT32, should I format it as The extended Journal?

Thanks

---

### Post by cj.surrusco on 2010-07-13
> **flatlined said:**
> OK Thanks

Also what should I format the Partition as if I want to use it as a bootable drive in Disk Utility? I have it formated now as FAT32, should I format it as The extended Journal?

Thanks

You should format it in ext4, as that is the current standard for Ubuntu installations.

---

### Post by linuxopjemac on 2010-07-13
I am not sure whether you will be able to boot from USB. Firewire will certainly work:
[http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0](http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0)

---

### Post by flatlined on 2010-07-14
I got it installed on my USB drive, but when I turn on my Mac and hold down Alt ( I have a PC USB Keyboard) but I only see the internal harddrive OS X Operating system.

Is there anything else I can try? Should I use rEFIt?

Thanks

---

### Post by linuxopjemac on 2010-07-15
As I said, USB is possibly not a bootable device, at least not with that method. You could try from open firmware.

[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)

---

### Post by flatlined on 2010-07-15
> **linuxopjemac said:**
> As I said, USB is possibly not a bootable device, at least not with that method. You could try from open firmware.

[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)


So I would try the booting from stick part? Do I need to reinstall or can I try the commands? 

Also another 2 questions I have are 1. what's the minimum drive space needed and does anybody know if 10.5's Disk Utility do partitioning of a hard drive without erasing the whole drive?

I tryed partitioning my internal main drive last night with 10.4 and it deleted the whole drive. I didn't have much on it so I didn't care and reinstalled 10.4 right away. I googled and seen various post that it was possible to partition and extend the main drive with 10.5's disk utility and not delete it.

Thanks

---

### Post by linuxopjemac on 2010-07-15
Try the commands..

---

