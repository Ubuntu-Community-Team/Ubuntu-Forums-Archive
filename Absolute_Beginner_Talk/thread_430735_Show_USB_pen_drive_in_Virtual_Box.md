---
title: "Show USB pen drive in Virtual Box"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by thecomputingexpert on 2007-05-02
I am running Windows XP in Virtual Box on my linux operating system but cannot acccess my pen drive, when I select it to mount a USB device it brings up an error saying:

"Not permitted to open the USB device, check usbfs options."

Could anyone tell me how I can change my usbfs options

Thankyou

---

### Post by misconfiguration on 2007-05-02
sudo nano -w /etc/fstab

Enter this in your fstab under all of the rest of the lines, make sure you do not edit anything BESIDES adding this new line.

Reboot and see how well it works.

#usbfs
none    /proc/bus/usb            usbfs          devgid=46,devmode=664            0    0

---

### Post by thecomputingexpert on 2007-05-03
thanks that worked brilliantly

---

### Post by misconfiguration on 2007-05-04
> **thecomputingexpert said:**
> thanks that worked brilliantly

I'm just glad I can help!

---

### Post by headchange on 2007-05-09
just wanted to thank you for this post, helped me with my usb hd in virtualbox :P

---

### Post by misconfiguration on 2007-05-10
That makes me feel great; you know without the support of Linux users by Linux users this community would be nothing!

---

### Post by drowner on 2007-05-10
misconfiguration, from an education (MY education ;) ) point of view, could you explain what that line means, and what the problem was?

Cheers

---

### Post by Wiebelhaus on 2007-05-10
How do you save it?

---

### Post by misconfiguration on 2007-05-11
Drowner:
fstab is a configuration file that contains information of all the partitions and storage devices in your computer. The file is located under /etc, so the full path to this file is /etc/fstab. The first column contains the device name, the second one its mount point, third its filesystem type, fourth the mount options, fifth (a number) dump options, and sixth (another number) filesystem check options. Their issue was simply the devices couldn't be mounted and append to the filesystem without having the proper rules assigned to it. 

To sx66gns:

After you've opened and edited your file with nano hold control and press x, it will ask if you want to write the file as, click enter for defaults (filename fstab) and hit Y when it prompts you to append the changes, then enter, and it should dump you to the dir.

---

### Post by El Viejo Lobo on 2007-05-17
More thanks for the solution :guitar::popcorn::KS:KS:KS:KS

---

### Post by Triskal on 2007-06-29
Works great for me also!  Thanks!

---

### Post by Phrantik on 2008-05-11
thanks for pointing me in the right direction.
in my install of hardy heron the group usbfs did not exist. i had to create the group called usbfs and take note of the group id# to put into the fstab config file.

---

### Post by mrflabby on 2008-05-27
I also wanted to thank you for the brilliant solution!!

---

### Post by alecclews on 2008-07-21
I'm in the process of implementing this solution. I used the virtualboxusers group the groupid in fstab. It appears to work OK. 

However is that a sub optimal fix? Will I have problems in other programs under Linux?

Thanks

---

