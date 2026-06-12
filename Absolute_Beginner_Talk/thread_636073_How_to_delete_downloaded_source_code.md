---
title: "How to delete downloaded source code ?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by coffee81 on 2007-12-09
After reading starcraft.man  "Complete Guide to Installation in Ubuntu" , I found out I ticked the "source code". I have already downloaded and upgraded the system for a week or so.

[IMG]http://i22.photobucket.com/albums/b324/FFManiac1/GUI1.png[/IMG]

So my question is, how can I clean up and delete those source code that I downloaded before ? 

thanks all

---

### Post by taurus on 2007-12-09
You mean
```
sudo apt-get clean
```

---

### Post by coffee81 on 2007-12-09
> **taurus said:**
> You mean
```
sudo apt-get clean
```

i see

that's the command to clean out the downloaded source code, right ?

thanks buddy

---

### Post by mcduck on 2007-12-09
Apt-get doesn't automatically download any source code unless you specifically tell it to do so. So unless you have done that you don't have any source codes installed even if you have installed a bunch of applications.

'sudo apt-get autoclean' will just remove cached .deb packages.

---

