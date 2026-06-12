---
title: "Save time and bandwidth with apt-proxy"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by uber_n00ber on 2007-08-12
Like me, you might have a few computers on a local network that you have installed Ubuntu on. I love the fact that packages are being updated all the time, whether security or feature improvements, but as soon as you have more than one computer to update you soon start wishing for a way to mirror and serve the updates locally, rather than downloading them all over again for each computer.

I'm new to Linux so there might be a few different ways to achieve this, but I have just started playing around with apt-proxy, after reading about it here:

[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)

> apt-proxy is a program that caches the packages you download from the Internet, to your hard disk. Because apt-proxy behaves as if it were a HTTP server with a full copy of the repositories you select, you can access the packages from other computers on your network. If a package is not in the cache, apt-proxy automatically downloads and caches it. This can significantly decrease download bandwidth and installation time when you have to install the same packages repeatedly (i.e. an upgrade of multiple machines).

Perfect!

That page has got good instructions on how to set it up, but for an overview, it's quite simple. Once you've installed apt-proxy on a ("master") computer that you want to use as a local repository, you can edit a conf file to suit your particular network settings. Then, on  each other ("slave") computer, you change the sources.list file that apt-get uses to point to the ("master") local repository. Easy!

Also, here's another howto that you might find useful:

[http://www.subvs.co.uk/apt-proxy_on_ubuntu](http://www.subvs.co.uk/apt-proxy_on_ubuntu)

> If you have more than one box to update or install software with apt on, apt-proxy can save you a lot of time (and bandwidth). It runs on one box, and others are then set up to update through it. Updates are then stored on the apt-proxy box so that any others that also update can do so a lot quicker than getting them from the mirrors. It also releives a bit of the strain on the mirrors you are using.

So not only is it helpful for you in reducing your own bandwidth usage, it also makes you a better netizen by reducing the load on the official mirrors. A win-win situation for everyone!

---

### Post by SOULRiDER on 2007-08-12
You should add some steps on how to get this working and post it in the Tip and Tutorials forum. Great post!

---

### Post by bluenova on 2007-08-12
What happens when there is a program installed on the slave machine that isn't installed on the master?

---

### Post by kansei on 2007-08-12
good stuff! And here I was *trying* to waste space on a new 1.5TB storage array I have set up (a RAID 5) by running a local full ubuntu mirror.. looks like I might not have to after all! I'll have to play around with this later today.

---

### Post by uber_n00ber on 2007-08-13
Thanks SOULRiDER!

I thought about putting a HOWTO together for the tips forum, but I've only got a single "master" and "slave" set up at the moment, so I'd want to roll it out on to a few more machines with some more thorough testing before offering anyone else advice. It certainly seems to work great with this simple set up, but y'know.... ;)

Also, I'm not sure you'd need anything more than the community guide -- it's not too hard to set up (I'm a n00b myself after all!)

I think the idea of caching updates locally was such a brilliant idea when you're supporting multiple computers, I just wanted to make sure others knew about it!

---

### Post by uber_n00ber on 2007-08-13
> **bluenova said:**
> What happens when there is a program installed on the slave machine that isn't installed on the master?

Well the "master" will only cache apt-get requests from "slaves", so if a program is already installed on the slave there won't be an apt-get to install it, and therefore there won't be anything to cache on the master.

Of course, if the slave removes the program, and uses apt-get to install it again, then it will be using the master as its repository and the program will be cached for other slaves.

---

### Post by uber_n00ber on 2007-08-13
> **kansei said:**
> good stuff! And here I was *trying* to waste space on a new 1.5TB storage array I have set up (a RAID 5) by running a local full ubuntu mirror.. looks like I might not have to after all! I'll have to play around with this later today.

/drools

I think I need some more storage ;)

Let us know how it works for you.

---

### Post by kansei on 2007-08-14
yeah I still haven't gotten around to it, maybe today. there are a bunch of ubuntu computers in the house so it would be great

- 1 ubuntu server (the storage array, also runs a mythtv backend)
- 5 laptops with ubuntu (2 feisty, 2 gutsy 32-bit, 1 gusty 64-bit)
- 4 desktops with ubuntu (3 gutsy, 1 feisty, 1 gutsy 64-bit)

It would be a decent bandwidth savings with my setup definitely.

4 feisty 32-bit
5 gutsy 32-bit
2 gutsy 64-bit

instead of 11 downloads of packages all the time, it'll be just three :)

---

