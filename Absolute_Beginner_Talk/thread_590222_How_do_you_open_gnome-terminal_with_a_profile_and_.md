---
title: "How do you open gnome-terminal with a profile and multiple tabs?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Barleyman on 2007-10-24
Hi All, I use gnome-terminal everyday and use 4 tabs with specific start points.

Is there a way I could launch gnome-terminal with a specific profile and 4 tabs each one in a different directory?

---

### Post by nick_h on 2007-10-24
Try:
```
gnome-terminal --tab-with-profile=profile1 --working-directory=/home/user/path1 --tab-with-profile=profile2 --working-directory=/home/user/path2
```
you will need to extend it from 2 to 4 tabs.

---

### Post by Barleyman on 2007-10-24
Thanks alot.  I was trying something along those lines, but was unable to get it to open multiple tabs.  Using the --working-directory option works great.

Even better, I didn't mention I want to run specific commands for each tab.  So using the -e option along with your original post, I have exactly what I want.  Saving 2 minutes each time I start my laptop.

```
gnome-terminal --tab-with-profile=profile1 --working-directory=/home/user/path1 --tab-with-profile=profile2 --working-directory=/home/user/path2 -e "script/console"
```

---

