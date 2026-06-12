---
title: "Very annoying problem I am having with install of 7.10"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-12-26
Hi I can not cd into certain directories, specifically it seems directories in my /home folder. I try to cd into directories that are clearly there from my home directory i.e."cd /user" and it says the directory doesnt exist??? Even though when I use "ls" the directory comes up. 

Actually it seems more widespread then that since the same thing happens to media such as cds I have in also.

---

### Post by Rocket2DMn on 2007-12-26
When you put a / in front, that is referring to the root of the filesystem where they have folders like home, etc, boot, proc, and so on...
So, when you cd from terminal you just do
```
cd foldername
```

---

### Post by Josh1 on 2007-12-26
> **Rocket2DMn said:**
> When you put a / in front, that is referring to the root of the filesystem where they have folders like home, etc, boot, proc, and so on...
So, when you cd from terminal you just do
```
cd foldername
```

Yep, and adding onto what Rocket said, to change into your home directory from anywhere, you can do:
```
cd ~
```

To change into say.. /home/yourname/iloveubuntu
```
cd ~/iloveubuntu
```

Enjoy.

---

