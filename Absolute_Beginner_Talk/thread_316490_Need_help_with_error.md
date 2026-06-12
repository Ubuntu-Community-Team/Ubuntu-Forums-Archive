---
title: "Need help with error"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by anthonysdad on 2006-12-10
Hi. I am brand new to linux. I really don't know what I'm doing, was just glad to get it installed. Anyway it seems cool, but since I installed it I've been getting an error messege when I try to install updates. It's probably something stupid but here it goes.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

It sounds like a foreign language. I pride myself in been very good with windows OS but linux is a whole different world. Hopefully one day though I can say the same about linux too.

Thanks in advance.

---

### Post by ciscosurfer on 2006-12-10
You need to enter that into a Terminal.

To get to the Terminal, go to Applications > Accessories > Terminal

Then enter in the following (you will be prompted for your password--you won't see it being entered in, but it is...once you have entered in your password, press Enter)```
sudo dpkg --configure -a
```

---

### Post by anthonysdad on 2006-12-10
Thank you so much ciscosurfer. It worked like a charm.

---

### Post by ciscosurfer on 2006-12-10
> **anthonysdad said:**
> Thank you so much ciscosurfer. It worked like a charm.Glad I could help out! :KS

---

