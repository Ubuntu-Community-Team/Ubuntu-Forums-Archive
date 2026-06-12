---
title: "Dual booting Arch and Ubuntu"
date: 2008-02-09
forum: Arch and derivatives
---

### Post by MONODA on 2008-02-09
Hi i have been using ubuntu for quite some time but would like to try somethig else. I DOWNLOADED aRCHLINUX and am trying to dualboot it with ubuntu. But I am not sure how to add a Arch linux choice to the boot loader. Also, during install it asks me to install either the grub or LILO boot loader, I want Grub so when I choose it it asks me to configure it, how should I do so? thanks in advance.

---

### Post by MONODA on 2008-02-09
Hi, here is what I need help with now:
 At the top of Arch grub it says:
> 
Linux                                Grub
---------------------------------------------------------
         /dev/fd0                             (fd0)
         /dev/hda                            (hd0)
         /dev/hdb2                          (hd1,1)
         /dev/hda3                          (hd0,2)

what does each part of this mean? how can I tweak it for myself? Do I even have to edit this?
also I dont know the grub menu entries in my ubuntu, could anyone provide me with a template or something...
One last thing, is this all I will have to change in grub or is there more? thank you.

---

### Post by Rumor on 2008-02-09
> **MONODA said:**
> Hi, here is what I need help with now:
 At the top of Arch grub it says:

what does each part of this mean? how can I tweak it for myself? Do I even have to edit this?
also I dont know the grub menu entries in my ubuntu, could anyone provide me with a template or something...
One last thing, is this all I will have to change in grub or is there more? thank you.

I'll try to answer this step by step.

First, the answer to "What does each part mean?" is found in the line immediately above what you copied and pasted into your post where it says: 
```
# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/hda        (hd0)
#  /dev/hdb2       (hd1,1)
#  /dev/hda3       (hd0,2)
```
You don't edit that portion of grub. It is telling you Linux calls your first hard drive hda and Grub calls it hd0 and so on. You don't have to edit it. Editing it will change nothing.

Dual booting Ubuntu and Arch

While this is not the most elegant solution, I found it worked for me when I was dual booting Ubuntu and Arch. 

During your install you set up the file system mount points for / and for /home. When you get to the point where you are asked where you wish to install grub, choose your / partition for Arch. When you are reviewing the entry in vi / nano, look for the part that says something like this:
```
# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /vmlinuz26 root=/dev/sda3 ro
initrd /kernel26.img
```

Copy down your specific entry. 
Reboot into Ubuntu
Edit Ubuntu's Grub menu ```
sudo gedit /boot/grub/menu.lst
``` and add the entry for Arch after the entries for ubuntu.
Reboot your computer and boot into your new Arch install and begin updating and building your new system.

---

### Post by MONODA on 2008-02-09
Thanks for the reply in fact thats what I ended up doing all by my little old self. no i just need to configure it :)

---

### Post by woedend on 2008-02-09
When I first ventured into arch, i would run into problems similar and run back to ubuntu.  But arch has the most helpful forums, and is so great to use once you get running.  Please, if you have any questions just ask...and don't give up.  Many solutions are documented online, and the community is great.  Good luck with arch, I do hope you like it!

---

### Post by MONODA on 2008-02-09
well i have given up on it (for today only) since I have a limited download every month (2gb only :'() since I have to download a de and Xorg and eerything. Also I am not too sure how to find the best server so I download very slowly: 7kbps.

---

### Post by woedend on 2008-02-09
where do you live?  there are scripts for finding best download server, but i'll try to find one for you. (read wiki.archlinux.org, especially pacman sections) Typically, installing arch takes MUCH less room than any other OS i've used.  To install arch with gnome, X.org, codecs, media, wireless, openoffice, gimp, firefox, thunderbird, java, flash, firestarter, frostwire, and a couple extras, usually takes less than 600 mb.  The ubuntu CD image is larger than this, not including its abysmal install time.

---

