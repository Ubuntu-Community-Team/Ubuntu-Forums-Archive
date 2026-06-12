---
title: "[SOLVED] Gutsy: when I tried to run terminal I was refused because I had exited with"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2008-01-28
Since the terminal session was ended with root in control I was not allowed to start another.  So I tried to reboot.  Now I cannot login.  I tried removing the /.gnome2/session file but that doesn't help.  So I am wondering if I have the same effects but caused by a different file.

---

### Post by taurus on 2008-01-28
What is the error message when you try to log into your account?

---

### Post by ICUR2Ys on 2008-01-28
First I get the session ended in less than 10 seconds, which gives me the option of checking the ~/.x-session-errors file. When I view that file I get a process number followed by Gtk-Warning **  This process is currently running setuid or setgid.  This is not a supported use of GTK+.
This message is repeated for a different process.  Then it says Refusing to initialize GTK+
followed by ?etc/gdm/Xsession:  Beginning session setup...
Can't Create dir /home/dace/Desktop  followed by a list of other directories that it couldn't create.

The final message (x-session-manager: libgnomevfs-Warning **: Unable to create ~/.gnome2 directory : Permission denied  Could not creat per-user gnome configuration directory '/home/dace/.gnome2': permission denied

---

### Post by asmoore82 on 2008-01-28
try "repairing permissions" on your home folder
```
sudo chown -R dace:dace /home/dace
```

(this command actually doesn't do anything with permissions;
it **ch**anges **own**ership of **/home/dace** and everything inside
to **user** and **group** **dace** and **dace**.)

---

### Post by ICUR2Ys on 2008-01-28
I changed the ownership but I still get the same set of messages.

---

### Post by asmoore82 on 2008-01-28
what does this show?```
ls -l /home
```

---

### Post by ICUR2Ys on 2008-01-28
ls -l /home gives

drw-r--r-- 68 dace dace  4096 2008-01-26 18:55 dace
drwxr-xr-x  2   1001   1001  4096 2008-01-26 10:44 charles
drwx------ 2 dace dace 16384 2008-01-18 18:33 lost +found

---

### Post by ICUR2Ys on 2008-01-30
Bump

---

### Post by taurus on 2008-01-30
Boot into recovery mode from GRUB menu and run

```
chmod -R 755 /home/dace
chmod 644 /home/dace/.dmrc
shutdown -r now
```
Now, see if you can log into your account, dace.

---

### Post by ICUR2Ys on 2008-01-30
Thank you very much.  I am now able to log back in.  I really appreciate you guys.

---

### Post by asmoore82 on 2008-01-30
> **taurus said:**
> Boot into recovery mode from GRUB menu and run

```
chmod -R 755 /home/dace
chmod 644 /home/dace/.dmrc
shutdown -r now
```
Now, see if you can log into your account, dace.

Yikes! One should almost **_never_** use `chmod` to set
**absolute permissions**(octal digits such as 755) **recursively**(-R)
This will cause every single file under that directory to be executable.

`chmod` accepts a syntax it calls "symbolic mode" to set or clear read/write permissions
without touching execute permissions.
So the proper command to run in this case would be:
```
chmod -R o+rw /home/dace
```
``o+rw'' = "owner(add)read&write"

---

