---
title: "A problem with editing"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by wat3r on 2006-05-10
Hi!

I've been working with Ubuntu Breezy 5.10 for a little while, but when I earlier was trying to edit the etc/network/interfaces file, I just can't seem to get "control of it". I just can't edit it. I can't find anywhere it says I can open it with root priveligies. I've tried with gedit and Nano.

---

### Post by PhrankDaChickenGeek on 2006-05-10
Fire up a Terminal - "Applications -> Accessories -> Terminal" and type:
```
 sudo gedit /etc/network/interfaces 
```
You'll have to type in your password. You can now do anything you want to this file.

---

### Post by wat3r on 2006-05-10
Thank you :)

edit: I can't seem to open the file in Terminal. But when I open it from Nautilus, it works just fine.

---

