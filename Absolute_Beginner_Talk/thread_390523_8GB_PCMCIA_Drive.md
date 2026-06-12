---
title: "8GB PCMCIA Drive"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by aldorr on 2007-03-22
I have Ubuntu Edgy installed on a Samsung X10 laptop and don't have the faintest idea how I could get this drive to mount.
It's a [P2 drive]("http://catalog2.panasonic.com/webapp/wcs/stores/servlet/ModelDetail?storeId=11201&catalogId=13051&itemId=94170&surfModel=AJ-P2C008HG") from Panasonic. I need to copy HD video files from it to Firewire drives that are also connected to my laptop. The problem is, I put the [P2 card]("http://catalog2.panasonic.com/webapp/wcs/stores/servlet/ModelDetail?storeId=11201&catalogId=13051&itemId=94170&surfModel=AJ-P2C008HG") in and I don't know how I could find it and mount it, or even how I can find out how to do this.

Does anyone have any experience mounting media that's in a PCMCIA bay? If not... I'm going to be forced to put a microsoft product back on my machine. Any help would be greatly rewarded in the afterlife.

Thanks.

---

### Post by fdrake on 2007-03-22
after you plug-in your drivers type in the terminal 
 
sudo fdisk -l

---

### Post by igknighted on 2007-03-22
You will probably need some sort of boot disk.  I don't believe the linux kernel can boot from a pcmcia drive.  You might be able to chroot into the system from the liveCD and rebuild the kernel with pcmcia support built in (not as a module), but this would be a complex solution.  Hopefully someone else has better news.

EDIT: My apologies, I thought you were trying to boot from that drive

---

