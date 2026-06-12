---
title: "gnome automount according to fstab"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by compwiz18 on 2007-02-02
I added an entry in my /etc/fstab to mount my external hdd to the same folder every time, but GNOME's automount appears to ignore /etc/fstab, just randomly mounting it at /media/usbdisk-1

my /etc/fstab:
```
UUID=f51738fc-4dc4-42b8-87f5-c7a3a931f616 /media/external-1     ext3    defaults        0       2

```

yes, I tried **mount -a** and it mounted it correctly.

I wouldn't mind if it actually mounted it in the same place every time, but depending on the order things are plugged in...it doesn't seem to work.

so my question is: does anyone know how I can tell GNOME where to mount my drive, instead of it just randomly mounting it somewhere?

---

### Post by pseudonym on 2007-02-02
I think you would have to have the drive plugged in and switched on at startup for what you want to do to work. Though gnome-volume-manager may have a config file somewhere which you could edit (it's a long time since I used GNOME). Check in /etc or /etc/default or similar for such a file.

But, at the same time, is it really necessary that your external drive gets mounted to that particular mount point? If you set your file browser to display all your disks (which I think is the default view) you will have easy access to the drive from your /home. Then just delete that /etc/fstab line and let GNOME mount the drive where it wants.

---

### Post by compwiz18 on 2007-02-03
I don't really care, to be honest, but I wanted to install a couple of virtual computers on that drive, and vmware doesn't like it when the drive changes mountpoints.  But seeing as vmware won't install today, it doesn't really matter for now.

looked in /etc/, /etc/default, and gconf - nothing except the option I can change with the GUI. Oh well.

Thanks for confirming my suspicion, though.

---

### Post by mcduck on 2007-02-03
In this case you'd only have to set the partition label of the removable drive to 'external-1', and then the automount would mount it to /media/external-1, just like you want..

If removable drivers have labels set, they are used when automounting those drives. Otherwise you just get 'usbdisk-1' and such names.

---

### Post by compwiz18 on 2007-02-03
Yeah, I set my fat32 drives to have names, like flash* and they always mount at flash*, but is it possible to set ext3 drive labels? edit : nvm, google knows all.

---

### Post by compwiz18 on 2007-02-03
works great, thanks
for any one who is wondering, the command is:
**e2label /dev/sdc1 yourlabel**

---

