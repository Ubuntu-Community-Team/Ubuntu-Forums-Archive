---
title: "removing software"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by sethdotcom on 2007-05-18
How do I remove things that where preinstalled in ubuntu like gaim, bittorrent,ect

because add/remove wont let me remove some stuff

im not really good with the terminal, but i can do some real basic things in the terminal,

---

### Post by echo $USER on 2007-05-18
I'm not sure because i never remove stuff especially bittorrent, but try...

sudo apt-get remove gaim

---

### Post by misfitpierce on 2007-05-18
Can also use Add/Remove software link in menu :)

---

### Post by sethdotcom on 2007-05-18
> **echo $USER said:**
> I'm not sure because i never remove stuff especially bittorrent, but try...

sudo apt-get remove gaim

I want to remove bittorrent because I use utorrent under wine works much better

---

### Post by echo $USER on 2007-05-18
> **sethdotcom said:**
> I want to remove bittorrent because I use utorrent under wine works much better

did apt-get remove * work?

---

### Post by sethdotcom on 2007-05-18
> **echo $USER said:**
> did apt-get remove * work?

yup thanks i got rid of bittorent 

ubuntu doesnt get software updates via bittorent does it?

---

### Post by teknosexual on 2007-05-19
> **sethdotcom said:**
> yup thanks i got rid of bittorent 

ubuntu doesnt get software updates via bittorent does it?

No, it doesn't. 

You can also check out Synaptic (System > Administration > Synaptic Package Manager) to remove some applications that can't be removed by Add/Remove. If you haven't compiled anything in the Terminal, you shouldn't need to uninstall anything in the Terminal.

---

### Post by Sef on 2007-05-19
Some applications can't be removed because they are an integral part of Ubuntu/Gnome.

---

