---
title: "Updates broke Webcam"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by EricJosepi on 2007-02-10
Hey

I just installed a whack of updates this morning and after I restarted my computer, i found that my webcam was no longer working properly.  I used the SPCA drivers for it, since those are the only ones that support the Logitech Quickcam for Notebooks Deluxe.  I tried re-installing the drivers and got no love from the oft-forgiving Linux gods.  So, basically I'm just looking for a helping hand here.

---

### Post by EricJosepi on 2007-02-10
Ok... I tried re-installing the drivers with no luck.  I tried following the steps to get SPCA [here](http://ubuntuforums.org/showthread.php?t=205782&page=5&highlight=quickcam+deluxe) like I did before and I'm getting errors in the compile process. 

This is the error I get

```
josepi@UbuntuLappy486:~$ sudo  '/home/josepi/Desktop/gspcav1-20070110/gspca_build' 

 REMOVE the old module if present
ERROR: Module gspca does not exist in /proc/modules

 CLEAN gspca source tree
make: *** No rule to make target `clean'.  Stop.

 COMPILE gspca Please Wait ....!!

 INSTALL gspca in the kernel binary tree
make: *** No rule to make target `install'.  Stop.

 LOAD gspca in memory 
FATAL: Module gspca not found.

 PRINT COMPILATION MESSAGES if ERRORS look kgspca.err 
make: *** No targets specified and no makefile found.  Stop.
```

If anyone out there can give me a hand it would be most appreciated!

---

### Post by tom_ on 2007-02-23
if you have not been successful, try ...

$ cd /home/josepi/Desktop/gspcav1-20070110/
$ sudo ./gspca_build

---

