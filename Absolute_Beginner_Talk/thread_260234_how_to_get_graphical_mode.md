---
title: "how to get graphical mode"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Newbie in Linux World on 2006-09-18
Hi, now i hav installed ubuntu, but when i reboot it starts in text mode !! I want it in graphical mode.

Can some one help me please ?

---

### Post by jd65pl on 2006-09-18
log in then try

```
startx
```

 to see if the xserver will start

---

### Post by Newbie in Linux World on 2006-09-18
when I type "startx" I get this mesage: -bash: startx: command not found 

????

---

### Post by Perfect Storm on 2006-09-18
Is it a server installation you made?

---

### Post by Newbie in Linux World on 2006-09-18
I don`t think soo, I used the "Desktopp" cd !!

---

### Post by Brunellus on 2006-09-18
> **Newbie in Linux World said:**
> I don`t think soo, I used the "Desktopp" cd !!
1)  Did this install and run successfully before?

2) If yes to (1) did you change anything?

---

### Post by Perfect Storm on 2006-09-18
It looks like there isn't a X installed. 
Try:
```
sudo aptitude install ubuntu-desktop
```

---

### Post by buffy^ on 2006-09-18
login using your username and password, then type "sudo apt-get install gnome-desktop"

or kde-desktop

---

### Post by Newbie in Linux World on 2006-09-18
tnx, but i get this mesage: E: couldn`t find package "gnome/kde"-desktop

Do I have to tell where to look for it ? The CD is in the player

---

### Post by Newbie in Linux World on 2006-09-18
when i type: sudo aptitude install ubuntu-desktop
i get this: Couldn`t find any package whose name or description matched "ubuntu-desktop", and the same with kde or gnome

---

### Post by jd65pl on 2006-09-18
buffy^

When installing a desktop environment "aptitiude" should be used instead of "atp" it handles dependancies better.

Like Artificial Intelligence said use

```
sudo aptitude install ubuntu-desktop
```

---

### Post by buffy^ on 2006-09-18
/me learns more and more and more. :D


Ok so, do you currently have an internet connection to download these files from?

---

### Post by Newbie in Linux World on 2006-09-18
hmm yes, where do I find them ?

---

### Post by Brunellus on 2006-09-18
> **Newbie in Linux World said:**
> hmm yes, where do I find them ?
log in.

execute

```

sudo aptitude install ubuntu-desktop

```

Then let it cook.

---

