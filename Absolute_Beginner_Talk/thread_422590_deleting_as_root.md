---
title: "deleting as root"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Cornbreadly on 2007-04-25
i made a boo boo and was leafing through the output files of an attempting photorec recovery as root when I relized that the files i was deleleting from that were not freeing up any disk space.  Now it look like I have lost about 25 gigs to the ether.  Did I miss something in ubuntu 101?  Why isnt root deleting the same as would my normal use?

---

### Post by eentonig on 2007-04-25
As a normal user, deleting is actually "move to trash", so basically the same behavior, not?

---

### Post by Cornbreadly on 2007-04-25
thats what i thought... but that is not the case it seems

i ran photorec under sudo if that means anything.  I have no idea why the deleted files didnt free up space.

---

### Post by Cornbreadly on 2007-04-26
ubuntu... despite the hype... does not have the power to magically correct itself overnight.

Which is ok.  Does anyone have a thought onto how I can again discover what has happened to a large piece of my HD?

---

### Post by Skrynesaver on 2007-04-26
```
sudo du / |sort -n
```
Will give you a pointer, it will return the directories on your system from least data to most

---

