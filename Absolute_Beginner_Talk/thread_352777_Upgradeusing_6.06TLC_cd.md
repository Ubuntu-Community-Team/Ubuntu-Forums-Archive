---
title: "Upgradeusing 6.06TLC cd?"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by acidblue on 2007-02-03
I'm running 5.1 breezy edition i want to upgarde to 6.06.
I have a  6.06 install/live cd can i use this to upgarde??
Or do i have to format HD and install 6.06?
Using apt-get or synaptic to upgrade i am told 
is a bad idea since i'm using a much older version (5.1)

---

### Post by neverett on 2007-02-03
> **acidblue said:**
> I'm running 5.1 breezy edition i want to upgarde to 6.06.
I have a  6.06 install/live cd can i use this to upgarde??
Or do i have to format HD and install 6.06?
Using apt-get or synaptic to upgrade i am told 
is a bad idea since i'm using a much older version (5.1)

In my experience, using apt-get in the terminal to upgrade has worked great.  There is an alternate CD that you can download, but as far as I know, you cannot use the Live CD to upgrade.

---

### Post by acidblue on 2007-02-03
Ok I'm downloading the alternate cd image right know.
Iv'e seen a web page on this site that describes how to 
upgarde using the alternate cd image but can't remember
where i saw it
any help?

---

### Post by neverett on 2007-02-03
Try looking at this thread:

[http://www.ubuntuforums.org/showthread.php?t=208906](http://www.ubuntuforums.org/showthread.php?t=208906)

---

### Post by acidblue on 2007-02-03
Ok great.
but i want to use he cd image withouit burnning it
since i don't have a burnner, 
so what is the commands for mounting the image??

---

### Post by neverett on 2007-02-03
I can't help you there... I'm not sure how to mount a CD image.  To be brutally honest, I would use the apt-get upgrade call.  Sorry that I can't help you any further.

---

### Post by Buck2348 on 2007-02-03
> **acidblue said:**
> 
so what is the commands for mounting the image??
```
sudo mkdir /mnt/iso
sudo mount -o loop -t iso9660 /home/username/Desktop/xubuntu.iso /mnt/iso
```
where "/home/username/Desktop/xubuntu.iso" is the full path to the iso file.

Buck

---

