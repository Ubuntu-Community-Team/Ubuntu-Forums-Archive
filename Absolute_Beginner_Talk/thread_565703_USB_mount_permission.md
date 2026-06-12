---
title: "USB mount permission"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by tony.morse on 2007-10-02
Help please,
When I switch on my USB hard drive, I get a message saying I don't have permission to mount it!!

Whats going on??  How do I fix this??

---

### Post by baysl on 2007-10-02
Write:

**ls -la /media** in terminal and paste it here...

---

### Post by tony.morse on 2007-10-03
ok I get this...

drwxr-xr-x 13 root root  4096 2007-10-03 12:15 .
drwxr-xr-x 22 root root  4096 2007-09-30 15:56 ..
lrwxrwxrwx  1 root root     6 2007-09-28 21:04 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-09-28 21:04 cdrom0
dr-xr-xr-x  1 root root 12288 2007-09-18 21:41 data
lrwxrwxrwx  1 root root     7 2007-09-28 21:04 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2007-09-28 21:04 floppy0
-rw-r--r--  1 root root    71 2007-10-03 12:15 .hal-mtab
--wxr-x---  1 root root     0 2007-04-15 13:56 .hal-mtab-lock
lrwxrwxrwx  1 root root     4 2007-09-30 19:08 usb -> usb0
drwxr-xr-x  2 root root  4096 2007-09-30 19:08 usb0
drwxr-xr-x  2 root root  4096 2007-09-30 19:08 usb1
drwxr-xr-x  2 root root  4096 2007-09-30 19:08 usb2
drwxr-xr-x  2 root root  4096 2007-09-30 19:08 usb3
drwxr-xr-x  2 root root  4096 2007-09-30 19:08 usb4
drwxr-xr-x  2 root root  4096 2007-09-30 19:08 usb5
drwxr-xr-x  2 root root  4096 2007-09-30 19:08 usb6
drwxr-xr-x  2 root root  4096 2007-09-30 19:08 usb7

---

### Post by philinux on 2007-10-03
sudo chown -R yourusername /media/yourdiskname

---

### Post by tony.morse on 2007-10-03
Ok fixed it. What I had to do was change a line in /etc/fstab so it read...
/dev/sda1       /mnt/USB        auto rw,user,noauto  0       0

was having no luck with the volume permission documents but they lead me to the file fstab and after some messing about I just copied the permission from a drive that did work and that fixed it!!

---

### Post by philinux on 2007-10-03
I had trouble with root so I had to ch owner

---

