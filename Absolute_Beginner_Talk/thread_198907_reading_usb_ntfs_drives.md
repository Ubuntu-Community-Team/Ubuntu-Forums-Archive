---
title: "reading usb ntfs drives"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by opita on 2006-06-17
Hello,

Help
I know linux reads ntfs drives, but how.
I have ubuntu installed in my inspiron 9100 laptop, I need to install the wireless drivers.
To do that I need to be able to read my usb drive which has all my files (but it is an ntfs drive)
You can see the drive in ubuntu, but when i try opening it says unable to mount selected drive.
Is there any way I can read the contents of this drive?
Any help would be appreciated.

p.s I've looked through the forum and only see complex how tos on mounting ntfs primary hard drives.Which is not what i have.

---

### Post by johnnymac on 2006-06-18
You'll have to mount the drive as an ntfs file system....

mount -t ntfs /dev/device_thingee /media/somedirectory

That should do it....you'll at least be able to do stuff using sudo anyway.

---

### Post by aysiu on 2006-06-18
Actually, assuming the external drive doesn't automatically mount with the proper permissions (which seems to be the case), it's the same procedure to mount external hard drives as it is to mount internal hard drives or internal partitions on hard drives.

Most likely, if it's /dev/sda1, the procedure would be ```
sudo mkdir /ntfsdrive
sudo umount /dev/sda1
sudo mount -t ntfs /dev/sda1 /ntfsdrive -o nls=utf8,umask=0222
```

---

