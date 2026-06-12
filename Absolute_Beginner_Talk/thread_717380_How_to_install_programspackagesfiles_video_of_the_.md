---
title: "How to install programs/packages/files video of the things needed to be installed"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Gigidy5 on 2008-03-07
KK


here's what the title of the things i want to install are

Phun_beta_3_12_linux32.tar.bz2

and

firefox-3.0b3.tar.bz2

what to do?

they are both on my desk top.

here's a horrible video of what they look like

Compression=shit
[http://www.youtube.com/watch?v=OXT9mmd0zOc](http://www.youtube.com/watch?v=OXT9mmd0zOc)

---

### Post by amingv on 2008-03-07
This will help (it even has some explanatory videos):
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Also, you can install those things from the repositories (the guide explains how).

---

### Post by S15_88 on 2008-03-07
i find sudo apt-get install the easiest way to do stuff....
with tarballs(tar) u need to unpack them and make them then install them alot of times you get weird errors other times it works fine.  with apt-get it does all that for you and you can watch it all happen in the terminal

Thanks, ALain

---

### Post by steveneddy on 2008-03-07
Synaptic Package Manager

System --> Administration --> Synaptic Package Manager

search for Firefox 3

can't help you with Phun. Looks cool though.

---

### Post by Vadi on 2008-03-07
Phun doesn't need an installation. Just right-click, extract archive, you'll get a folder. Inside the folder, there will be a file called "phun" - double-click on it, and it'll start.

(If it doesn't start, right-click, properties, permissions, enable it to be executable, and double-click to start)

---

### Post by hyper_ch on 2008-03-07
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

[http://www.psychocats.net](http://www.psychocats.net)

[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by jspangler on 2008-03-07
Gigidy,

If you install the build essential package, that will help you avoid many errors when install files from tarballs.

So, in the terminal, post:

```
sudo apt-get install build-essential
```

---

### Post by steveneddy on 2008-03-07
> **Vadi said:**
> Phun doesn't need an installation. Just right-click, extract archive, you'll get a folder. Inside the folder, there will be a file called "phun" - double-click on it, and it'll start.

(If it doesn't start, right-click, properties, permissions, enable it to be executable, and double-click to start)

I couldn't get executable to run, but I noticed it there and knew there was something to it.

I may try DLing this again to play with it.

---

### Post by Vadi on 2008-03-07
If you're on 64bit, you should download the 32bit one still - the 64bit one doesn't work properly and as I saw, the program doesn't make use of dualcores anyway.

---

### Post by Gigidy5 on 2008-03-07
thank you all they worked 

phun folder
firefox synaptic

---

