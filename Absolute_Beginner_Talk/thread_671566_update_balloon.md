---
title: "update balloon"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Rita G. on 2008-01-18
I get a damn annoying software update balloon that shows up every time I start ubuntu.

every time I try to install it I get this error box:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.1_i386.deb)

  403 Forbidden

---

### Post by lgambett on 2008-01-18
There is a message in Launchpad saying that they are fixing the package, which causes malfunction in the Java machine; the package should be fixed ASAP.

---

### Post by PinkFloyd102489 on 2008-01-18
Yeah that prevented me from fully updating one of our school computers today.

---

### Post by Rita G. on 2008-01-18
thanks lgambett

---

### Post by nikoPSK on 2008-01-18
> **lgambett said:**
> There is a message in Launchpad saying that they are fixing the package, which causes malfunction in the Java machine; the package should be fixed ASAP.

yup, samba had it too. Learn to live with it. :)

---

### Post by ajgreeny on 2008-01-18
It's fixed now if you refresh your repos.

---

### Post by nikoPSK on 2008-01-18
good, please mark this thread as "SOLVED".

---

### Post by Rita G. on 2008-01-19
I realize you have ants in your pants and you want to dance.....but

relax....it's not “SOLVED” yet.

how does one refresh repos?

---

### Post by Lord Illidan on 2008-01-19
sudo apt-get update or Synaptic -> Reload will "refresh the repositories"

---

### Post by nikoPSK on 2008-01-19
> **Rita G. said:**
> I realize you have ants in your pants and you want to dance.....but

relax....it's not “SOLVED” yet.

how does one refresh repos?

lol, sorry.

> **Lord Illidan said:**
> sudo apt-get update or Synaptic -> Reload will "refresh the repositories"

thank you lord illidan. :)

---

### Post by Rita G. on 2008-01-19
ok, so i did the  sudo apt-get update  thing 

and after a reboot my resolution blew up so large i could not find the system menu to change it.

i can however, open the applications and places menus. 

can anyone tell me how to get my res back to 1280x1024 in a terminal?

---

### Post by nikoPSK on 2008-01-19
reconfigure xorg;:
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

should do it. :)

---

### Post by Rita G. on 2008-01-19
that didn't work either.

seems like every fix opens another can of worms around here.

i think it's time to junk this OS and look for one that works.

i'd like to spend SOME of my time USING the computer

not ALL of my time FIXING it.

thanks for all help.

---

