---
title: "Audacity - reverting to older version"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by tonymoloney on 2007-11-04
I have Audacity 1.3.3 on my system and it is a Beta version with a few problems.
 The Audacity web-site tells me I should really be using 1.2.6
I have downloaded 1.2.6 as a Debian package, but how do I install it?
If i right click on the file and select "Open with Gdebi package installer" a window opens for Gdebi but after a couple of seconds the window closes and nothing gets installed.
Do I have to un-install the 1.3.3 version first?
Tony

---

### Post by tgalati4 on 2007-11-04
>sudo apt-get remove audacity  (this would presumably remove 1.3.3 that already exists)
>sudo apt-get install audacity    (this would presumably install 1.2.6 from the repository)

I've been using 1.3.0 without problems, what problems have you encountered?

---

### Post by tonymoloney on 2007-11-05
If I follow your instructions, won't that re-install 1.3.3 as that is what is listed in Kubuntu add/remove programs?
My biggest problem with 1.3.3 is the new input choices of:
Front Mic Boost:0
Mic Boost:0
Capture:0
Digital:0
I use Audacity for manipulating songs from audio cassettes and I just can't seem to get the input right with 1.3.3
I either get total overload or nothing. I use a Lenovo laptop which only has a mic input jack, but I am able to change this to line-in from the Kmix panel (at least i think I have changed it).
I don't have the same problem with 1.2.6 which I'm running on a Windoze 2000 laptop.

---

### Post by tonymoloney on 2007-11-05
OK. while i've been waiting for a new post, I did what you said and it did what i said. i.e. it removed 1.3.3 then re-installed 1.3.3 'cos that's what it found in the repositories

---

### Post by rsambuca on 2007-11-05
1.3.3 is the version in the repos.  You will have to hunt down an old deb or source from somewhere.

---

### Post by tonymoloney on 2007-11-05
I've done that - but how do I install it?

---

### Post by rsambuca on 2007-11-05
Just double-click it.  If that doesn't work for some reason, try ```
sudo dpkg -i <packagename>
```

---

### Post by tonymoloney on 2007-11-05
When I double click I get this message in a window:

The archive file:///home/tony/Desktop/audacity_1.2.6-0ubuntu1_i386.deb is already open and has been raised.

Sorry, I have to go out now, so I won't be able to continue this until tomorrow. Thanks for your help
Tony

---

