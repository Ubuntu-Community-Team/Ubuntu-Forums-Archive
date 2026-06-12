---
title: "avertv go 007 tv-card driver"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by murmillo on 2007-04-09
hi,

i'm really new about ubuntu.

i'm using ubuntu, version 6.10 and i have a tv card which is avertv go 007.
and i want to install its driver.

i found many sources for driver but i can not understand and i can't do anything.

so i want u to tell me step by step how i can install my drivers?

thank u :)

---

### Post by darthchaosofrspw on 2007-04-19
> **murmillo said:**
> hi,

i'm really new about ubuntu.

i'm using ubuntu, version 6.10 and i have a tv card which is avertv go 007.
and i want to install its driver.

i found many sources for driver but i can not understand and i can't do anything.

so i want u to tell me step by step how i can install my drivers?

thank u :)

Here's a website that may help.

[http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm](http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm)

And here are some instructions if your card uses the sa7134 chipset. 

[http://www.linuxtv.org/v4lwiki/index.php/Avermedia_AVerTV_GO_007_FM](http://www.linuxtv.org/v4lwiki/index.php/Avermedia_AVerTV_GO_007_FM)

If you have to do a modprobe, remember you will have to run the commands as sudo. For example, if you want to run the command

```
modprobe saa7134-oss
```

you will have to run it with this command :

```
sudo modprobe saa7134-oss
```

Just remember when the terminal asks for your password, use your user password, not the root password. Later Linux kernels support saa7134-oss and saa7134-alsa, so be sure to read up on the ALSA link at [http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa](http://www.linuxtv.org/v4lwiki/index.php/Saa7134-alsa)

If you find success, please post what you did so you could be of help to others (such as me, since I just won an AVerTV Go 007 FM TV Tuner card on eBay).

---

