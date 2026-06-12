---
title: "How do i..."
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by DavidBrandau on 2007-05-11
how do i redirect the repository to look at a cd?

I've posted a couple of times today, and my other questions have gotten answered, but this is the one that is going to deter me from Ubuntu.

If i can't download apps, or the codecs to make DVD's play and burn them to cd, then i won't be able to switch from XP. I don't have an internent connection at home, only at work.

Can someone please help?

I'm trying to do this over the weekend, and my work-week ends at 5 today....:(

---

### Post by aysiu on 2007-05-11
Is the CD a genuine Ubuntu CD? Or is it just a random data CD with .deb files on it?

---

### Post by DavidBrandau on 2007-05-11
it's a random, with .deb's.


is there an official Ubunutu app cd image?

---

### Post by aysiu on 2007-05-11
Well, it doesn't have to be "official" as in "produced by Canonical," but it can't just be a collection of .deb files if you want the package manager to recognize it as a repository source.

There used to be an unofficial add-on CD, but it hasn't seen much action since Dapper:
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

APTonCD helps you make a CD repository correctly:
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

But you don't need to have the CD be an actual repository. If you have all the .deb files you need, just copy them to your desktop and then type these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by DavidBrandau on 2007-05-11
hey,

thank you very much for helping me. I'll check this out over the weekend, if this is the problem i've been having, i'm going to laugh histerically and then cry!

thx

---

### Post by aysiu on 2007-05-11
Ubuntu *sans* internet connection = misery

---

### Post by DavidBrandau on 2007-05-14
Well,

Got a new HDD and CDrom for my laptop so that helps with doing an install of Ubuntu. Installed 6.10.

For some reason Fiesty wouldn't run, i'll have to burn another image. Anyways, I had to re-install XP on one partition and instiall Ubuntu on another.

I'll have to try the Repo CD after work today, see if it worx.

---

