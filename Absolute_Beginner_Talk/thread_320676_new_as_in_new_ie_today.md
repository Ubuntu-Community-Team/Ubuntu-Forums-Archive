---
title: "new as in new ie today"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by bill 380 on 2006-12-17
i know im new but how do i install  programs on  this op sys
ie mp3 player and zip utilaties?

---

### Post by taurus on 2006-12-17
How to install something:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

And for MP3, install automatix2 and use it to install the codecs and other media players for your machine...
[http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation)

---

### Post by zekopeko on 2006-12-17
for automatix:

System > Administration > Synaptic Package Manager (enter your password when asked)

then in Synaptic: Settings > Repositories > Third Party (it's a tab) and then click on Add

and paste this code

```
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
```

after that click on reload (it will complain that the repository can't be verified or something like that but just go ahead)

and then search for automatix2 , right click and install.

and that's it

be sure to check the link that taurus has given for automatix (it looks like it is broken for now so check it tomorrow)

---

### Post by Blondie on 2006-12-17
Or if you're really lazy just click on this [link]("http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/automatix2_1.1-2.3-6.10edgy_i386.deb")

Either way Automatix will be in Applications / System Tools after you install it.

---

### Post by raul_ on 2006-12-17
> **zekopeko said:**
> for automatix:

System > Administration > Synaptic Package Manager (enter your password when asked)

then in Synaptic: Settings > Repositories > Third Party (it's a tab) and then click on Add

and paste this code

```
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
```

after that click on reload (it will complain that the repository can't be verified or something like that but just go ahead)

and then search for automatix2 , right click and install.

and that's it

be sure to check the link that taurus has given for automatix (it looks like it is broken for now so check it tomorrow)

You are assuming he's using edgy

---

### Post by arnieboy on 2006-12-17
just a quick update for whoever's reading:
After our joomla homepage, our wiki has been the latest victim of the 100 MB database cap (and hence gone down too). 
We are working very hard on transferring 2 of our 3 databases to a more generous host which will fix this issue soon.
please remember:
Our repositories, file servers and forums are still working fine.

---

### Post by serlex on 2006-12-18
can someone tell me, does Automatix2 install a software which is already installed or skip it?

---

### Post by TooRight on 2006-12-18
With automatix  you have to check off what you want it to install anyways...but actually, earlier today I was half asleep and installing things using automatix; I forgot i had installed something manually before that and I "checked" it in automatix, Instead of installing it over the previous one, Automatix let me know that the program was already installed, skipped it and went on.

---

### Post by jvc26 on 2006-12-18
Have you also looked here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
tends to have useful stuff for when you're starting out.
Il

---

