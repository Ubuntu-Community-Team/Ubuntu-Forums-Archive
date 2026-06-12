---
title: "Problem with watching videos"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by theKvakkis on 2007-11-08
I have just started out with Linux (Ubuntu 7.10), and now i want to watch some video on my computer. The files is AVI / XviD or something.

I tried to download the VLC media player, but on the page I just couldn't, find out how to download the files.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

How do i do it?

Is there any other media player that will work bether for me?

Pleas help.

---

### Post by rolnics on 2007-11-08
It might be as easy for you to look under your SYSTEM menu and find Synaptic Package Manager, then do a search for VLC check the install tick box and then apply.

Hope that helps and welcome to Ubuntu

---

### Post by philinux on 2007-11-08
In the menus, System, Admin, synaptic search for vlc and mark it for installation.

By the way the pre-installed totem ,named Movie player will play these files.

---

### Post by taurus on 2007-11-08
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install vlc
```

---

### Post by rolnics on 2007-11-08
> **philinux said:**
> Admin,

Opps forgot that!!!! :lolflag:

---

### Post by theKvakkis on 2007-11-08
> **philinux said:**
> By the way the pre-installed totem ,named Movie player will play these files.

No, it wouldnt. It says that Ii am missing codecs.


And the managerthing don't find VLC:/

---

### Post by philinux on 2007-11-08
Ah you need to go to add/remove and install/tickbox all the gstreamer entries under sound and video then totem will do its stuff

---

### Post by LowSky on 2007-11-08
go into add/remove

type in VLC and in the right menu choose all availble packages it will show up

---

### Post by FierceDeity on 2007-11-08
Totem will play most of the files if you tell it to search for the Codec...

But I still prefer vlc

---

### Post by philinux on 2007-11-08
Something changed with Gutsy, totem now plays everything well including wmv. It even plays .ra streaming audio.

---

