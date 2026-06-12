---
title: "MacBook Pro 4,1, 64-bit Lucid with wireless connectivity issues...UGH!"
date: 2010-11-28
forum: Apple Hardware Users
---

### Post by punkaroo on 2010-11-28
Hi everyone :)

I stayed up way past my bedtime last night, and finally got around to installing the 64-bit version of Lucid on my MacBook Pro 4,1. I've already tried the Broadcom driver, yet my wireless connectivity doesn't seem to stay connected.

I've typed in the correct password for my network, and it tries to connect, but then drops the signal. I've searched and searched online and cannot find a fix. I've found some Debian sites that require me to install packages, but it seems very confusing to a newb like me!

I've used Terminal in OS X before, so that doesn't scare me. If I have to connect to the internet wired to do this, I'd really appreciate some help.

Thanks so much!

---

### Post by tom4everitt on 2010-11-29
I assume you connected it to the internet at least once, to get all updates etc? Otherwise that is a good idea, of course. 

Broadcomm actually just open-sourced their wireless driver, it will be included in the 2.6.37 linux kernel which will probably be used in Ubuntu 11.04. 

It is possible to install that kernel in earlier versions Ubuntu, either by compiling it from [source]("http://www.kernel.org") or, easier, by [the builds provided by Ubuntu.]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") There are no guarantees your system will work well with that new kernel, however. 

Hopefully the newer driver will work better. That is the only solution I can think of at the moment, maybe someone else has another idea? I hope you get it working!

---

### Post by jsiret on 2010-11-29
I had a problem like this when I first installed ubuntu on my imac, I installed all the updates through a wire and have been fine since.

---

### Post by 1337hippo on 2010-11-29
I am using a fresh install of Maverick 64-bit on my macbook 5,1 and I am also experiencing this problem. 

I found these bug reports:
[https://bugs.launchpad.net/ubuntu/+bug/572777](https://bugs.launchpad.net/ubuntu/+bug/572777)
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/488340](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/488340)

So far I tried installing wicd and so far it seems to have fixed the problem, I'll post if I can find a better solution

Update:
I tried this [https://bugs.launchpad.net/ubuntu/+bug/572777/comments/35](https://bugs.launchpad.net/ubuntu/+bug/572777/comments/35) but it didn't work for me

---

### Post by punkaroo on 2010-11-29
Oddly enough...the problem fixed itself...? Weird how that works!

Thanks for the help all!

---

### Post by alexmurray on 2010-11-30
I would suggest it may be more like this issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651008](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651008)

i.e. connection drops out when on battery power.

If so try typing the following in a terminal to fix it:

```

sudo iwconfig eth1 power off

```

---

### Post by 1337hippo on 2010-11-30
I have this problem with and without power.

I have had less problems since I've put wicd on autostart, I'll post if I find a better solution

---

