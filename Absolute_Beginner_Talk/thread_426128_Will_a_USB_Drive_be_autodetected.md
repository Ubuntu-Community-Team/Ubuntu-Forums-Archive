---
title: "Will a USB Drive be autodetected ??"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by =CrAzYG33K= on 2007-04-28
I've just installed Ubuntu 6.06 ..
I'm very very new to Linux and the whole file - structure .. :) 
So Would be 1GB Transcend USB drive be auto-detected ??
Where would it be mounted??

---

### Post by adelie on 2007-04-28
Most likely it will, and usually once it is plugged in, it will be detected and automatically mounted under /media/...  If it is a generic USB drive it may mount as /media/usbdisk. other USB devices, like IPODS will mount as /media/ipod. Either way, check under /media and you may see it there. 

Hope that helps.

---

### Post by vanadium on 2007-04-28
If you would have tried, you would have seen that it is automounted. You can see where it is mounted by right-clicking its icon on the desktop and selecting "properties". You will see the "mount point" listed there.

---

### Post by laidback on 2007-04-28
Mine is. It appears on the desktop. On my system it opens in the file manager automatically (many partitions worth). There are also a number of icons on the desktop, one for each partition.
If you don't get that look in Places>Computer , there you should see an icon, double click to open. 
If it says not mounted, right click choose Mount Volume.

Oh and Welcome to Ubuntu..........it's great.

---

### Post by octoberdan on 2007-04-28
> **=CrAzYG33K= said:**
> I've just installed Ubuntu 6.06 ..
I'm very very new to Linux and the whole file - structure .. :) 
So Would be 1GB Transcend USB drive be auto-detected ??
Where would it be mounted??

Nautilus, the file browser, may even open it automatically once you plug the drive in and turn it on. If the drive is plugged in and on and you can find it on your desktop or in /media, let us know and we can walk you through trouble shooting. Good luck!

---

### Post by =CrAzYG33K= on 2007-04-28
Oh ..
Thanx for all the replies... I'll sure check them out :D

---

### Post by konungursvia on 2007-04-28
Worst case, reboot linux with the thing plugged in, and it should show up in your places > computer and /media/ areas.

---

### Post by kordite on 2007-05-14
My iPod attached via USB used to be detected automatically. I don't know if it was my upgrade from v6.06 to v7.04 or repartitioning the drive that did it but it does not mount anymore. Doesn't appear on the desktop. Doesn't appear in /media. I have an external USB drive which continues to function properly. How can I get the iPod to come back?

---

### Post by aeiah on 2007-05-14
a word of advice for external usb drives: sometimes it will not load all the data onto it when you drag and drop. to complete the data transfer before removing the drive, right click it's icon and select 'eject'.

also, when you delete things from it, it'll store them in its own trash folder, so you'll have to remember to empty the trash every now and then or your usb stick will quickly become full

---

### Post by lakersforce on 2007-05-14
Try to plug it in :D

---

