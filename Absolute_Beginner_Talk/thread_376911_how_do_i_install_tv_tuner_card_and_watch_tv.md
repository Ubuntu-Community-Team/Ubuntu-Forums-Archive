---
title: "how do i install tv tuner card and watch tv?"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by shashank on 2007-03-05
i have managed to setup everything on ubuntu except my tv tuner card...
its a company called "enter"
[www.entermultimedia.com](www.entermultimedia.com)
i looked in device manager and it shows only "video device"
i looked in /dev and a file and not a folder called /dev/video0 was found.
i dont know what this site is to do with my installing the driver and software to run tv tuner...
[http://www.linuxtv.org/](http://www.linuxtv.org/)
plz help...
i realy want to run my tv tuner card on linux. i have dapper...:confused:

---

### Post by caintona on 2007-03-05
try out mythtv.org

---

### Post by the_nomad on 2007-03-05
i have just installed tvtime and seems very easy to use but i dunno why it didnt find any channel that works... maybe you're lucky so i say you should try it :)

---

### Post by TonKi on 2007-03-05
Do you know what chip is on your card (eg BT878 ) or can point out the card you have?

---

### Post by lamalex on 2007-03-05
try out mythtv and keep your eye on another project called elisa that is looking to add tv tuner support. it's a nice media centre for linux.

---

### Post by TonKi on 2007-03-05
xawtv is another tv-app (just a tv app, not a multimedia-center ;))

---

### Post by superm1 on 2007-03-06
> **shashank said:**
> i have managed to setup everything on ubuntu except my tv tuner card...
its a company called "enter"
[www.entermultimedia.com]("http://www.entermultimedia.com")
i looked in device manager and it shows only "video device"
i looked in /dev and a file and not a folder called /dev/video0 was found.
i dont know what this site is to do with my installing the driver and software to run tv tuner...
[http://www.linuxtv.org/](http://www.linuxtv.org/)
plz help...
i realy want to run my tv tuner card on linux. i have dapper...:confused:
What you should do is post the output of
```
lspci
``` 
in this thread.  We can hopefully identify the card better from this.

---

### Post by punx45 on 2007-03-06
you might need a driver for the card?   ivtv or bttv probably aren't installed by default.

to know what you need you will first have to know what chipset the card uses.   so do like superm1 said and post the output of 'lspci'

---

