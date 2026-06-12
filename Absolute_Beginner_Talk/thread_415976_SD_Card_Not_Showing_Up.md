---
title: "SD Card Not Showing Up"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by cam2009 on 2007-04-20
I'm using Feisty, and a Toshiba Satellite A105-S4054 laptop. It has a built in Texas Instruments 5-in-1 reader, but nothing happens when I insert one. Putting 'lspci' into the terminal comes up with 

> [ 1625.632000] mmcblk0: error 1 sending read/write command
[ 1625.632000] end_request: I/O error, dev mmcblk0, sector 249

repeated over and over again with a different sector number. Towards the end it says

> 07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

but it's not showing up in the File Browser or anything. I found a site that had me add some lines to /etc/modules, but that did nothing. Any ideas?

---

### Post by cam2009 on 2007-04-20
woops, had some of that info wrong. that error comes up when I do 'dmesg'. It shows that second quote when I do 'lspci'. I put in

sudo modprobe tifm_7xx1
sudo modprobe tifm_core

and 

sudo modprobe tifm_sd

In terminal, but that doesn't do anything.

---

### Post by macogw on 2007-04-23
Go [here](http://ubuntulinuxtipstricks.blogspot.com/2007/04/texas-instruments-sdmmc-card-reader.html) for instructions on making your TI SD card reader work with Feisty.  I copied the newer version of the driver plus included fixed kernel modules and tarred them up with a bash script.  The bash script will fix the kernel headers and install the new drivers.  Let me know if you have any trouble.

---

### Post by cam2009 on 2007-04-28
thanks for the reply, but that didn't work. was I supposed to put something special in
"linux-headers-`uname -r`"
where uname is? that gave me a "command not found".

---

### Post by cam2009 on 2007-04-28
Scratch that - it worked on reboot! thanks a bunch, it was getting very annoying having to go through my digital camera to access it.

---

