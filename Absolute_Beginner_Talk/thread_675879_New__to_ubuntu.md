---
title: "New  to ubuntu"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by pedrom169 on 2008-01-23
hi
i was wondering if anyone could help me out with a few questions

1) i have downloaded the 32bit and 64 bit ubuntu and burnt it to disk. i was wondering which one would be best?
my spec is

AMD64 x2 3600+
1gb DDR2 ram
Recent nvidia graphic card. (not sure which one)

2) i have been told off a friend that it doesnt come with any codecs installed where can i get these codecs? (i.e. mp3, avi, divx etc)

3) i have a ipod. i was wondering the best program to sync my ipod with ubuntu.

thanks in advance.

---

### Post by housam on 2008-01-23
> **pedrom169 said:**
> 

1) i have downloaded the 32bit and 64 bit ubuntu and burnt it to disk. i was wondering which one would be best?
my spec is

AMD64 x2 3600+
1gb DDR2 ram
Recent nvidia graphic card. (not sure which one)

.

64 bit is the best for your box.

---

### Post by kpkeerthi on 2008-01-23
1. There is no 64-bit JRE yet. So go with 64-bit if Java is not important for you.
2. You would need **ubuntu-restricted-extras** package. 
3. gtk-pod.

To install a package, open a terminal and type
```

sudo aptitude install <package-name>

```

Or

Search and Install using Synaptic package manager from System menu.

---

### Post by rhc on 2008-01-23
2)From Applications>>Add-Remove type the codec you want.
It ll appear as gstreamer bla bla something.
Download it.

---

### Post by rosegarden78 on 2008-01-23
32-bit if you intend to use for computer for real life.  Don't like iPod wouldn't know except they're mountable like any other device in /etc/fstab and many programs available for sync,  What was the last part?  Oh yeah install the restricted extras from Add/Remove Programs or Synaptic package manager.

---

### Post by Kingfield on 2008-01-23
64bit

Just the same. And if you are hoping to upgrade ram definately 64bit.

There are virtually no problems only affecting 64bit if you are using it casually.

Codecs - Search Automatix, easiest way for first-timers.

As for iPod, gtkpod. After gtkpod I don't even consider iTunes.

---

### Post by rhc on 2008-01-23
I don't suggest Automatix for codecs.
It caused trouble for me once,and some other people expressed it.
Add-Remove is easy one.
If you can't find it from there,you can find in Synaptic.Just say that which codec you want,here.

---

### Post by hyper_ch on 2008-01-23
If you have no experience go first with 32 bit... there are still a few challenges if you want to use 64 bit.

For the graphic card, use then the inbuilt restricted drivers manager... after installation upon booting and logging into your machine, there will be a a notice on the bottom right in the taskbar of your screen (I think its the bottom right....)

Amarok can deal with iPods (search the forum for that)

and for codecs:

- enable the universe and multiverse repos
- add the medibuntu repos

then just run
```

sudo apt-get update && sudo apt-get install ubuntu-restricted-extras libdvdcss2

```
That should take care most of it.

P.S.: Automatix is not recommended.

---

### Post by smurphy_it on 2008-01-23
With Ubuntu, rhythmbox seems default media player.  Rhythmbox will handle most of the ipods by default.  Some Nano's have been problematic I hear, usually connect it to a windows box once to upgrade the firmware, and it will work flawless in Linux after that.

Other entries above will setup your codecs.

Usually there isn't much of a performance hit with 64 bit vs 32 bit.  The support is good for both, and java will work with 64 bit.  You should note that the adobe flash linux version is a 32-bit app only so if there is any support for it, it will be for 32 bit only.  You can still install it in a 64 bit o/s though.

---

