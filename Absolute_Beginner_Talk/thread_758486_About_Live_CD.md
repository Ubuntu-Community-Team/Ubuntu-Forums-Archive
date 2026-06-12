---
title: "About Live CD"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by mak_20789 on 2008-04-18
Hi all,
         I want to learn Linux and so I posted to some forum where I was told  about Ubuntu. Here is what I was told:
          " You should try a Live CD,this will allow you to play with the OS without it ever touching your HD.
Simply download the live CD ISO and burn it to a disc,reboot your computer and your in linux! Remove the live CD reboot your computer and your back in Vista."
 
This exactly meets my requirements, as before installing it making a partition on my hard drive, i wanted to try it.
Now I am in the process of downloading ubuntu-7.10-desktop-i386.iso
Please answer my doubt, as I am using any OS other that windows for the first time.

Is this the same live CD ISO that i was told on that forum? i mean when I burn it to a disc, and reboot my computer, will the comp start in this new OS?
Would it work if I copy it to my 1 GB pen drive instaed of a CD? Or do I need to make any changes for booting from it?
 If I need to install it on my hard drive by making a partition, what steps do I need to follow?
Is there any article about it?


Btw, I read the threads that appeared at the top about Live CD, but none of them dealt with these questions.


Thankyou.

---

### Post by joshrobinson on 2008-04-18
thats the correct cd to use as a live cd

just burn it, put it in the cd-drom/dvd drive, and restart
if it doesnt start and say "start or install ubuntu" then you will have to restart your computer and enter the bios, and set it so the computer boots from the cd-rom first

as for putting it on a pen-drive, you would have to modify it, and your pc would have to support booting from a usb device, ive never done this so i personally cant help with that

as far as installing it, you would need to partition your drive, if your keeping windows (you can select which system to boot windows or ubuntu), you would need your windows partition, an ext3 partition for root, say about 10-20gig minimum, and a partition for swap space, which would be 2x the amount of ram you have

you will most likely have to resize your windows partition to get this to work, unless you have a spare hard-drive you can format just for ubuntu

---

### Post by mak_20789 on 2008-04-18
Thank you.

---

### Post by erginemr on 2008-04-18
First of all, welcome to Ubuntu! :D

For graphical installation guides, please refer to:
[http://ubuntuforums.org/showpost.php?p=4738950&postcount=4](http://ubuntuforums.org/showpost.php?p=4738950&postcount=4)

For installing on a pen-drive (which is too advanced for you to try at this stage, if you ask me), please refer to:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by kpkeerthi on 2008-04-18
> **erginemr said:**
> 
For installing on a pen-drive (which is too advanced for you to try at this stage, if you ask me), please refer to:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Unfortunately, you would need to be in another linux to get gutsy onto a pen drive and be able to boot with it. Not sure how you can make a bootable gutsy live USB from windows.

---

### Post by hyper_ch on 2008-04-18
have a read here:

[http://www.psychocats.net](http://www.psychocats.net)

---

### Post by erginemr on 2008-04-18
> **kpkeerthi said:**
> Unfortunately, you would need to be in another linux to get gutsy onto a pen drive and be able to boot with it. Not sure how you can make a bootable gutsy live USB from windows.

Actually, in this Community Howto, there seems to be a way to do it:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent#head-b1abb580ecc10852bd8a6877bb220448b324ac3f](https://wiki.ubuntu.com/LiveUsbPendrivePersistent#head-b1abb580ecc10852bd8a6877bb220448b324ac3f)

but I didn't bother as my BIOS did not allow booting from USB. :(

---

### Post by kpkeerthi on 2008-04-18
> **erginemr said:**
> Actually, in this Community Howto, there seems to be a way to do it:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent#head-b1abb580ecc10852bd8a6877bb220448b324ac3f](https://wiki.ubuntu.com/LiveUsbPendrivePersistent#head-b1abb580ecc10852bd8a6877bb220448b324ac3f)

but I didn't bother as my BIOS did not allow booting from USB. :(

Thanks for posting the link. Should be useful for the OP.

---

