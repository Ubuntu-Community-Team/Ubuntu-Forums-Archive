---
title: "How to simply upgrade from 5.04 to the latest"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by esteban2x on 2006-04-12
My CD says it's Ver 5.04.  It took a long time to get this thing loaded and working great. However, is there a sure fire simple way to upgrade?

Thanks

---

### Post by aysiu on 2006-04-12
```
sudo apt-get update
sudo apt-get install ubuntu-desktop (if you're using Ubuntu)
sudo apt-get install kubuntu-desktop (if you're using Kubuntu)
sudo cp /etc/apt/sources.list /etc/apt/sources.list_hoary
sudo nano /etc/apt/sources.list
``` Replace all the *hoary* references with *breezy* (or *dapper*, if you're feeling adventurous). Save (control-x), confirm (y), and exit (Enter) ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Jason_25 on 2006-04-12
If you want to go to dapper, you should go to breezy first.

---

### Post by esteban2x on 2006-04-12
You guys are incredible  with your support. I'm amazed. Ok, is there a command to find out what Version of Ubuntu is installed on my machine? I did an upgrade and install so shouldnt it say 5.10 somewhere?

---

### Post by aysiu on 2006-04-12
[QUOTE=Jason_25]If you want to go to dapper, you should go to breezy first.[/QUOTE] Can you explain some of the mechanics behind this--why you can't jump up two versions?

---

### Post by stuporglue on 2006-04-12
> Can you explain some of the mechanics behind this--why you can't jump up two versions?

I'll bet it would work, it just probably wouldn't be considered a "supported" upgrade path.

---

### Post by aysiu on 2006-04-12
[QUOTE=esteban2x]Ok, is there a command to find out what Version of Ubuntu is installed on my machine? I did an upgrade and install so shouldnt it say 5.10 somewhere?[/QUOTE] Press Control-Alt-F1. Take a peek. Then press Control-Alt-F7.

---

### Post by esteban2x on 2006-04-12
Control alt f1 turns my screen black..??????

---

### Post by deathkiss on 2006-04-12
cat /etc/issue

---

