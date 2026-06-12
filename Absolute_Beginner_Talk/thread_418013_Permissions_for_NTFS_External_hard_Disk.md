---
title: "Permissions for NTFS External hard Disk"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-04-22
[https://help.ubuntu.com/community/Mo...493f08ad90a52c](https://help.ubuntu.com/community/Mo...493f08ad90a52c)

I am on 7.04. I followed the instructions in the above link, I have enabled write support in the configuration, but when I try to write anything to my external hard disk it still tells me I don't have permission to access it. How do I change this??

Also, how do I go into directories using the cd command into an external device? I only know how to use the cd command on everything contained within the home folder on the internal hard disk.

---

### Post by lluisanunez on 2007-04-22
Your external devices mount under /media directory. Open Nautilus and you'll see them: /media/sda1, or /media/usbdisk or whatever. In a terminal:
```
cd /media/usbdisk
cd /media/sda1

```
To change permissions:
```

sudo chown [yourusername] [path]

```

---

### Post by Wake Rider on 2007-04-22
Thank you for the info.

Unfortunately when I last used the USB disk, I did not unmount it and now Linux refuses to mount it. How do I fix this problem?

---

### Post by lluisanunez on 2007-04-22
What's in your etc/fstab?

---

### Post by Wake Rider on 2007-04-22
> **lluisanunez said:**
> What's in your etc/fstab?

What do you mean? I'm sorry, I'm still relatively new to Ubuntu.......

---

### Post by Wake Rider on 2007-04-23
I'm getting an error that is telling me that the volume is due for a check and I must boot into Windows twice (can't do that, this isn't a dual-boot system) or do a force mount using the command line. How do I do a force mount??:confused:

---

### Post by lluisanunez on 2007-04-23
This thread may help you:
[http://ubuntuforums.org/showthread.php?t=413145](http://ubuntuforums.org/showthread.php?t=413145)

---

### Post by Wake Rider on 2007-04-24
I fixed my problem. I attached the USB drive to Windows and did a scan disk and used the 'Safely Remove Hardware' Option. Linux accepted the drive perfectly after that, both read and write. 

Thanks for your advice everyone!!:)

---

### Post by lluisanunez on 2007-04-24
Good to know :KS

---

