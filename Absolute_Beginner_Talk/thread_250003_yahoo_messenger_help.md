---
title: "yahoo messenger help"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by dal2k5 on 2006-09-03
umm i got the installer, ran it and this is wat i got

[http://i67.photobucket.com/albums/h314/geexo777/yim.png](http://i67.photobucket.com/albums/h314/geexo777/yim.png)

---

### Post by dal2k5 on 2006-09-03
ppl can u plez help i have no idea wat to do..

---

### Post by Scorpuk on 2006-09-03
goto your synaptic package manager and do a search for libssl0.9.6 and install it. 

Try again, any more dependencies not satisfied then do the same for each you find.

---

### Post by jorn on 2006-09-03
I just found this on the web, maybe it will work for you:
[http://ubuntuforums.org/archive/index.php/t-7147.html](http://ubuntuforums.org/archive/index.php/t-7147.html)

---

### Post by dal2k5 on 2006-09-03
> **Scorpuk said:**
> goto your synaptic package manager and do a search for libssl0.9.6 and install it. 

Try again, any more dependencies not satisfied then do the same for each you find.

okay i'll try it thnx in advance

---

### Post by dOvi on 2006-09-03
i am having the same ... kind of ... problem
it says i need libssl0.9.6 but i have libssl0.9.8 - why isn't it working with an update and still needs the old package?
what should i do?
10x in advance

---

### Post by dal2k5 on 2006-09-03
> **dOvi said:**
> i am having the same ... kind of ... problem
it says i need libssl0.9.6 but i have libssl0.9.8 - why isn't it working with an update and still needs the old package?
what should i do?
10x in advance

same here i have libssl0.9.7 installed.......

---

### Post by blent07 on 2006-09-03
Also, you could just use GAIM. I used that for my Yahoo Messanger account for  a while. I don't use it anymore, but it worked fine for me.

---

### Post by dal2k5 on 2006-09-03
> **blent07 said:**
> Also, you could just use GAIM. I used that for my Yahoo Messanger account for  a while. I don't use it anymore, but it worked fine for me.

okay i'll try gaim

---

### Post by dOvi on 2006-09-03
thx
after i've seen i gotta install an old package ... better gaim
peace

---

### Post by dal2k5 on 2006-09-03
> **dOvi said:**
> thx
after i've seen i gotta install an old package ... better gaim
peace

lol ye

---

### Post by Omnios on 2006-09-03
Hi hi I played around with this for a bit and got all the dependancys but one

> 
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed


 So basicly we have o find xlibs 3.3.6 which not available in synaptic yet. Anyways you might be able to find it in edgy but from my last experience with this type of thing led to dependancy hell

---

### Post by iam_foo on 2006-09-05
i installed wine.
then i installed trillian 0.74.i [on wind0z then moved the folder
via my fat32 partition]
works Mazingly well.
heh..the s0larian skin is good eye candy to go with my aiglx.

:twisted: 

btw, i tried the method your trying..wine is less work..
and i have MSN, AIM, ICQ, Yahoo, and IRC [although i use bitchX for that<3]
all work fine, i can move windows..etc..which is a problem with some other trillian releases.

---

### Post by hellmet on 2006-09-06
search for the dummy packages of libssl and xlibs from debian.com
and install them thru terminal..
then try y!..
i did it that way..

---

### Post by Zyphrexi on 2006-09-10
gaim doesn't support a lot of the options yahoo messenger does. Personally for me, it's no contest.

---

### Post by Najand on 2006-09-10
libssl0.9.6 is not available at Dapper Drake, because it is an old library. However you can download and install it from Ubuntu Package Contents Hoomepage:
[http://packages.ubuntulinux.org/breezy/oldlibs/libssl0.9.6]("http://packages.ubuntulinux.org/breezy/oldlibs/libssl0.9.6")

---

### Post by djheadley on 2006-09-10
What does YM support that GAIM doesn't?

---

