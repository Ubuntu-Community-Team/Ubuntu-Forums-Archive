---
title: "File Server on an old P3 666"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by mikesch on 2006-11-30
I'm not sure if this is the right forum for this question, but since I'm new to Linux, it seems to be a good place to start.  

I have an old P3 666 that is good working order but no longer used.  I'd like to turn it into a file server for my Win XP network at home.  Is Ubuntu a good platform for that kind of use?

Also any suggestions on how to cost effectively do it?

TIA

---

### Post by zgornel on 2006-11-30
Yes and No. If you plan using Windows XP, you will have to use SAMBA to share your files (those on the server) and SAMBA's performance is limited (I get 6MB/s on a 100Mbit connection). I am talking from my own experience so feel free not to take my advice seriously. Apart from speed, it should work quite well (far more stable than windows and you won't even need to install X).

---

### Post by madmetal on 2006-11-30
you can also try freenas 
[http://www.freenas.org/](http://www.freenas.org/)
but i also suggest samba.

---

### Post by mikesch on 2006-12-01
I can understand why Samba might be a little slower, but that seems a little much.  Are you running SATA drives with a RAID controller?  I'm looking at a SATA RAID 10 controller with a pair of high speed drives which one would think would give me fairly high performance at the hardware level.  Now I'm wondering whether this is such a great idea :confused:

---

### Post by zgornel on 2006-12-02
> **mikesch said:**
> I can understand why Samba might be a little slower, but that seems a little much.  Are you running SATA drives with a RAID controller?  I'm looking at a SATA RAID 10 controller with a pair of high speed drives which one would think would give me fairly high performance at the hardware level.  Now I'm wondering whether this is such a great idea :confused:
It's not is you're using a 10/100Mbs NIC.

---

### Post by mikesch on 2006-12-02
Do you have any idea why the network speed would affect SAMBA?  Is it that chatty?

---

### Post by zgornel on 2006-12-03
> **mikesch said:**
> Do you have any idea why the network speed would affect SAMBA?  Is it that chatty?
It's the other way around: for example, if you have a 100Mbit/s line, that's 11-12 MB/s, the real throughput using Samba will be 6-7 MB/s. So there's no reason to create a powerful speedy raid system if you can copy from it with 6 MB/s. A simple hard drive will suffice.

---

