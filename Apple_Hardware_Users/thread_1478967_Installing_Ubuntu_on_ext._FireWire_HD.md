---
title: "Installing Ubuntu on ext. FireWire HD"
date: 2010-05-10
forum: Apple Hardware Users
---

### Post by c-a-b on 2010-05-10
Hi there,

since yesterday, I try to install Ubuntu Linux on an external FireWire drive on my iMac G5 2 GHz. First I insert a Ubuntu 8 CD, klicked restart and pressed c for booting from the Linux CD. The first time, it worked and I got the DOS-like screen of installing Ubuntu. I selected the external drive, Installation did going well but then at the end, there was an error creating the yaboot files. Linux was on the ext. drive but useless. 

I tried several times again since then, but booting again from CD the screen remained grey and didn't do anything for about ten minutes. I tried restarting several times, nothing changed. 

So this morning I gave it another try and inserted an older Ubuntu Linux Live 6 CD and it loaded the live Linux well. But then, the installation did fail at the point of loading the partitioning tool. I had to force quit by pressing the power button again. 

Today I tried several times, too. Chances are best when the iMac was completely off power and with the insertet Ubuntu 6 Live CD. But then, Ubuntu stops while Startscreen with mass of messages like
"buffer i/o error on hda" 
I waited some minutes but nothing changed.

---

### Post by linuxopjemac on 2010-05-10
This guy did it with Karmic Koala:
[http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0](http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0)

---

### Post by linuxopjemac on 2010-05-10
If yaboot was put on the external firewire disk, all you need to do is hold the option (Alt) key during boot. It will then give you a screen with bootable devices.

[http://picasaweb.google.nl/lh/photo/C8nTY1sgb4jpQ8R8KuxhWdPJRTAxhjHcBD8yhZTROEk?feat=embedwebsite](http://picasaweb.google.nl/lh/photo/C8nTY1sgb4jpQ8R8KuxhWdPJRTAxhjHcBD8yhZTROEk?feat=embedwebsite)
[http://picasaweb.google.nl/lh/photo/5FClHkVGpUq00YPyT3pOIdPJRTAxhjHcBD8yhZTROEk?feat=embedwebsite](http://picasaweb.google.nl/lh/photo/5FClHkVGpUq00YPyT3pOIdPJRTAxhjHcBD8yhZTROEk?feat=embedwebsite)

---

### Post by c-a-b on 2010-05-10
It simply didn't go that far. There was no Yaboot.

---

### Post by linuxopjemac on 2010-05-10
You can set yaboot on the external firewire drive also manually. If you created a bootstrap partition.

[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

Note pdisk is now mac-fdisk

---

