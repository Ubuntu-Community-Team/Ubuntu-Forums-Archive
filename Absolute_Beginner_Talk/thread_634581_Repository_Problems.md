---
title: "Repository Problems"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by techmunkey on 2007-12-07
I recently tried to add AWN and Compiz repositories. I added them everything went fine. I have been trying to learn more about the console and nerfed my sources.lst file. I managed to get a few repositories going but have not updated in a week and I know my stuff is behind. 

Can anyone please assist in pointing me to a good article, wiki, blog etc. on managing repositories. I want to make sure I have some good ones added.

---

### Post by reacocard on 2007-12-07
> **techmunkey said:**
> I recently tried to add AWN and Compiz repositories. I added them everything went fine. I have been trying to learn more about the console and nerfed my sources.lst file. I managed to get a few repositories going but have not updated in a week and I know my stuff is behind. 

Can anyone please assist in pointing me to a good article, wiki, blog etc. on managing repositories. I want to make sure I have some good ones added.

Here's a part of my sources.list:
```
deb http://mirrors.kernel.org/ubuntu/ gutsy main universe restricted multiverse
deb-src http://mirrors.kernel.org/ubuntu/ gutsy main universe restricted multiverse 

deb http://security.ubuntu.com/ubuntu/ gutsy-security main universe restricted multiverse
deb-src http://mirrors.kernel.org/ubuntu/ gutsy-security main universe restricted multiverse

deb http://mirrors.kernel.org/ubuntu/ gutsy-updates main universe restricted multiverse
deb-src http://mirrors.kernel.org/ubuntu/ gutsy-updates main universe restricted multiverse

deb http://mirrors.kernel.org/ubuntu/ gutsy-backports main universe restricted multiverse
deb-src http://mirrors.kernel.org/ubuntu/ gutsy-backports main universe restricted multiverse 



### 3rd party repos ###

deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

That has all the main ubuntu repositories and one for AWN.  You shouldn't need repos for compiz, compiz is included in the main ubuntu repositories.

In general it's best to keep the number of 3rd party repos you use to a minimum, they have been known to conflict with each other and cause breakage.

---

### Post by techmunkey on 2007-12-08
Thanks that is exactly what I needed!

---

