---
title: "[SOLVED] get pictures off razr v3 in ubuntu"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-08-10
how can you do this in ubuntu?  i've tried moto4lin, but no luck.  i'm gonna give it another go though.  any other ideas while i'm at it?

---

### Post by SOULRiDER on 2007-08-10
Your phone should work with kmobiletools
[http://www.kmobiletools.org/](http://www.kmobiletools.org/)

that program is aimed at KDE users so you might wanna try something else, this can be a temporary alternative though.

---

### Post by ed67 on 2007-08-11
I have a Bluetooth dongle I picked up at Wal-Mart.  Ubuntu recognized it immediately, I paired it to my Razr and opened the Bluetooth Obex client.  Works like a charm.

---

### Post by tact on 2007-08-11
I use moto4lin to connect to my V3 razr.  Its a bit of a trick to get working but there are guides online.  Google or search.

---

### Post by Niklas Schröder on 2007-08-11
yeah.  i'm still working on moto4lin.  but what i can't figure is that i got the phone to connect on p2kcommander on windows, but i couldn't find the pictures anywhere.  and when i followed guides to upload wallpapers/ringtones, it showed up that it was uploaded on the phone, but it wouldn't come up in the menus.  did cingular lock the phones for the new v3s?

---

### Post by tact on 2007-08-11
Ahhh ok - I don't know about vendors locking the phone.  Under ubuntu (feisty) using moto4lin here is how I find pics on my V3 Razr:

1.  You gotta install moto4lin as a user, not sudo, but you gotta run it as sudo.
Have the phone plugged in first.
```
sudo moto4lin
```

2.  moto4lin sees the phone connected in AT mode.  I click on "connect" and after some AT commands get a response it changes to P2K mode

3.  then click on the "Update list" button

Now you will have in the left most panel an icon representing the phone, under that an icon representing the drive in the phone calles /a.   Under that a folder called mobile and under that pictures.

---

### Post by Niklas Schröder on 2007-08-11
ok.  i'll try that.  but one problem.  i only have one user on my machine and that's the admin account.

---

### Post by Niklas Schröder on 2007-08-12
never mind about my last post.  i got it working and was able to finally look at the file system.  but i found that my phone isn't just a plain v3.  it's really a v3r.  that makes a BIG difference.  there have been changes made in the firmware that make it harder to mod.  this makes it impossible for me to do anything noticeable (other than change the outer lcd image) without motorola phone tools.  i think i'm just gonna buy that and end my misery.  ;)  thanks for the help guys.

---

### Post by usererror on 2007-11-24
I've got a V3m that I cannot get to connect.  I think it's supposed to be in P2K mode, but it always says Mode: AT in the bottom of the moto4lin screen...even if i go to preferences and change it to P2K any, ideas?

Thanks.

---

### Post by Guitar John on 2007-12-26
Removed

---

