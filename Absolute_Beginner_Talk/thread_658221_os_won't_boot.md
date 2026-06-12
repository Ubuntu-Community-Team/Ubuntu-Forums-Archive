---
title: "os won't boot"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by jhvillegas2 on 2008-01-04
I asked for a solution to the problem that when I set the monitor to never shut off (power save), the monitor still shuts off.  I got what I thought was an alternate solution, and I implemented it.  However, my OS won't boot up now at all.  It allows me to enter my account username and password, then goes black and stays black.  Any help in resolving this would be much appreciated.

---

### Post by dstew on 2008-01-04
Did you edit your xorg.conf file? If so, you might have made it so the graphical user interface cannot start. You can get a command line interface by pressing ctrl-alt-F1. Then we can try to repair the system.

---

### Post by jhvillegas2 on 2008-01-04
ok, I am logged into the command line

---

### Post by meindian523 on 2008-01-04
If you have changed your xorg.conf file(including installing Restricted drivers for your ATi or Nvidia card),try

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jhvillegas2 on 2008-01-04
I can't remember if I changed my xorg.conf file.  How do I determine if I did, please?

---

### Post by meindian523 on 2008-01-04
Do a ```
ls -alF /etc/X11/xorg*
``` and post the results.

edit:That lists the files with permissions of all files starting with "xorg"

Also post when you installed Ubuntu.

---

### Post by jhvillegas2 on 2008-01-04
The results are:

-rw-r--r-- 1 root root 2495 2008-01-02 13:05 /etc/X11/xorg.conf

I think I installed the OS on Tuesday.

---

### Post by meindian523 on 2008-01-04
Nopes,you didn't change your xorg.conf.:)

Try checking the data and power cable connections to your monitor and do the 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

