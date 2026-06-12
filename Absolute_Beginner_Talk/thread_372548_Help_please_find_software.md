---
title: "Help please find software"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by roylond on 2007-02-28
After trying to install a usb modem I lashed out and bought a ethernet card and router. :) 
I have downloaded Opera Browser and I am told it is on my desktop but I cannot find it. Is it hidden or how do I get it to reveal its presence. Also where is it in the file file structure,? ie it would be in Program folder in the 'other'  OS which I hope to be able to get away from totally.

Thanks

---

### Post by taurus on 2007-02-28
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
ls -la ~/Desktop
```

---

### Post by roylond on 2007-02-28
This is what I get 

roy@collie:~$ ls -la ~/Desktop
total 8
drwxr-xr-x  2 roy roy 4096 2007-02-28 11:50 .
drwxr-xr-x 19 roy roy 4096 2007-02-28 15:24 ..
roy@collie:~$

But there is nothing showing at all on the desktop

---

### Post by taurus on 2007-02-28
Did you remember where you've saved the Opera?  What about the output of this command?

```
ls -la ~
```

---

### Post by roylond on 2007-02-28
I downloaded Opera with the Add/Remove applications and it was without me intereveining once it started to download and install the program

roy@collie:~$ ls -la ~
total 124
drwxr-xr-x 20 roy  roy  4096 2007-02-28 16:04 .
drwxr-xr-x  3 root root 4096 2007-02-28 11:38 ..
-rw-------  1 roy  roy    24 2007-02-28 16:10 .bash_history
-rw-r--r--  1 roy  roy   220 2007-02-28 11:38 .bash_logout
-rw-r--r--  1 roy  roy   414 2007-02-28 11:38 .bash_profile
-rw-r--r--  1 roy  roy  2227 2007-02-28 11:38 .bashrc
drwxr-xr-x  2 roy  roy  4096 2007-02-28 11:50 Desktop
-rw-------  1 roy  roy    26 2007-02-28 11:50 .dmrc
-rw-------  1 roy  roy    16 2007-02-28 11:50 .esd_auth
drwxr-xr-x  8 roy  roy  4096 2007-02-28 14:50 .evolution
lrwxrwxrwx  1 roy  roy    26 2007-02-28 11:38 Examples -> /usr/share/example-content
drwx------  5 roy  roy  4096 2007-02-28 15:24 .gconf
drwx------  2 roy  roy  4096 2007-02-28 16:10 .gconfd
-rw-r-----  1 roy  roy     0 2007-02-28 15:49 .gksu.lock
drwx------  7 roy  roy  4096 2007-02-28 14:50 .gnome2
drwx------  2 roy  roy  4096 2007-02-28 11:57 .gnome2_private
drwxr-xr-x  2 roy  roy  4096 2007-02-28 13:44 .gstreamer-0.10
-rw-r--r--  1 roy  roy    85 2007-02-28 11:50 .gtkrc-1.2-gnome2
-rw-------  1 roy  roy   159 2007-02-28 15:24 .ICEauthority
drwxr-xr-x  2 roy  roy  4096 2007-02-28 14:47 .icons
drwx------  3 roy  roy  4096 2007-02-28 11:50 .metacity
drwx------  3 roy  roy  4096 2007-02-28 16:05 .mozilla
drwx------  3 roy  roy  4096 2007-02-28 16:04 .mozilla-thunderbird
drwxr-xr-x  3 roy  roy  4096 2007-02-28 11:50 .nautilus
drwx------  9 roy  roy  4096 2007-02-28 16:10 .opera
drwxr-xr-x  2 roy  roy  4096 2007-02-28 14:15 .qt
-rw-r--r--  1 roy  roy     0 2007-02-28 11:51 .sudo_as_admin_successful
drwxr-xr-x  2 roy  roy  4096 2007-02-28 14:47 .themes
drwx------  3 roy  roy  4096 2007-02-28 14:45 .thumbnails
drwx------  2 roy  roy  4096 2007-02-28 11:50 .Trash
drwx------  2 roy  roy  4096 2007-02-28 11:50 .update-notifier
-rw-------  1 roy  roy   117 2007-02-28 15:24 .Xauthority
-rw-r--r--  1 roy  roy  7068 2007-02-28 16:08 .xsession-errors
roy@collie:~$

---

### Post by taurus on 2007-02-28
So it's already installed on your machine.  It should be in Applications -> Internet.  Maybe you need to log out and back in again.  Otherwise, run this from a terminal.

```
opera
```

---

### Post by Songwind on 2007-02-28
> **taurus said:**
> So it's already installed on your machine.  It should be in Applications -> Internet.  Maybe you need to log out and back in again.  Otherwise, run this from a terminal.

```
opera
```
Or even better "opera &" so it gives you your command prompt back after it starts.

---

### Post by roylond on 2007-02-28
Did that now works fine 

Thanks alot

---

