---
title: "Dist Upgrade"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by whoosh on 2007-01-28
I think this might have been posted before but I'm just gonna start a new thread and risk being yelled at

So here's what basically happened:

When linux was working, it told me I needed to do an dist-upgrade through synaptic. I attempted to do it, but I got some error so I decided just to do it by terminal via apt-get dist-upgrade (something liek that...)

Now I can't start X server up...and I'm pretty sure it has to do with the fact that my nVidia kernels aren't upgraded all the way. I tried to do something like apt-get install nvidia-glx and then it told me there was some sort of dependency or something. I attempted to apt-get install the depency and it didn't work...

Sorry about the vague details, I don't know how I'd copy/paste the stuff into this thread...

I think I basically need to upgrade my nVidia kernels so how do I do that?

---

### Post by dbbolton on 2007-01-28
first, i think your should reconfigure X. boot into recovery mode, and type:
```
sudo dpkg-reconfigure xserver-xorg
```next, i would recommend following Compiz' guide on nvidia drivers:

[http://go-compiz.org/index.php?title=NVidia](http://go-compiz.org/index.php?title=NVidia)


no, you do not have to install compiz from that tutorial. it just deals with drivers.
==========

First you must install the necessary packages to build a kernel interface for the latest nvidia driver:

```

sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
```

---

