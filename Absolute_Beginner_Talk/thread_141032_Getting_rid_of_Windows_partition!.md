---
title: "Getting rid of Windows partition!"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by n1tro on 2006-03-07
Ok, I finally found a reason to dump Windows XP. I followed the guide on how to setup Windows XP using VMware and it works great (USB webcam is detected so I can use my web chat)! Better than Qemu I was using when I was with Ubuntu 5.04. Anyways, I want to wipe out the Windows partition that I had set up for dual booting and was wondering if/how I can do it and assign the extra space to the Linux partition of Ubuntu. Thanks in advance.

---

### Post by meborc on 2006-03-07
You can use your ubuntu install cd... go through the install process until the partitioning... then chose manually editing the partitions... delete the windows partition... that should be free space now... 

now comes the tricky part... i don't know if it is possible to just then edit the linux partition which you use and make it bigger, or you have to assign this new free space to be a fat32 or a linux partition...

DO NOT GO THROUGH THE INSTALLATION PROCESS :mrgreen: after partitioning cancel the installation... or you just reinstall the whole system

---

### Post by aysiu on 2006-03-07
As far as I know, free space can be tacked on to the **end** of a partition but not the **beginning**.

So right now if you have
/dev/hda1 Windows
/dev/hda2 Ubuntu
you can't add the extra space to Ubuntu.

If it's
/dev/hda1 Ubuntu
/dev/hda2 Windows
you can.

The former situation is probably what happened--correct me if I'm wrong.

I would just delete the Windows partition, reformat it as Ext3, and use it as extra storage space mounted at /home/data or something. For that you wouldn't need the install CD or live CD. You could boot into Ubuntu, unmount Windows (*sudo umount /dev/hda1*) and then ```
sudo apt-get update
sudo apt-get install gparted ntfsprogs
sudo gparted
``` and use GParted to delete the Windows partition and reformat it as Ext3 and then ```
sudo mkdir /data
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` and tack this line on the end ```
/dev/hda1 /data ext3 defaults 0 0
``` and save (control-x), confirm (y), and exit (Enter).

---

### Post by meborc on 2006-03-08
wow... got some usefull information... thanks aysiu ;)

---

### Post by WelterPelter on 2006-03-08
And for god's sake, backup your data before trying any of this.

---

