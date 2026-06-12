---
title: "[SOLVED] gtk-WARNING in terminal"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2007-12-05
Each time I go to edit my /xorg.conf file, I get this warning. Any idea how I get rid of it?
```
john@john-laptop:~$ sudo gedit /etc/X11/xorg.conf
Password:

(gedit:5771): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5771): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5771): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gedit:5771): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```

I am running Dapper

---

### Post by mali2297 on 2007-12-05
Try
```

sudo apt-get install gtk2-engines-pixbuf

```

Also, it is recommended to use 
```

**gksudo** gedit /etc/X11/xorg.conf

```

---

### Post by Papa-san on 2007-12-05
Thanks.
Why the gksudo instead? (I'm not a computer whiz.)

I tried it and got this:```
john@john-laptop:~$ sudo apt-get install gtk2-engines-pixbuf
Password:
Reading package lists... Done
Building dependency tree... Done
gtk2-engines-pixbuf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-laptop:~$


```

---

### Post by mali2297 on 2007-12-05
> **Papa-san said:**
> Thanks.
Why the gksudo instead? (I'm not a computer whiz.)


See [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> 
I tried it and got this:```
john@john-laptop:~$ sudo apt-get install gtk2-engines-pixbuf
Password:
Reading package lists... Done
Building dependency tree... Done
gtk2-engines-pixbuf is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-laptop:~$

```

Post the output of these commands:
```

locate libpixmap
ls /usr/lib/gtk-2.0/

```

Do you have problems running gedit or is it just that you find the warning messages annoying?

---

### Post by Papa-san on 2007-12-05
Thanx for the link! Here's the output:
```
john@john-laptop:~$ locate libpixmap
/usr/lib/gtk-2.0/2.4.0/engines/libpixmap.a
/usr/lib/gtk-2.0/2.4.0/engines/libpixmap.la
/usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so
```

```
john@john-laptop:~$ ls /usr/lib/gtk-2.0/
2.10.0  2.4.0  modules
john@john-laptop:~$

```
Just the warnings being annoying... Something is wrong somewhere, and I'm slightly bothered by it. That's all!

---

### Post by mali2297 on 2007-12-05
> **Papa-san said:**
> Thanx for the link! Here's the output:
```
john@john-laptop:~$ locate libpixmap
/usr/lib/gtk-2.0/2.4.0/engines/libpixmap.a
/usr/lib/gtk-2.0/2.4.0/engines/libpixmap.la
/usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so
```

```
john@john-laptop:~$ ls /usr/lib/gtk-2.0/
2.10.0  2.4.0  modules
john@john-laptop:~$

```
Just the warnings being annoying... Something is wrong somewhere, and I'm slightly bothered by it. That's all!

It seems like the pixmap engines are in the 2.4.0 folder but not the 2.10.0 folder. So symlinking to them from the 2.10.0 folder might solve the issue.
Copy/paste into the terminal:
```

cd /usr/lib/gtk-2.0/2.10.0/engines/

```
If you get an error about nonexistent directory, then 
```

sudo mkdir /usr/lib/gtk-2.0/2.10.0/engines/
cd /usr/lib/gtk-2.0/2.10.0/engines/

```
Continue with linking
```

sudo ln -s /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.a
sudo ln -s /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.la
sudo ln -s /usr/lib/gtk-2.0/2.4.0/engines/libpixmap.so

```
and check
```

ls -l libpixmap*

```

---

### Post by Papa-san on 2007-12-05
I thank you! It has worked. 

I just wish I knew a bit more about how these things work together (or don't)!

I'll file this away and noodle it in hopes that I'll be able to track this kind of thing down for myself one day!

Again, Thanks!

---

