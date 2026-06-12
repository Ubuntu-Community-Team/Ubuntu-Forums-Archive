---
title: "Mounting usb stick..."
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by FleetAdmiral74 on 2007-06-06
Someone suggested:
sudo mkdir /media/sda && sudo mount /dev/sda /media/sda

It says I need tp specify the filesystem type. Any way I get get this to just auto mount when I plug it in?

edit: i might just be retarded, because now it does. I wonder if it was because of the code...

---

### Post by tgalati4 on 2007-06-06
Flash drives will automount.  However, if the drive is broken, has a corrupted partition table, or a "Hidden" autorun DOS partition, then it will give problems.

What brand and model is the USB stick?

---

### Post by FleetAdmiral74 on 2007-06-06
Dane-Elec. Never heard of it before, but it was on sale....like I said, all seems well now.

---

### Post by tgalati4 on 2007-06-07
Be mindful when writing large files to your flash disk that Nautilus will show that files have transfered, but they are pushed to the background and can take several minutes.  If you are not aware of this, you can end up pulling the flash stick before all the files have been written.  This tends to happen to flash drives with slow memory controllers.

---

### Post by Inxsible on 2007-06-07
you should use pmount to mount your removable drives
```
 sudo pmount <device name> <mount point>
```

pmount doesnt automatically mount your devices, only when they are connected- which is what you want with external drives and flash drives

---

