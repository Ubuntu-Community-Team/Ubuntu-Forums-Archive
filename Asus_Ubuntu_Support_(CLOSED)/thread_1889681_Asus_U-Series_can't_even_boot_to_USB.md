---
title: "Asus U-Series can't even boot to USB"
date: 2011-12-01
forum: Asus Ubuntu Support (CLOSED)
---

### Post by raichle on 2011-12-01
I'm trying to install Ubuntu on my new Asus U-series laptop. I followed the directions to create a bootable usb install but when I boot from it, I just get a flashing cursor.  I've reformatted to fat32.

What am I doing wrong?

---

### Post by shakabra on 2011-12-02
Here are the steps that always work for me.

1. Format the drive to FAT using Disk Utility
   a.open disk utility
   b.unmount disk
   c.format

2. Install unetbootin 
   a.[https://launchpad.net/~gezakovacs/+archive/ppa]("https://launchpad.net/~gezakovacs/+archive/ppa")

3. Use unetbootin to make startup disk
   a.open unetbootin
   b.choose image
   c.install

4. Reboot

5. Open BIOS (different for every computer probably ESC, F2, DEL or something like that)

6. Make sure the usb drive is at the top of the boot priorities

7. Exit BIOS saving changes

8. Profit

---

### Post by raichle on 2011-12-02
I used this software to format to fat32 and create it (as recommended by Canonical):
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3)

I'll try your method as well later today. Is it possible thatit's an isue with my drive being too large? I think it's 16GB.

---

### Post by raichle on 2011-12-03
Okay, I did all of this and it's still not working.  I tried on another computer and could boot to it either.  Is it possible that every download that I've tried is corrupted?  I have tried 3 different ones. How can I get it via torrent?

---

