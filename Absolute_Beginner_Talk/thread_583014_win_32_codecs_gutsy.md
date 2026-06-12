---
title: "win 32 codecs gutsy"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by sneezymelon on 2007-10-20
How do I install win32 codecs in gutsy??

---

### Post by forestpixie on 2007-10-20
get medibuntu first then you should be able to download it - do these in terminal

```
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
```

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install w32codecs
```

---

### Post by ounas on 2007-10-20
Thanks I needed that as well :)

---

### Post by BLTicklemonster on 2007-10-21
Huh. I would have figured it would have been easier than that.

Thanks!

---

### Post by ant2ne on 2007-10-26
```
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
antsvr@antubuntu:~/scr$ 
```Am I getting screwed cause I got an AMD 64?

---

### Post by FuturePilot on 2007-10-26
> **ant2ne said:**
> ```
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
antsvr@antubuntu:~/scr$ 
```Am I getting screwed cause I got an AMD 64?

There is no w32codecs for 64 bit. However the Medibuntu people have put something together called w64codecs. Try
```
sudo apt-get install w64codecs
```

---

### Post by ant2ne on 2007-10-28
> **FuturePilot said:**
> There is no w32codecs for 64 bit. However the Medibuntu people have put something together called w64codecs. Try
```
sudo apt-get install w64codecs
```

```


antsvr@antubuntu:~$ sudo apt-get install w64codecs
[sudo] password for antsvr:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w64codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
antsvr@antubuntu:~$ 
```

But when I try to play a clip
> 
Video codec 'Windows Media Video 7' is not handled. You might need to install additional plugins to be able to play some types of moviesAny advice?

---

### Post by FG123 on 2007-10-29
> **ant2ne said:**
> ```


antsvr@antubuntu:~$ sudo apt-get install w64codecs
[sudo] password for antsvr:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w64codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
antsvr@antubuntu:~$ 
```

But when I try to play a clip
Any advice?
Try using mplayer (or better yet, SMplayer) if you aren't already. It seems to be the best for handling the widest variety of formats.

---

### Post by andrewoftheelves on 2007-12-18
thanks forest pixie, your code worked like a charm
p.s. i like your name, we should be ubuntu forum friends and be wardens of the enchanted forest.

---

### Post by sonofskywalker3 on 2008-04-29
so is it illegal to watch DVDs in Linux? i keep seeing all these warnings and disclaimers stating that installing the package necessary to watch commercial dvds on my laptop violates the dmca. can someone explain this to me? I just want to watch dvds that i bought and paid for. what's wrong with that?

---

### Post by hellonull on 2008-04-30
> **sonofskywalker3 said:**
> so is it illegal to watch DVDs in Linux? i keep seeing all these warnings and disclaimers stating that installing the package necessary to watch commercial dvds on my laptop violates the dmca. can someone explain this to me? I just want to watch dvds that i bought and paid for. what's wrong with that?

I'm no lawyer, but I'm pretty sure it's perfectly legal. The operating system you use is irrelevant. (Fun fact: almost all DVD players run on Linux.) Whoever is telling you that it's illegal is full of ****.

---

### Post by timcredible on 2008-04-30
> **sonofskywalker3 said:**
> so is it illegal to watch DVDs in Linux?

well..... this topic has been discussed for years, and the bottom line is that the mpeg group wants you to pay them $0.75US for each and every DVD player you own because they own the patent on the mpeg2 format.  if you bought your PC with windows on it, you already paid, but the mpeg group wants you to pay again because they think your PC is now a different DVD player.  some countries uphold this thought in their laws, and some countries have shot it down.  similarly, the group that owns the patent on mp3s want money for each mp3 player.

---

