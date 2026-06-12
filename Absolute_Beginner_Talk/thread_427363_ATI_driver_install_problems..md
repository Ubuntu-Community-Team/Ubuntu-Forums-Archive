---
title: "ATI driver install problems."
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by And1945 on 2007-04-29
Hi all.

I am very new to this, so bare over with me. I have tried several guides found on this forum, and on the unofficial ati wiki, everything turns out basicly with this error: 
> ./ati-installer.sh: 165: Syntax error: Bad substitution
Removing temporary directory: fglrx-install

What can do with this, because 1024x768 on a 22" monitor is not the best option.

Thanks in advance.

P.S. This is driving me utterly nuts.

---

### Post by livesys on 2007-04-29
Hi there,

Can you post more information about your system so other can better help you.

What ATI video card are you using? 
Brand and Model of the 22" monitor?  Specs? 

xorg.conf file? etc...

---

### Post by And1945 on 2007-04-29
ATI 9800XT and a Compaq P1220 monitor.

But I did add something to that config file, to enable me to run in 1600x1200, so I wuld say that it doesnt really matter anymore. Thanks anyway.

---

### Post by user1397 on 2007-04-29
> **And1945 said:**
> ATI 9800XT and a Compaq P1220 monitor.post your xorg.conf file by going to a terminal (applications > accessories > terminal) and typing: ```
gedit /etc/X11/xorg.conf
```

---

### Post by Gavin77 on 2007-04-29
I'd make a guess that your forgot to use sudo before the install command.

---

### Post by And1945 on 2007-04-30
> **Gavin77 said:**
> I'd make a guess that your forgot to use sudo before the install command.
I might have. Im quite new to this, so the terminal doesnt make sense for me yet.

Im going to try and install them again, when a proper Feisty driver comes.

But, would it say "bad substitution" if I wrote sudo?

---

### Post by And1945 on 2007-04-30
> **ubuntuman001 said:**
> post your xorg.conf file by going to a terminal (applications > accessories > terminal) and typing: ```
gedit /etc/X11/xorg.conf
```
I will add that later today. I really dont have time for geeking with linux know, even though I LOVE it. :)

Ubuntu rules.

---

