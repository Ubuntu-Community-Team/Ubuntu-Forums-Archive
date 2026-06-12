---
title: "Manually mount a USB flash drive?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by dfa_geko on 2006-08-15
Hi Everyone,

Does anyone need to manually mount a USB flash drive via CLI interface? For some reason, I remember just clicking on the USB flash drive icon and it would pop up. (Maybe I had the USB flash drive connected when I booted the system???) 

So my question is, did I forget to install something like Fedora's "autofs" or do I have to manually mount using "sudo mount" and "sudo umount" each time?

---

### Post by dfa_geko on 2006-08-15
I just installed "autofs" and it didn't change. I keep getting this error message:
> mount: only root can mount /dev/sdb1 on /media/sdb1



Did I miss something here? 

Thanks in advance!!!

---

### Post by dfa_geko on 2006-08-15
For anyone who has a similar problem. Here's the error and the fix:

The problem was I put my usb flash drive in the usb port of my laptop when I initially installed Ubuntu. Ubuntu treated my usb flash drive as another hard disk (with NTFS file system). 

When I plugged in my usb flash drive, ubuntu required that I manually mount it using "sudo mount" and "sudo umount". 

How I fixed it was I edited my fstab

> sudo gedit /etc/fstab

And removed the line corresponding to the usb flash drive. In my case, it was /dev/sdb2. And it worked! It's probably a linux newbie error, but I figured it out. Hopefully anyone who comes across this problem will find this helpful.

---

### Post by 3rdalbum on 2006-08-16
If for any reason you ever have to manually mount (I've never HAD to, but I did it a couple of times for fun), just "pmount" and "pumount" rather than "sudo mount" and "sudo umount".

---

