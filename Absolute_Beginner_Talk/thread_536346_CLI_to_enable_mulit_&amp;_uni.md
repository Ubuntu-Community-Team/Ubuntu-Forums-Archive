---
title: "CLI to enable mulit &amp; uni"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-08-27
What is the CLI to enable multivers and univers in /etc/apt/sources.list 
something like...
> echo multivers >> /etc/apt/sources.list 
echo univers >> /etc/apt/sources.list 

---

### Post by mendingo84 on 2007-08-27
there is no CLI for that. you have to edit your sources.list using any text editor. my part of sources.list that is of interest to you looks like: 
```
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ro.archive.ubuntu.com/ubuntu/ feisty multiverse universe
deb-src http://ro.archive.ubuntu.com/ubuntu/ feisty multiverse universe

```

```

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
```

---

### Post by ant2ne on 2007-08-27
so, why can't I just
> sudo echo deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe >> /etc/apt/sources.list 
sudo echo deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe >> /etc/apt/sources.list 
instead of uncommenting the lines. So what if there are extra comments?

---

### Post by Lord Illidan on 2007-08-27
I guess you could do that, but is it that much of a hassle?

---

### Post by Henry Rayker on 2007-08-27
perhaps it's a script to set up a new machine or something?

---

### Post by ant2ne on 2007-08-28
> **Henry Rayker said:**
> perhaps it's a script to set up a new machine or something?
:mrgreen:

---

