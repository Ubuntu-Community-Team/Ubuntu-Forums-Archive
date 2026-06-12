---
title: "transfering files"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by akash238 on 2007-12-29
i just installed ubuntu 7.04 
i was wondering how you can transfer all my music, videos,and documents from vista to ubuntu

---

### Post by p_quarles on 2007-12-29
Is your Vista partition mounted currently? If so, it's pretty easy to grab the files over to your Ubuntu partition using the file manager.

If you're not sure, run this and post the output:
```
sudo fdisk -l
```

---

### Post by hyper_ch on 2007-12-29
don't you want to test Ubuntu a bit longer before you start moving all that?

---

### Post by akash238 on 2007-12-29
how can tell if my vista partition is mounted correctly
sorry im a complete noob when it comes to ubuntu

---

### Post by p_quarles on 2007-12-29
> **akash238 said:**
> how can tell if my vista partition is mounted correctly
sorry im a complete noob when it comes to ubuntu
Open a terminal (press ALT-F1) and type the command I gave in my last post. Then, you can cut-and-paste the output into your next message.

---

### Post by eolson on 2007-12-29
An alternate way if you have a USB Flash Drive handy.  Copy the over to the flash then from the flash to Ubuntu.  Round about,  but works.  If you leave them on the Flash, you've also got a backup.

---

### Post by nick_h on 2007-12-30
> If so, it's pretty easy to grab the files over to your Ubuntu partition using the file manager.

or leave the files where they are and access the through Ubuntu.

I agree with you that the output of:
```
sudo fdisk -l
```
would be useful to see if the partition is recognised.  Then the output of:
```
cat /etc/fstab
```
to show what is mounted by default.

---

### Post by Martje_001 on 2007-12-30
Just go to 'Locations (at top of screen) --> Computer' and look for your windows drive.

---

