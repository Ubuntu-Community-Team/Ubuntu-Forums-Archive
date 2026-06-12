---
title: "Can't access external usb drive"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by DavidNW on 2006-11-16
Hello, everyone.

I'm a Linux newbie in need of help with getting an external usb drive writable and readable in Ubuntu Dapper Beta.

I have formatted my external USB drive (formerly formatted in NTFS under Windows) in Ext 3 format in Ubuntu Dapper.  I did this as I'm no longer using Windows and wanted to free-up the external drive to to use for storing data in Ubuntu.

After the formatting, I cannot access the drive at all due to not having the appropriate ownership/file permissions.  All I want to do change ownership to myself 'david'.  

I have tried a series of Linux bash commands to try and change ownership/permissions but cannot change anything so that I can write/save any data to the drive - I'm guessing I'm using the incorrect syntax.

I'm attaching a couple of screenshots to aid any help/advice.

Many thanks,

David.

---

### Post by jd65pl on 2006-11-16
What commands have you tried. Could you provide the output of

```
ls -l /media
```

---

### Post by DavidNW on 2006-11-16
Thanks for replying.  I have since found out the code I needed to enter was : sudo chown -R david:david /media/usbdisk

That did the trick, so all is well now! :D

---

