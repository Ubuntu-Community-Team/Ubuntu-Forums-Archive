---
title: "ATI Driver"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Exershio on 2008-01-05
I've got a bit of a problem. I don't really know what ATI driver to use. My system:

Radeon 9550 AGP 4x
P4 2.0ghz CPU
768mb PC2100 RAM

I've tried using the restricted drivers, and they worked, but that's it. XGL/Compiz "looked" fast, but XGL was eating up a lot of my CPU and caused my computer to lag a lot. Typing out a search @ google.com would take a second before the letters that I was typing even showed up.

I also want to play games like World of Warcraft and Neverwinter Nights. I managed to get WoW running, however, the fps was pretty bad. I even used the performance tweaks people suggested, and no go. So I figure it's my driver.

What driver should I really use? And how would I go about installing it?

I tried using Envy to install the right driver, but my god that made everything really bad. Compiz would tear as I moved boxes across my screen and everything felt so slow.

Help would really, really be appreciated. I don't want to go back to Windows because I'm just sick of it, and Ubuntu has everything I need, but it's slow at the moment due to these problems.

---

### Post by JoshuaRL on 2008-01-05
I don't use fglrx on my ATI card, but you might try:

```

aticonfig

```

I think that might help you to configure it for your system.  I can't remember where I saw that, but I hope it helps.

---

### Post by jck99nz on 2008-01-06
The 'unofficial linux ATI driver' wiki is a good resource [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

Follow the 'ubuntu' link on the page; I've used the guide to set up an ATI Radeon X1650.

---

### Post by strabes on 2008-01-06
If you install fglrx version 7.11 you can use compiz without having to use XGL. Don't install 7.12, screen resolution is broken.

---

