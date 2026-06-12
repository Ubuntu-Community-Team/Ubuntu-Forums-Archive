---
title: "installing in Kubuntu a second hard drive"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by arno1991 on 2007-08-19
hello,

i've searched everywhere, but nothing found. I want to mount my second hard drive with **Kubuntu**. For Ubuntu i've found millions of ways doing it, but then there is one line to do with this:

sudo gedit /etc/fstab

ofcourse, i don't have gedit, but Kate. And when i try to change the word "gedit" in "kate" the Konsole says that the command Kate doesn't exist. I tried this several ways.
It is a fresh install, since yesterday. 

The second hard drive is normal on hda1 and i made already a space for it: /media/Maxtor30GB
it is just for storage, and i want to mount it because all my music and doc's are standing on it since Ubuntu... (so it is already a ext3 filesystem)

thanks,

arno

---

### Post by tdrusk on 2007-08-19
Try installing kate.

```
sudo aptitude install kate
```

---

### Post by arno1991 on 2007-08-19
thanks for your reply,

but Kate is already installed. I use Kubuntu...

grtz,

arno

---

### Post by MenZa on 2007-08-19
Could you paste the exact command you're using to launch Kate?

You could also try using a terminal editor, such as nano or vi.

---

### Post by arno1991 on 2007-08-19
normally, via terminal, and to install the second hard drive, i use
[HTML]sudo /etc/fstab kate[/HTML]
and i tried also to write kate with a capital, etc...

what is a terminal editor? i even don't know what nano or vi is... do i'll have to install that?

thanks,
arno

---

### Post by MenZa on 2007-08-19
Aha! There's the problem; what you want to run is:

```
sudo kate /etc/fstab
```

Also, as far as I know, both nano and vi (and vim) are installed by default. vi and vim are both powerful text editors, but require some knowledge (I use vim in my daily life).

---

### Post by arno1991 on 2007-08-19
thank you very much, it works :D
this is also the first time I use Kubuntu...

thanks!

arno

---

