---
title: "Video group"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by ibizatunes on 2008-02-08
In ubuntu 7.10 i need to add a user to the video editing group, what is it called, i cant see a video group in group management
Many thanks

---

### Post by talsemgeest on 2008-02-08
Well if that group isn't there then there shouldn't be any need to add any users to it should there?

---

### Post by ibizatunes on 2008-02-08
There is because picasa has a problem long story and i maybe found a fix. I need the user to be in the video editing group......

---

### Post by tsh on 2008-04-23
```
sudo usermod -a -G video USERNAME
```
Or just edit the /etc/group file, and remember to log out and back in after making the change. This is a bug in the group management tool.

Maybe related, if you end up with a blank brown screen after doing this, try removing your .metacity directory (which will trash some settings, but save your sanity)

---

