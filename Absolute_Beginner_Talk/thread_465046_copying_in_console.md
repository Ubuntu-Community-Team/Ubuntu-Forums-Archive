---
title: "copying in console?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Boris-- on 2007-06-05
I somehow lost my xorg.conf. Now, when I wanna copy the backed-up one to the X11 folder, this happens. 

> boris@buckshot:~/Desktop$ sudo cp /etc/X11/ xorg.conf 
Password:
cp: omitting directory `/etc/X11/'

TIps?

---

### Post by Martje_001 on 2007-06-05
you have to do it like this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

### Post by Boris-- on 2007-06-05
> boris@buckshot:~/Desktop$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_orig
cp: cannot stat `/etc/X11/xorg.conf': No such file or directory


No go..

---

### Post by taurus on 2007-06-05
What's the output of this command?

```
ls -la /etc/X11
```

---

### Post by Martje_001 on 2007-06-05
```
No such file or directory
```
No file? Do
```
cd /etc/X11
ls
```
Do you see xorg.conf?

---

### Post by earobinson on 2007-06-05
try ```
cd /etc/X11
ls -la
``` and paste the output for us

---

### Post by Boris-- on 2007-06-05
> boris@buckshot:/etc/X11$ ls -la
total 160
drwxr-xr-x  12 root root  4096 2007-06-05 16:58 .
drwxr-xr-x 113 root root  4096 2007-06-05 16:09 ..
drwxr-xr-x   2 root root  4096 2007-04-15 14:00 app-defaults
drwxr-xr-x   3 root root  4096 2007-05-29 10:52 applnk
drwxr-xr-x   2 root root  4096 2007-04-15 13:59 cursors
-rw-r--r--   1 root root    14 2007-05-28 13:28 default-display-manager
drwxr-xr-x   6 root root  4096 2007-04-15 13:53 fonts
lrwxrwxrwx   1 root root     6 2007-05-28 13:28 gdm -> ../gdm
-rw-r--r--   1 root root 17371 2007-02-13 11:02 rgb.txt
drwxr-xr-x   3 root root  4096 2007-05-29 10:52 susewm
lrwxrwxrwx   1 root root    13 2007-05-28 11:43 X -> /usr/bin/Xorg
drwxr-xr-x   3 root root  4096 2007-04-15 13:54 xinit
drwxr-xr-x   2 root root  4096 2007-04-15 13:50 xkb
-rw-r--r--   1 root root  3387 2007-06-05 16:54 xorg.conf~
-rw-r--r--   1 root root  3493 2007-05-29 10:00 xorg.conf.20070529100021
-rw-r--r--   1 root root  3363 2007-05-29 12:29 xorg.conf.20070529122925
-rw-r--r--   1 root root  4231 2007-05-29 15:08 xorg.conf.20070529150840
-rw-r--r--   1 root root  3436 2007-05-29 15:12 xorg.conf.20070529151202
-rw-r--r--   1 root root  3384 2007-05-29 16:12 xorg.conf.20070529161252
-rw-r--r--   1 root root  3415 2007-06-05 16:11 xorg.conf.20070605161103
-rw-r--r--   1 root root  3387 2007-06-05 16:55 xorg.conf.20070605165554
-rw-r--r--   1 root root  4231 2007-05-29 14:52 xorg.conf_backup
-rw-r--r--   1 root root  3415 2007-06-05 16:55 xorg.conf_orig
-rw-r--r--   1 root root  3415 2007-06-05 16:57 xorg.conf.original-0
-rw-------   1 root root   152 2007-06-02 09:33 xorg.conf.save
-rw-r--r--   1 root root 20480 2007-06-05 16:05 .xorg.conf.swp
drwxr-xr-x   2 root root  4096 2007-04-15 13:50 Xresources
drwxr-xr-x   2 root root  4096 2007-04-15 13:59 xserver
-rwxr-xr-x   1 root root  3911 2006-08-07 21:01 Xsession
drwxr-xr-x   2 root root  4096 2007-04-15 14:00 Xsession.d
-rw-r--r--   1 root root   234 2006-08-07 21:01 Xsession.options
-rw-------   1 root root   614 2007-04-15 13:50 Xwrapper.config

This is it.

---

### Post by taurus on 2007-06-05
```
sudo cp /etc/X11/xorg.conf~  /etc/X11/xorg.conf
```

---

### Post by Boris-- on 2007-06-05
ok, when i try to restart x it doesn't load. i had to do sudo mv... again. Taurus and anyone else, would you mind looking at this thread [http://ubuntuforums.org/showthread.php?p=2785961#post2785961](http://ubuntuforums.org/showthread.php?p=2785961#post2785961) (it's got all the details)

Thanks in avance

---

### Post by taurus on 2007-06-05
Edit /etc/X11/xorg.conf

```
gksudo gedit /etc/X11/xorg.conf
```
and change the Driver back to "ati".

And if you don't have X running right now, then you need to use a text base editor.

```
sudo nano -w /etc/X11/xorg.conf
```
Save it with <Ctrl>o and exit with <Ctrl>x.  Then, see if X is running this time.

```
startx
```

---

### Post by Boris-- on 2007-06-05
didn't work. Had to mv again and now im in the starting position again.  And there's no more xorg.conf. Any other ideas? This is pretty frustrating. Is there a way to purge all graphics settings and reinstall them?

---

### Post by taurus on 2007-06-05
```
sudo dpkg-configure xserver-xorg
```

---

### Post by Boris-- on 2007-06-05
Nope, doesn't work. tried this many times prior to your response. Something must be thouroughly messed up. Again, is there a way to purge all graphics settings and reinstall them?

---

### Post by earobinson on 2007-06-07
could you cut and paste exactly what happens when you try?

---

