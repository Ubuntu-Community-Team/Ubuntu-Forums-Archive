---
title: "Pendrive woes"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by mrdlouisd on 2008-02-06
I have been trying out different distros on a new 4 gig pen drive. The last one I tried installing was xubuntu. But it didn't finish, When I try to format my pen drive I notice it has a boot flag on it. Whenever I try to do anything to it I get the read only error. I've tried the included apps to format it, I've tried deleting the partion on it, tried writing a new one. 

I've searched to no avail. Wondering if there is something I'm missing here.

---

### Post by eggdeng on 2008-02-06
Sorry, misread OP.

---

### Post by wolfen69 on 2008-02-06
have you tried gparted to delete partition?
```
sudo gparted
```
then unmount pendrive before deleting partition.
```
sudo umount /dev/sdxx
```

try this for ubuntu on pendrive. [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by onthefence on 2008-02-06
There are many ways to cut a carrot, although in this case, you have to be careful thinking that all these methods are actually doing the same thing. 
Likewise, there are many manuals/guides to installing linux and even installing linux to a pendrive. I have tried many and had  much frustration.
This one I found to be the best because it is command-based so it is direct communication, not an interface that who knows what it is doing in the background.

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/) 

A couple of simple newbie things you will have to know in case you don't already that weren't mentioned in the guide.
1. To open a terminal, go to Applications-->Accessories-->Terminal.
2. To copy from most programs it's "Ctrl+C". However, for the terminal it's "Ctrl+Shift+C". Likewise, to Paste it's "Ctrl+Shift+V". This will save lots of time and ensure no typos. 
3. I learned the hard way since I was typing the commands that the command to unmount a partition/drive is "umount" not "unmount". So I definitely recommend for this to copy and paste.

Doesn't hurt to try, takes about 20 minutes maybe. If this doesn't work, then maybe something went bad with the drive. But I could not say for sure.

Good luck!

---

### Post by mrdlouisd on 2008-02-06
I do favor the cmd line installs. That was what I was trying out at first to no avail. So I just installed with the text line installer from a kubuntu livedvd. It worked out great, but when I tried xubuntu is when I ran into problems.

I unmount drives, but still get the read only error. I have noticed that a boot flag is on, that I can't remove. Is this perhaps my problem? I've tried deleting the partition. Is it perhaps there I went wrong. Whenever I use fdisk umounted or mounted I get the text that it is a read only, and I wont be able to write to it. 

There is no hardware read only switch on the usb pen drive.

Also pendrivelinux is a great site, and that is where I follow off of.

---

### Post by froy02 on 2008-02-06
Did you start as a root user, code: su?

---

### Post by warrior24 on 2008-02-06
haha thanks for the copy command in terminal. I wondered why it never worked. :guitar:

---

### Post by mrdlouisd on 2008-02-06
Yes I use su.

---

### Post by onthefence on 2008-02-07
Sorry for stating the obvious but another way to go is to borrow(or buy) another usb drive and see if it works. Or maybe there is utility out there that can check for any hardware errors on the device.

My understanding is that once you reformat from the very first block and then format all the way to the end of the logical space, there should be no other information or flags on that piece of drive. This is why I suggested that guide to install. It commands the partition editor to start with the very first block etc etc.

Best of luck

---

### Post by mrdlouisd on 2008-02-07
I have another usb pen drive that works. I went ahead and started using it for the moment. Trying to get minime onto it. I'm going to stop by a friends house that has a windows pc, and see if I can't get that flag off and format it. 

Not really sure what went wrong nor how to fix it. I've been thru those tutorials with terminal, but to no avail. Thanks for all the help.

---

