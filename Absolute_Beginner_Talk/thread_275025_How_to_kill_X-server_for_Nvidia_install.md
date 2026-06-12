---
title: "How to kill X-server for Nvidia install?"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by GotGamble on 2006-10-10
I've been instructed to install the new beta-Nvidia driver in order for it to auto-detect my TV output device and to auto/help me configure X-server. 

I get an error during installation of the driver that says that I am running X-server, and I need to quit X-server to install this driver. 

I have tried Ctrl-Alt-Bckspace, but GDM starts back up in a few seconds. I have tried logging in at the beginning choosing terminal instead of GNOME, it still tells me I am running X-server.

How to I straight up kill X-server, so I can run this from a command line.

sh NVIDIA-Linux-x86-1.0-9625-pkg1.run

I tried removing the X-server settings from the login screen preferences section, but that just got me a message saying that It appears I have no x-server configured, one has been started for you, please login and fix this problem.

Grrrrr! Angry beavers!](*,)

---

### Post by RanDinCarolina on 2006-10-10
```
Sudo killall xserver
```

I think:-k

---

### Post by blendmaster on 2006-10-10
Yeah, control+alt+backspace simply restarts GNOME, not killing X.

RanDinCarolina is right.

It should take you to a command prompt mode which has no GUI (in other words, it's just white words on a black screen, with no pretty pictures).

---

### Post by WhiteDawn on 2006-10-10
there is no need to do so. Through synaptech you can install the nvidia drivers. Its alot easyer, and you can be sure it will work.

---

### Post by GotGamble on 2006-10-10
I tried sudo killall xserver it comes back with 

xserver: no process killed



Grrrr ](*,)

---

### Post by PriceChild on 2006-10-10
press ctrl+alt+F1 to go to tty1

Log in, enter p/w etc.

```
sudo /etc/init.d/gdm stop
```Do whatever you need to do```
sudo /etc/init.d/gdm start
```

---

### Post by GotGamble on 2006-10-10
Okay, thanks very much gdm stop seems to get me past that part. Now I have some other stuff to do apparently, but I think I can get there myself now, thanks again! :cool:

---

### Post by RanDinCarolina on 2006-10-10
Me noobie, I probably would have come up with those commands in about a month or so.So much to learn.......

---

### Post by GotGamble on 2006-10-10
Well so much for that. I can kill gdm, so I run the installer, it tells me that it needs to recompile my kernel, and starts giving me missing modules to install. I installed about 4 of them, and now it is stuck saying that it cannot find the kernel source tree, even though I have installed that package. I have looked through the repository for anything else I might be missing I can't figure it out. 

I guess I need to find a different way to install the beta driver. Any suggestions? Surely someone else out there must have installed the Nvidia beta driver 9625 already. Is there an easier way? I can't find it with Synaptic, which is what I first tried.

---

### Post by RanDinCarolina on 2006-10-10
Me noobie, I probably would have come up with those commands in about a month or so.

So much to learn.......then you die.

---

### Post by PriceChild on 2006-10-10
> **GotGamble said:**
> Surely someone else out there must have installed the Nvidia beta driver 9625 already. Is there an easier way? I can't find it with Synaptic, which is what I first tried.Yup i'm running the beta on Edgy atm.

I strongly advise you to stick with the stable driver for now. If you are wanting to use it for beryl then on Dapper I think the current consensus is to stick with xgl.

---

