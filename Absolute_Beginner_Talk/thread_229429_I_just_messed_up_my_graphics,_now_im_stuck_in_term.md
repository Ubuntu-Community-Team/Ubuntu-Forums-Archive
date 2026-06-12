---
title: "I just messed up my graphics, now im stuck in terminal!"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by bamf on 2006-08-04
So I was trying to get my Lenovo X41 laptop to use the correct video driver. So using these wonderful forums I followed the following steps, except backwards (putting i915 in instead of i810). I was doing this so I could get xgl to work, which is a whole other story.

> You should already have the driver installed, but you are likely not using it yet. First, let's make sure that it is installed. Start Synaptic, and look for xserver-xorg-driver-i810 (or just type in i915 into the search box).

If it is already installed (the box next to it is green), we can go to the next step. If it is not installed, install it. I too have i915 installed, and the problem is that Ubuntu didn't go ahead and use the i915 driver as it was supposed to have done. Instead, it relied on VESA. If you're interested in what VESA is, read about it, but its not important, so keep reading.

We're now going to make sure the system uses the driver it is supposed to use, instead of VESA. We're going to do that by opening up /etc/X11/xorg.conf. Go into the terminal, and type in gksudo gedit /etc/X11/xorg.conf. This will open the file using gEdit.

You should now have /etc/X11/xorg.conf on your screen. Go to the following section:

Quote:
Section "Device"
Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Driver "i810"
Option "XAANoOffscreenPixmaps"
BusID "PCI:0:2:0"
EndSection

You see where my driver says i810? That's because I changed it to i810. Before, it said "vesa," because it wasn't using the driver it was supposed to use. You may be wonder...why i810 when you actually have the i915? Well, i810 is the name that covers the entire family, including i915. So, change the driver from whatever it is (likely "vesa"), change it to say i915, as you see in the above example.

Now, to have things go into effect, save the document, and restart your system. Your system should now be using the correct driver, instead of Vesa.
Reply With Quote

Now when i rebooted I get a nice blue error message, I know what the error is its the stupid i915 drivers that probably don't exsist but they were in my Synaptic and it was green. So now Im stuck in terminal and have no clue how to open this file to edit it back to i810 so I can have graphics again. 

So basically whats the commands to edit this file in terminal and how do I get it to use the right driver?

Anyhelp would be awesome!

Thanks!
Kiley

---

### Post by Arisna on 2006-08-04
In your terminal, use the command

```
sudo nano /etc/X11/xorg.conf
```

to edit that file.  Navigate with arrow keys, make your changes, and do Ctrl-O to save the file.

Also, you'll have to get X started after it is configured correctly.  You can reboot, or you can use the following command:

```
sudo /etc/init.d/gdm restart
```

---

### Post by Markus Valkeapaa on 2006-08-04
>
> So now Im stuck in terminal and have no clue how to open this file to
> edit
 
$ cd /etc/X11
$ sudo nano xorg.conf

'nano' editor works in the terminal window. I am sorry that I have no advice to your original problem. Hopefully you get at least your previous set-up back.

-Markus

---

### Post by bamf on 2006-08-04
Sweet, I got the problem fixed, still don't get why that didn't work for my graphics card, but I'll work on that later.

Thanks!

---

