---
title: "audio drivers Realtek97"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by jake16424 on 2007-08-09
are not working. need help

Ubuntu 6.06 i think.

---

### Post by Jimmyfj on 2007-08-09
Found a link for you - Hope they'll help you out:

[http://www.mikinews.net/2007/06/30/realtek-ac97-vista-audio-driver-6016243-whql/](http://www.mikinews.net/2007/06/30/realtek-ac97-vista-audio-driver-6016243-whql/)

---

### Post by MenZa on 2007-08-09
See, we'll need a bit more info than that if we are to help you. I believe you can find your version of Ubuntu by running:

```
cat /etc/lsb-release
```.

Also, could you paste the output of lspci?

---

### Post by jake16424 on 2007-08-09
> **MenZa said:**
> See, we'll need a bit more info than that if we are to help you. I believe you can find your version of Ubuntu by running:

```
cat /etc/lsb-release
```.

Also, could you paste the output of lspci?

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"
jacob@jacob-desktop:~$

well there you go, 

and,, thats the chipset i have, realtek audio 97 chipset.. idk what else to put in there.. ask and ill run a diag and find out.. or,, pray it magically pops up infront of me in english ^_^

---

### Post by jake16424 on 2007-08-09
> **Jimmyfj said:**
> Found a link for you - Hope they'll help you out:

[http://www.mikinews.net/2007/06/30/realtek-ac97-vista-audio-driver-6016243-whql/](http://www.mikinews.net/2007/06/30/realtek-ac97-vista-audio-driver-6016243-whql/)

didnt help that driver is for vista,, + the page is mostly in another language..

---

### Post by jake16424 on 2007-08-09
> **MenZa said:**
> See, we'll need a bit more info than that if we are to help you. I believe you can find your version of Ubuntu by running:

```
cat /etc/lsb-release
```.

Also, could you paste the output of lspci?

what is Ispci

---

### Post by MenZa on 2007-08-10
Run *lspci* in a terminal and paste the output here.

---

