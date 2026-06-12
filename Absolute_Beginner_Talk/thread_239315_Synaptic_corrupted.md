---
title: "Synaptic corrupted?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by stoer on 2006-08-19
hi all.
Just noticed Synaptic is inaccessable, get an error loading shared libraries...

steve@laptop:~$ sudo synaptic
Password:
synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory
steve@laptop:~$ 

I was working on Hellanzb yesterday, further nothing dramatic.  Only files i remember working on were in my Home directory.

Anybody have any ideas on how to recover this situation please?
Thanks in advance. Steve.

---

### Post by angkor on 2006-08-19
I have no idea what could be the cause of this but that missing file is in the package libvte4.

```
 apt-file search libvte.so.4
libvte4: usr/lib/libvte.so.4
libvte4: usr/lib/libvte.so.4.5.0
```

```
apt-cache search libvte4
libvte4 - Terminal emulator widget for GTK+ 2.0 - runtime files
```

Do you have that package installed? If not try installing it with apt-get and try synaptic again (with gksudo in stead of sudo just to be sure).

---

### Post by David Corrales on 2006-08-19
**sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4**
It's from the Compiz/quinn updates.

---

### Post by stoer on 2006-08-19
Hi,
mind running the code by me....
gksudo get-apt ???????????

I'm very new to this :confused: 

And thanks.

---

### Post by stoer on 2006-08-19
> **David Corrales said:**
> **sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4**
It's from the Compiz/quinn updates.


Yep! that worked. Synaptic back and working.
(what was the problem? tried the forum but couln't find it myself.)

And many thanks.
Steve.

---

### Post by Loffe_ on 2006-08-19
I got the same problem. I couldn't find it in the forums...

I tried making a symbolic link and it worked as in this thread.

Weird bug though..

//Loffe

---

### Post by bullgr on 2006-08-19
> sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
It's from the Compiz/quinn updates.

i had the same problem. it comes with the last package update i make. there is some problem in compiz updates and synaptic was dead.
thanks for the solution...

---

### Post by it.henrik on 2006-08-19
It helped me too... thnx heaps.

I so regret installing compiz :(

---

### Post by angkor on 2006-08-19
> **stoer said:**
> Hi,
mind running the code by me....
gksudo get-apt ???????????

I'm very new to this :confused: 

And thanks.

I tried to say you should use gksudo when starting graphical applications as root in stead of sudo:

```
gksudo synaptic
```

Don't know why exactly but it seems to be good practice.

The problem was that the compiz repositories installed a newer version of the above mentioned package and synaptic apparently needed the old version to work.

---

### Post by angkor on 2006-08-19
> **it.henrik said:**
> 
I so regret installing compiz :(

Why is that? You can always get rid of it.

---

