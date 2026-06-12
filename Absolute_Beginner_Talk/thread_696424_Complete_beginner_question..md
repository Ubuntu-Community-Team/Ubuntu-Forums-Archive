---
title: "Complete beginner question."
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by SFalbowski on 2008-02-14
I've already installed the Mythbuntu command centre, and it didn't bring me into the command centre window. I used this guide [https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop#head-d1fc09905631f0bfc629909e8babbd2a882383f7](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop#head-d1fc09905631f0bfc629909e8babbd2a882383f7) 
and got all the way until the "install mythtv" section. Although it installed, (it's in the "installed applications" section of the add/remove window.) I'm an absolute beginner with all linux. Please help me.

---

### Post by emarkd on 2008-02-14
I think you still have to launch Myth after MythBuntu boots.  Maybe under Sound & Video > MythTV Frontend

I'm not sure if that's exactly right, but look around the menus.

---

### Post by SFalbowski on 2008-02-14
Tried it. It didn't work. I've scoured the filesystem for the launch file, and I just can't find it. It never appeared in the menu.

---

### Post by emarkd on 2008-02-14
Ok, try it from the command line.  Launch a terminal from Accessories and run:

```
mythfrontend
```

and see what happens

---

