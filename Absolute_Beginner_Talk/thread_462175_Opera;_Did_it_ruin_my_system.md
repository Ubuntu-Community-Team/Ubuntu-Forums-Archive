---
title: "Opera; Did it ruin my system?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by kevCast on 2007-06-02
I can't open Synaptic because I tried to install Opera from the official Opera website. There was no archive created, so it has no idea what to do with it, so it stops when it hits Opera. This is what I get when I try to run sudo apt-get upgrade:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package opera needs to be reinstalled, but I can't find an archive for it.

Synaptic's error looks like this:

E: The package opera needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I don't know what to do. Can someone please help?

---

### Post by blue_shift on 2007-06-02
Try this?

```
sudo apt-get remove opera
```

---

### Post by dpzektor on 2007-06-02
Download the .deb package from Opera's website, double click and re-install. That should work.

---

### Post by blue_shift on 2007-06-02
The current opera package has to be removed first though, no?

---

### Post by dpzektor on 2007-06-02
> **blue_shift said:**
> The current opera package has to be removed first though, no?

Well, I would think that double clicking on the deb and choosing "reinstall package" may correct the issue.

---

### Post by blue_shift on 2007-06-02
You may well be correct, just the ```
E: can't find an archive for it
``` made me apprehensive.

---

### Post by zvacet on 2007-06-02
Just double click on package.It will install Opera.There should be no trouble but just in case something happened(I don´t belive it will) post it here.Opera  is easy package to install.

---

### Post by kevCast on 2007-06-02
> **blue_shift said:**
> Try this?

```
sudo apt-get remove opera
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package opera needs to be reinstalled, but I can't find an archive for it.

That's what I got.

---

### Post by kevCast on 2007-06-02
> **dpzektor said:**
> Download the .deb package from Opera's website, double click and re-install. That should work.

[[IMG]http://img502.imageshack.us/img502/503/screenshotpr6.th.png[/IMG]](http://img502.imageshack.us/my.php?image=screenshotpr6.png)

I checked the permissions, it's allowed to execute as a program.

---

### Post by shae on 2007-06-02
```
sudo dpkg -r opera
```

or

```
sudo dpkg -r [name of opera package]
```

---

### Post by kevCast on 2007-06-02
> **shae said:**
> ```
dpkg -r opera
```

or

```
dpkg -r [name of opera package]
```

sudo dpkg -r opera
dpkg: error processing opera (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 opera

and the second one didn't do anything but give me instructional help on what to do with dpkg.

---

### Post by Austin_KW on 2007-06-02
You need to force it
dpkg --force-remove-reinstreq opera

Also check the sum on your .deb file
md5sum ~/Desktop/opera_9.21-20070510.6-shared-qt_en_i386.deb
 I think the result should be 
2eda8f03bc2dac6e1b824a34a7d80a8b  opera_9.21-20070510.6-shared-qt_en_i386.deb

---

