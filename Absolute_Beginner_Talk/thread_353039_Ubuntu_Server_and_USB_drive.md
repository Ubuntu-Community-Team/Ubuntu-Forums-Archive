---
title: "Ubuntu Server and USB drive"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by bxbailey on 2007-02-04
I'm trying to copy some files over to ubuntu server using a USB drive but I'm not sure how to mount or where to look for the thumbdrive. Any help is greatly appreciated. Thank youl.

---

### Post by sardion on 2007-02-04
You say "server" so I will assume you mean server.  If you are running a desktop then there are much easier ways than this (like gnome-volume-manager for instance).  But for a genuine server (no desktop):

Make sure the module is loaded:

sudo modprobe usb-storage

Then:

sudo mount -t xxx /dev/sdaN /mnt

N is likely to be 1 but you can check dmesg to see for sure.

---

### Post by bxbailey on 2007-02-04
Ok thanks for the quick response 

I'm typing/trying  both

sudo mount-t xxx/dev/sda1 /mnt

sudo mount-t mnt/dev/sda1 /mnt


but what I am getting is: 

sudo: mount-t: command not found

---

### Post by jimcooncat on 2007-02-04
I'm not really familiar with this, but it looks like you need a space between the "mount" and the "-t".

---

### Post by bikeboy on 2007-02-04
Correct, there needs to be a space. Also, the xxx was just a placeholder to show you need something, the filesystem type to be exact. For example, a usb drive formatted in fat32 would be mounted with ```
 sudo mount -t vfat /dev/sda1 /mnt
```

---

### Post by bxbailey on 2007-02-04
Thanks that got me a little further 

maybe I should just install the desktop version first so I have a GUI.

---

### Post by bikeboy on 2007-02-04
To be honest that's not a bad idea. Once you're up and running how you want, it's easy to turn off the gui to free up resources. There's definitely a learning curve and there is no shame in starting with the simpler version.

When I first got into Linux it was as a desktop, I coudn't have run a headless server, but now I do and it's running great.

---

