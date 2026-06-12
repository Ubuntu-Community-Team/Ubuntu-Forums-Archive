---
title: "USB external drive question"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by HyperX on 2006-01-12
I unplugged a USB 2.0 drive from a Windows XP machine. I plugged it into my Ubuntu box. It was detected as BIT drive, and I am able to see the contents of everything inside. I am not able to write to it. When I try to change the permission to write it says I can't since I am not the owner. 

Any ideas?

I want to use this USB drive to backup my Ubuntu - so it's critical that I can write to this drive.  Thanks!!

---

### Post by thekiller on 2006-01-12
You can do either of the following :

```

1. sudo cp -R /ubuntu_bup /usb_disk, OR

2. chown username:users /usb_disk
    cp -R /ubuntu_bup /usb_disk

```

Hope that helps !

---

### Post by HyperX on 2006-01-12
[QUOTE=thekiller]You can do either of the following :

```

1. sudo cp -R /ubuntu_bup /usb_disk, OR

2. chown username:users /usb_disk
    cp -R /ubuntu_bup /usb_disk

```

Hope that helps ![/QUOTE]


Sorry about following up - but I get this with the first command

cp: cannot stat `/ubuntu_bup': No such file or directory

---

### Post by Haegin on 2006-01-29
Edit: Adding stuff for clarification.

First you need to know where the disk is mounted (probably somewhere in /media so have a look there with nautilus(the file manager) first or type "mount -l" into  a terminal and look for your usb drive) then you can use
```
sudo chown -R <your username> <path to disk>
```
replacing the stuff in <brackets> with your username and where the disk is mounted respectively.
For me this would look like this:
```
sudo chown -R harry /media/usbdisk
```

After you have done this you will be able to use the drive like normal through nautilus. The cp... command above just copies stuff from the usb drive to /usb_disk. You don't need to do this through the terminal - just use nautilus.

Hope this helps

---

### Post by Haegin on 2006-01-29
Edit - double post by accident - can somebody delete this please...

---

