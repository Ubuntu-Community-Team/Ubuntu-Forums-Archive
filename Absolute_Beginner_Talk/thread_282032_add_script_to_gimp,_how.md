---
title: "add script to gimp, how?"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-10-22
I want to add the pandora script to Gimp but when I try to copy or move the saved script to **usr/share/gimp/2.0/scripts** it says I don't have permission.  How do I put this script in it?

---

### Post by jordanmthomas on 2006-10-22
```
sudo cp *whatever_script_is* /usr/share/gimp/2.0/scripts
```

Or, if you're more comfortable using nautilus,
Alt + F2
```
gksu nautilus
```
and just drag and drop it where it belongs.

---

### Post by Russty of Oz on 2006-10-22
That was a quick reply, thanks I will give that a go.

---

### Post by Russty of Oz on 2006-10-22
GREAT! That worked.  I haven't used the nautilus thing before so I gave that a try and it was so easy!:D 

I will have to write that one down in my little Linux book!;) 

Thanks again :D

---

### Post by jordanmthomas on 2006-10-22
No problem.  I'd rather be helping here than doing my java program...whose due date is ever-approaching.:-#

**oh, and be careful using gksudo nautilus.  You have root privileges with that window and can do some damage if you mess up.

---

### Post by Russty of Oz on 2006-10-22
I will only use it for things where I have to do something like with this one.  I have found before that if I play around with things I don't know about I have to spend MANY HOURS doing a fresh install.  

Good luck with your java!:)

---

### Post by jordanmthomas on 2006-10-22
> I will only use it for things where I have to do something like with this one. I have found before that if I play around with things I don't know about I have to spend MANY HOURS doing a fresh install.When you're learning (which is pretty much for as long as you'll be computing) that's one of the best parts!

---

