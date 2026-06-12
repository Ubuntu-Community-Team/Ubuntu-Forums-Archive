---
title: "How to use apt-get and modify /etc files"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by kingsmalls on 2007-01-21
Hi everybody,
I'm a new user of Ubuntu and I've some problems using it.
I did use red hat, fedora, mandriva and mandrake, so I know some things about linux but in Ubuntu I can't do similar things like in other versions.
I know I can install some files using apt-get butI have to configure my proxy first, since I live in a school and we have to use that proxy to go out of the intranet. In what file can I do it? Besides, how to use it properly?
Secondly, I want to configure some /etc files but I've no rights to do it even if I do sudo -u <my_user_name_> or the file to modify but nothing to do! How to modify those files and get rights to do it?
My last question : are there softwares like emacs, gedit for text and xmms, xine or xawtv? 'cause I can't use my TV-card (Winfast).

Thanks a lot for answerring to some of my questions.

---

### Post by moshuptrail on 2007-01-21
To edit files in /etc

$ sudo gedit /etc/X11/xorg.conf  (for example)

It will ask for your password.  sudo just executes the command that follows as root.

Can't help with the proxy

---

### Post by 23meg on 2007-01-21
[QUOTE=moshuptrail]$ sudo gedit /etc/X11/xorg.conf (for example)[/QUOTE]You should use *gksudo* instead of *sudo* for graphical apps.
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by aysiu on 2007-01-21
More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by moshuptrail on 2007-01-21
I stand corrected.
Personally I use vi, but I never recommend it to others 'cause nobody (well very few) know how to use vi.

To get back on topic, can anyone help with how to configure a proxy?

---

### Post by JamieC on 2007-01-21
See [here](http://ubuntuforums.org/showthread.php?p=2043858#post2043858) for a similar issue.

---

### Post by kingsmalls on 2007-01-21
I haven't got gedit editor but kate editor which is not as common as emacs or gedit and, I can't open this file with kate. I can't do what you're advising.

---

### Post by moshuptrail on 2007-01-21
try this
sudo apt-get install emacs

p.s. what file?
pps.  you can't use apt-get yet...  arrrgh!!!

what error is kate giving, and what file is it?

---

### Post by kingsmalls on 2007-01-21
I can't write on any file because I've no rights since I can't open any file with kate. I don't know what to do?:confused:

---

### Post by aysiu on 2007-01-21
```
kdesu kate /etc/apt/sources.list
```

---

### Post by moshuptrail on 2007-01-21
the sudo command gives you those rights

sudo kate /etc/hosts

should allow you to edit /etc/hosts no prob

---

### Post by aysiu on 2007-01-21
> **moshuptrail said:**
> the sudo command gives you those rights

sudo kate /etc/hosts

should allow you to edit /etc/hosts no prob
You should use *kdesu*  with *kate*, not *sudo*.

Please read this link for more details:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

