---
title: "rar support?"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-07-17
any1 know something to unrar some files i got?

---

### Post by TheRingmaster on 2006-07-17
Download automatrix. This adds support for the rar format. I promise.:p

---

### Post by aysiu on 2006-07-17
1. Enable extra repositories
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. ```
sudo aptitude update
sudo aptitude install rar unrar
```

---

### Post by Ben Sprinkle on 2006-07-17
lol i just went to [http://www.rarlabs.com](http://www.rarlabs.com) and got winrar for linux :D

---

### Post by Uncle Spellbinder on 2006-07-17
> **jpazindustries said:**
> Download automatrix. This adds support for the rar format. I promise.:p

I did that for *Rar* and *7 Zip*, yet I cannot find anything regarding *rar* or *7 Zip* in the menus.

---

### Post by Ragazzo on 2006-07-17
> **Uncle Spellbinder said:**
> I did that for *Rar* and *7 Zip*, yet I cannot find anything regarding *rar* or *7 Zip* in the menus.

Select some files and right-click on them and select Create Archive. If you can choose rar from the drop-down menu, you have it installed.

---

### Post by Uncle Spellbinder on 2006-07-17
> **Ragazzo said:**
> Select some files and right-click on them and select Create Archive. If you can choose rar from the drop-down menu, you have it installed.

You are correct, indeed. Thanks. :-D

---

### Post by godd4242 on 2007-03-20
> **aysiu said:**
> 1. Enable extra repositories
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

2. ```
sudo aptitude update
sudo aptitude install rar unrar
```

Ok this screwed up my sources.list really badly, and ontop of that it gives me this error:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

So no I don't think this works.

---

### Post by aysiu on 2007-03-20
I don't see how it could have screwed up your sources.list "really badly" unless you didn't follow the instructions. The instructions would have you paste the new sources.list (which, I assure you, is not "screwed up") into a blank document, with your old sources.list backup in another file. 

If you didn't follow the instructions properly, you'd be adding sources to your already existing list--you shouldn't be doing that--and that would, in fact, screw up your sources.list badly.

As for the error: ```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
``` That means you have another program trying to access the package manager *dpkg*. If you have Synaptic Package Manager, Adept Package Manager, or Add/Remove Programs open now, **close it**. Then try again.

> So no I don't think this works. You're wrong. Follow the instructions **exactly** and ask questions before judging something to not work. The instructions are tried and true and worked literally thousands of times.

---

### Post by cowlip on 2007-03-20
Also check in the process/task manager if you see any other instances of apt-get or the other programs aysiu mentioned, and the process before updating.

---

### Post by bsegovia on 2007-11-29
> **Ben Sprinkle said:**
> lol i just went to [http://www.rarlabs.com](http://www.rarlabs.com) and got winrar for linux :D


Thanks man, For us noobs, this is a familiar process.

---

### Post by And1945 on 2007-11-29
Hmm... I think I would just go into the Synaptec and download the official rar package. It says something about only beeing good for 40 days, I havent had any problems though...

---

### Post by ptn107 on 2007-11-29
All you need is to enable the multiverse repository and install two packages (rar, unrar).
```
sudo apt-get install rar unrar -y
```

They are also part of the *ubuntu-restricted-extras* package.

---

### Post by And1945 on 2007-11-29
> **ptn107 said:**
> All you need is to enable the multiverse repository and install two packages (rar, unrar).
```
sudo apt-get install rar unrar -y
```

They are also part of the *ubuntu-restricted-extras* package.

I wasn't aware of that, actually. Thanks.

---

### Post by hayshaka on 2008-06-14
It works great, just did it. Make sure Synaptic is closed first though...=p

---

