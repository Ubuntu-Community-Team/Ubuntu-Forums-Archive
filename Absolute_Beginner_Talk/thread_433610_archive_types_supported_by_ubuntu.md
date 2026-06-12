---
title: "archive types supported by ubuntu"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by rufi_dukes on 2007-05-05
i installed ubuntu 2 days ago and then spent the rest of the time trying to get a handle on something, anything! about how to use it!!!!
i am sooooo frustrated!
what a learning curve
i am a pretty lowend user to date, but very keen to learn...
after searching for a graphics calculator all i could turn up was a prog called maxima, which is probably more than i need by far (i'm doing college level maths: functions, graphs etc)
so, i dload it (all 12mg of it) only to find that ubuntu doesn't handle rpm packages...
what do it do?
is there a site where u get ubuntu stuff? packaged in what archive forms?
how do i get synaptic to do the work for me, coz i sure as hell know i'm going to be stuck if i have to do it manually at command prompt (that level of sophistication seems a long way off for me right now, depressingly long)
any help would be a heaven send,
thx,
rufus

---

### Post by Pobega on 2007-05-05
Debian based systems can handle rpm packages, you just need to know how. Go into a terminal and:

```
sudo apt-get install alien && sudo alien -d *.rpm && sudo dpkg -i *.deb
```

Make sure the rpm file is in your home folder when you do that.

---

### Post by rufi_dukes on 2007-05-05
thx Richard,
so, is ubuntu debian-based?

---

### Post by Pobega on 2007-05-05
Yeah, I forgot to mention that. Ubuntu is a Debian based system (Almost anything that uses apt-get is Debian-based). Just run that command, it should work. Just make SURE the rpm is in your home folder (/home/rufi, if that is your username)

And by the way, as much as I wish I was, I'm not Richard Stallman. I'm just quoting him in my signature.

---

### Post by darkrose on 2007-05-05
system --> administration --> synaptic package manager
and use the search function to find a calculator.

Synaptic will download and install the application for you. Have a look at the synaptic how-to for more info - [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by igknighted on 2007-05-05
check out gnuplot, probably more up your ally.  But Gnuplot and Maxima are both in the repositories, use synaptic to access them.

---

### Post by lepz on 2007-05-05
> **Pobega said:**
> 
And by the way, as much as I wish I was, I'm not Richard Stallman. I'm just quoting him in my signature.

Bet you wish you could sing like him [though]("http://www.youtube.com/watch?v=9sJUDx7iEJw") :lolflag:

---

