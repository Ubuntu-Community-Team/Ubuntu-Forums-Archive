---
title: "synaptic package manager error"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by joelcont on 2007-05-26
when tryin to open synaptic package manager i get this error


> E: Dynamic MMap ran out of room
E: Error occurred while processing tetex-base (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


please help

---

### Post by Ek0nomik on 2007-05-26
Try:

```
sudo dpkg --configure -a
```

---

### Post by joelcont on 2007-05-26
i am sorry same thing ...
> 
E: Dynamic MMap ran out of room
E: Error occurred while processing tetex-base (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

thank you

---

### Post by Ek0nomik on 2007-05-26
I have been looking around, and this has been suggested, but please note, I have no idea what this does or if it will work for everyone:

Add the following line to either /etc/apt/apt.conf or /etc/apt/apt.conf.d/70debconf

```
APT::Cache-Limit "8388608"
```

---

### Post by Ek0nomik on 2007-05-26
Also, check out this blog post, it may help you (there are comments that may help too)

[http://valery.bgit.net/blog-en/2006/11/13/apt-get-e-dynamic-mmap-ran-out-of-room/](http://valery.bgit.net/blog-en/2006/11/13/apt-get-e-dynamic-mmap-ran-out-of-room/)

---

### Post by joelcont on 2007-05-26
thank you for your fast reply but i am so sorry its my very first time using ubuntu and i started to like it ... but i dont know were is  /etc/apt/apt.conf.d
Thank you very much again

---

### Post by joelcont on 2007-05-26
i am so sorry i fixed it not dat way but somehow i restored everithing but anyways how u edit thos files ?

---

### Post by Ek0nomik on 2007-05-26
If you want to edit a file, you can always use the Terminal.  I will explain the GUI (Graphical User Interface) below as well.

Terminal:

```
nano filename
```

You use Control+X to exit, Control+O to Write Out (save).

If it says you don't have permission to write to it (it's read only), than you just put sudo before the first part of the command (nano).

So it would be:

```
sudo nano filename
```

This will give you temporary root privileges and you can edit the file however you want.

If you want to use a graphical way of editing files, go to Places/Home

Than just navigate to the directory you need and open the file and edit it to your desire.

If you need that temporary root privilege again, open a Terminal and type:

```
gksudo nautilus
```

This will open a file browser with root privileges for you.

If you have more questions, feel free to ask.

---

