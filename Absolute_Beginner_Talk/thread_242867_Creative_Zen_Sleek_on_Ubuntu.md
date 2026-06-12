---
title: "Creative Zen Sleek on Ubuntu"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by slibuntu on 2006-08-24
Ok, i've tried using Gnomad2, but i can't get it to detect my Zen Sleek, i've checked lsusb, and it is there. Any ideas?
Its the 2.8.1 version i'm using, i tried to download the newer one but when i try to ./configure i get a list of bits i seem to be missing, help please!

---

### Post by slibuntu on 2006-08-24
<bump>

---

### Post by msak007 on 2006-08-24
> **slibuntu said:**
> Ok, i've tried using Gnomad2, but i can't get it to detect my Zen Sleek, i've checked lsusb, and it is there. Any ideas?
Its the 2.8.1 version i'm using, i tried to download the newer one but when i try to ./configure i get a list of bits i seem to be missing, help please!
 
It could be one of 2 things - either your player is an MTP player that requires an extra set of libraries, or the default installation doesn't know your device and the config file will have to be modified. For starters, can you please post the output of lsusb?
 
EDIT: Post the output of lsusb anyway, but I just found some info that indicates this is indeed an MTP MP3 player. Follow the link in my sig for a how to on getting your device working with Gnomad, and if you have any problems post them in that thread.

---

