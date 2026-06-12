---
title: "how to install libx11?"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by shishio on 2006-03-07
Hi,

how do you install libx11? I downloaded the debian packages, but I don't see any ./configure or make install options in them... 

How are you suppose to install this?

Thanks.

---

### Post by TrendyDark on 2006-03-07
You can get that package from the repositories using synaptic or apt-get

```
sudo apt-get install libx11-6
```

---

### Post by TrendyDark on 2006-03-07
*woops double posted, sorry*

---

### Post by shishio on 2006-03-07
I tried that, and I even tried re-installing, but when I try to ./configure gtk I get an error stating that I'm missing libx11.... any ideas?

---

### Post by LordBug on 2006-03-07
You're looking for the libX11 DEV files then.  It'll install the necessary header files for you to compile anything that needs them.  It should take care of that error.  Am I correct that you're trying to compile GTK?

---

### Post by shishio on 2006-03-07
Right, I'm trying to compile gtk 2.8.13, and during the ./configure sequence it spits on the missing libx11 error. I believe that I have tried re-installing the dev files for libx11. I was wondering if there's any configuration file or .so file that I might need to edit somewhere...

---

### Post by LordBug on 2006-03-07
Shouldn't have to modify anything. I do question why you're compiling GTK from scratch though.  GTK is installed by default with Ubuntu.

---

### Post by shishio on 2006-03-07
I'm trying to install it because I'm actually trying to install wxGT.. .I forget the exact name (not near my Linux computer). It's some kind of widgets library that isn't installed with ubuntu and I need it to install gEDA...

---

### Post by nudaz on 2006-06-29
I'm trying to get VMware server running on ubuntu-server.
I need libx11 or libx11-dev for VMware to verify install key,
but when I do
```
sudo apt-get install libx11
``` and similar I get E: package not found or something, also tried
```
sudo apt-cache search libx11
``` (or libx or x11 etc) but I don't find it.
When I tried to update, I get a lot of 407 proxy authentication errors.

Any ideas?

---

