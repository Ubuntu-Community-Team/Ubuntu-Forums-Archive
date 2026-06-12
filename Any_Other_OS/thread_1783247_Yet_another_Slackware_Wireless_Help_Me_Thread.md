---
title: "Yet another Slackware Wireless Help Me Thread"
date: 2011-06-15
forum: Any Other OS
---

### Post by P-nut on 2011-06-15
Hello people,

I am very much new to Slackware and trying my hardest to learn to use it myself. However, I just cannot get wireless to work.

I have looked at other threads and sites, tried different things and really thought about it all. To be honest though, I don't really understand what I am supposed to be doing, or what I have tried to do actually does.

Some help would really be lovely, I know I need to work things out myself but I think doing it it without even a basic understanding is just not going to happen.

Thanks,

Pnut

---

### Post by FormatSeize on 2011-06-15
> **P-nut said:**
> Hello people,
 
I am very much new to Slackware and trying my hardest to learn to use it myself. However, I just cannot get wireless to work.

Are you attempting to do it from the desktop environment, or at the not-desktop environment?

---

### Post by P-nut on 2011-06-15
Well I have been trying using Terminal in Xfce.

---

### Post by sffvba[e0rt on 2011-06-15
One of the reasons to use Slackware is to learn more about Linux.  I can remember the missions I had to go through to get everything set up... but it was worth it... I am going to link you to a thread I started on another forum... hopefully you can get some tips there about where to start looking and figure it out as you go along ;)

[http://www.overclock.net/linux-unix/823804-project-hewlett-slackard.html](http://www.overclock.net/linux-unix/823804-project-hewlett-slackard.html)


Oh, and the official Slackware forums - [http://www.linuxquestions.org/questions/slackware-14/](http://www.linuxquestions.org/questions/slackware-14/)



404

---

### Post by kk0sse54 on 2011-06-15
You can try looking over this page [http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:network](http://alien.slackbook.org/dokuwiki/doku.php?id=slackware:network), otherwise if you want somebody to help you here you'll have to provide a heck of a lot more information regarding your setup.

---

### Post by andrew.46 on 2011-06-15
My own solution to using wireless under Slackware has been to install the appropriate firmware (but you will need to give some details of your wireless chip here) and then to use wicd, this is in /extra in the Slackware source. Best place for detailed questions, as notfound has mentioned, is in the LinuxQuestions forums which is the web forum home for slackware.

---

### Post by boydrice on 2011-06-16
I am going to echo what andrew.46 said, assuming your wireless card is detected and working try installing wicd in /extra.  You need to provide more info though, specs, what wireless card, did you do a full Slackware install, etc.

---

### Post by P-nut on 2011-06-16
Hello,

Thanks for the replies. I am going to have a look through the links I have been given by you wonderful people and see if I can sort some stuff myself.

I didn't give more details as I was really kind of hoping to just get linked to some stuff to try.

I will report back soon.

Pnut

---

### Post by sffvba[e0rt on 2011-06-18
Well, after reading the OP and posting the link to my time with Slackware I got that hopping itch again and I am now sporting a 13.37 sticker on my desktop :p

Luckily my laptops wireless is already supported by the kernel so all I did was to install wicd from the DVD and I was good to go...


404

---

### Post by andrew.46 on 2011-06-18
> **not found said:**
> Luckily my laptops wireless is already supported by the kernel so all I did was to install wicd from the DVD and I was good to go...

Good on you :). I am also running 13.37 + the next few updates in -current but I have to do a little dance still with b43-fwcutter and the broadcom wl driver. My next computer will not have a wireless broadcom chip of any type :).

---

### Post by sffvba[e0rt on 2011-06-18
> **andrew.46 said:**
> Good on you :). I am also running 13.37 + the next few updates in -current but I have to do a little dance still with b43-fwcutter and the broadcom wl driver. My next computer will not have a wireless broadcom chip of any type :).

Nice... I have to still get to know how to stay current with Slack... I have seen that KDE 4.6.4 is available from AlienBOB's blog so I will get that installed... other than that I am pretty clueless with Slackware still, only started using Slackbuilds yesterday (the last time I tried Slackware I was still compiling everything I needed :p)


404

---

### Post by andrew.46 on 2011-06-18
> **not found said:**
> Nice... I have to still get to know how to stay current with Slack... 

I do it the lazy way and if you are interested it is a good time to start as -current has changed very little from 13.37 so if you have the dvd you can use this for the source tree. I use alienBOB's script:

[http://alien.slackbook.org/blog/local-slackware-mirror/](http://alien.slackbook.org/blog/local-slackware-mirror/)

and then run:

```

cd /home/andrew/slackware/slackware-current/slackware && \
for dir in a ap d f k l n t tcl x xap y ; do
 ( cd $dir ; upgradepkg --install-new $(ls *.t?z | grep -vE '(MPlayer|slrn|vim-gvim|xscreensaver)'))
done

```

which upgrades most of the series (except for emacs and kde) excluding a few packages. Finally comb /etc for altered configs:

```

find /etc -iname '*.new'

```

and deal with them. Mind you there is always slackpkg which is a little less 'manual' but I have not used this....

---

### Post by sffvba[e0rt on 2011-06-18
> **andrew.46 said:**
> I do it the lazy way and if you are interested it is a good time to start as -current has changed very little from 13.37 so if you have the dvd you can use this for the source tree. I use alienBOB's script:

[http://alien.slackbook.org/blog/local-slackware-mirror/](http://alien.slackbook.org/blog/local-slackware-mirror/)

and then run:

```

cd /home/andrew/slackware/slackware-current/slackware && \
for dir in a ap d f k l n t tcl x xap y ; do
 ( cd $dir ; upgradepkg --install-new $(ls *.t?z | grep -vE '(MPlayer|slrn|vim-gvim|xscreensaver)'))
done

```which upgrades most of the series (except for emacs and kde) excluding a few packages. Finally comb /etc for altered configs:

```

find /etc -iname '*.new'

```and deal with them. Mind you there is always slackpkg which is a little less 'manual' but I have not used this....

Andrew... don't wonder to far from Other OS... I suspect your assistance will come in very handy (I read your post and I got this feeling I sometimes do when someone speaks and I can see there mouth move but can't hear the words :p)

I will create a thread for upgrading if I get that far and get stuck so we stop hi-jacking this one :D


404

---

### Post by andrew.46 on 2011-06-18
> **not found said:**
> I will create a thread for upgrading if I get that far and get stuck so we stop hi-jacking this one :D

Oops... my apologies to the original poster!!

---

