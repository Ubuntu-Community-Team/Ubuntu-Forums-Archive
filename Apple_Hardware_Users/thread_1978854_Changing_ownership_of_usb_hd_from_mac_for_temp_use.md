---
title: "Changing ownership of usb hd from mac for temp use with 12.04"
date: 2012-05-12
forum: Apple Hardware Users
---

### Post by moonbasepi on 2012-05-12
I am in a sticky situation. I need to borrow my mac's Iomega usb HD to back-up my Ubuntu 12.04 but obviously the permissions will not allow this. Is it possible to change the ownership of the drive without making it useless to the mac? Thanks in advance.

---

### Post by aflyingturtle on 2012-05-18
Not sure if this helps, but if you are getting a "you do not have permissions to open this file" you should try running nautilus in sudo. So open up terminal (ctrl+alt+t) and then type in ```
 gksudo nautilus 
```Then use that nautilus window to browse the usb drive.

---

### Post by hansdown on 2012-05-19
Welcome to the forum, moonbasepi.

Just like to add to aflyingturtle's good advice.

Right click the iomega drive, left click, 

properties> permissions.

Hopefully you can change the permissions to

"read and write".

I haven't tried this with the apple file system, so... I'm crossing my fingers, and eyes, and toes.

---

### Post by moonbasepi on 2012-06-09
> **aflyingturtle said:**
> Not sure if this helps, but if you are getting a "you do not have permissions to open this file" you should try running nautilus in sudo. So open up terminal (ctrl+alt+t) and then type in ```
 gksudo nautilus 
```Then use that nautilus window to browse the usb drive.

Just wanted to say thanks for the quick response. I couldn't change permissions but was able to accomplish my task. Thanks

---

### Post by moonbasepi on 2012-06-09
> **hansdown said:**
> Welcome to the forum, moonbasepi.

Just like to add to aflyingturtle's good advice.

Right click the iomega drive, left click, 

properties> permissions.

Hopefully you can change the permissions to

"read and write".

I haven't tried this with the apple file system, so... I'm crossing my fingers, and eyes, and toes.

Each time I tried this I was informed the drive was owned by a different entity each time. Weird. It went from "nobody" to "user 23" to me. At one point I was able to change a folders ownership and all enclosed folders but it didn't actually do anything. I want to thank both of you for the quick response I am certainly not used to that!

---

