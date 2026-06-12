---
title: "Compiler problem"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by radicaledward on 2006-09-01
I've tried linux before, and i'm not a 100% linux newbie, just a 99% linux newbie. Recently I gained a computer to putz around on, and I plan on using it for a local fileserver type thing. Having had problems installing things on linux, I decide to simply try out installing something. I downloaded the source for a game called GRacer, then attempted to install it. Note that this is a FRESH install of Dapper. This is the output:

panzer@fileserv:~/Desktop/gracer-0.1.5$ ./configure
loading cache ./config.cache
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
panzer@fileserv:~/Desktop/gracer-0.1.5$

Synaptic seems to think that GCC is installed, but echo $PATH gives:

 echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games


Any help is, well, helpful!

---

### Post by taurus on 2006-09-01
Open a terminal (Applications -> Accessories -> Terminal) and type

```

sudo aptitude update
sudo aptitude install build-essential

```
Then run your ./configure && make && sudo make install again...

---

### Post by TFX360 on 2006-09-01
> **taurus said:**
> Open a terminal (Applications -> Accessories -> Terminal) and type

```

sudo aptitude update
sudo aptitude install build-essential

```
Then run your ./configure && make && sudo make install again...

Sneak question

Whats is or would be the difference in

```
./configure && make && sudo make install
```

compared to

```
./configure; make; sudo make install
```


Just curious

---

### Post by taurus on 2006-09-01
> **TFX360 said:**
> Sneak question

Whats is or would be the difference in

```
./configure && make && sudo make install
```

compared to

```
./configure; make; sudo make install
```

Just curious
Open a terminal and see what's the difference between the output of these two commands:

```
ls; finger
```
```
ls && finger
```
They are exactly the same.  However, most Unix users use the && instead of ; to include more than one command on the same line...

---

### Post by distroman on 2006-09-01
#wondering out loud

I was under the impression, that if you use && when compiling, the && will invoke a stop and report an error, if there is any, with make, where ; will not?

How about suggesting to use checkinstall instead of make install? 
I have not really done a lot of reading on checkinstall, so unsure if there are any issues, but it sure seems like the easy way. 
I have not had any trouble with it, so fare.

---

### Post by TFX360 on 2006-09-01
> **taurus said:**
> Open a terminal and see what's the difference between the output of these two commands:

```
ls; finger
```
```
ls && finger
```
They are exactly the same.  However, most Unix users use the && instead of ; to include more than one command on the same line...

Thanks for clearing that up, I was pondering that in my mind for quite a while.

---

