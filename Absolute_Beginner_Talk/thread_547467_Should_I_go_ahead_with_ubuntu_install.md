---
title: "Should I go ahead with ubuntu install?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-10
Hi all,
I want to install Ubuntu on my PC, (I already have Ubuntu installed on one machine) and I was wondering if people have experienced any problems with similar specs. 

AMD 3500+ 64bit
2GB RAM
250GB SATA
ATI RADEON X1950 PRO 512mb


Only asking because I'll be installing Ubuntu 64bit edition which I have not installed before.

By the way. Any thoughts on Kubuntu instead of Ubuntu? I know it's a personal preference but I have never used Kubuntu before. Only cause it seems to have too many things come with it and because Ubuntu comes originally with gnome

---

### Post by rich.bradshaw on 2007-09-10
ATi cards aren't that well supported - you will need to use Envy to download drivers for it to work nicely...


[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
 
I know it says nvidia, but it does Ati as well!

Apart from that it will be fine!

Why not try the live cd of Kubuntu - I prefer it. Gnome looks more like Mac OS 8 - not very modern. KDE 4 comes out this year (hopfefully!) and promises to be awesome!

---

### Post by ROUBOS on 2007-09-10
Thanks for that link.
Yes I'll download a Kubuntu 64bit cd and run it live. See what I think of it.
Just that Gnome seems lighter than KDE.

---

### Post by hyper_ch on 2007-09-10
If you have no experience with linux I'd rather recommend you to use the 32-bit version first. A few things are simpler with that (like flash)

---

### Post by ROUBOS on 2007-09-10
I've got an other machine running 32bit version with Beryl and all.
Just thought that it'll be better to run 64bit version since my CPU is 64bit

---

### Post by hyper_ch on 2007-09-10
well, you can use a 64bit system but not everything is ported to 64bit yet and you may enounter a few challenges ;)

---

### Post by ukripper on 2007-09-10
Only problem I can see is ATI card, if you  install it with envy as suggested above then its all good

---

### Post by Er1ck on 2007-09-10
I just finished installing the 64-bit version of ubuntu on my brother's laptop and it was def challenging and as far as flash goes (it is not supported by adobe at all) but the script provided in one of the forums which is basically an automated installation did the trick for me and now my brother's laptop is running ubuntu 64-bit flawlessly. The wireless card was also a bit tricky but through googling I was lucky enough to get it to work as well as beryl (along with his ati mobility card). Definitely check to see if your ATI card is supported (because I know modern ones aren't as well supported).

---

### Post by ROUBOS on 2007-09-10
OK, so what's the major difference between the 32bit and the 64bit? Why all the trouble. Is 64bit suppose to be faster?  And better? What about the dual core processors? What do they use?

---

### Post by ukripper on 2007-09-10
Here is lil comparison between the two - 64bit is certainly faster if you are using math intensive apps or multimedia apps like converters, video editing.....

[http://www.pcstats.com/articleview.cfm?articleID=1665](http://www.pcstats.com/articleview.cfm?articleID=1665)



Here are few benchmarks with Ubuntu Edgy -

[http://64-bit-computers.com/linux-ubuntu-610-64-bit-vs-32-bit-benchmark-test.html](http://64-bit-computers.com/linux-ubuntu-610-64-bit-vs-32-bit-benchmark-test.html)

Here you can find the poll for 64bit ubuntu users -
[http://ubuntuforums.org/showthread.php?t=403064](http://ubuntuforums.org/showthread.php?t=403064)

---

### Post by ShagzModo on 2007-09-10
The ATI card will not cause any problems....

---

### Post by Brightbelt on 2007-09-10
I thought I'd share my experience with Kubuntu. On Every install I've had with Kubuntu, Kubuntu had trouble mounting my hard drives. And these were hard drives which Gnome always mounted with no problems at all. 

For instance, my HP has an internal,  swappable bay 2nd hard drive.  On Gnome, it was Never a problem with mounting it. With Kubuntu, I had to mount it in the command line which was a royal pain. And even then, I seldom got the icon on my desktop the way I wanted. 

Finally I realized that I could get Gnome to look the way I wanted without all the hassle.

This has just been my experience; take it or leave it. ;)
Frank B.

---

### Post by ROUBOS on 2007-09-10
I have been using Ubuntu with Beryl and it looks great. I have not used Kubuntu before, so I thought about getting people's opinion on it. Seems to be a big thing Gnome vs KDE.
Oh well I think I'll stick to Gnome... nice simple and it works.

---

### Post by ROUBOS on 2007-09-10
Linus prefers KDE
[http://www.desktoplinux.com/news/NS8745257437.html](http://www.desktoplinux.com/news/NS8745257437.html)

---

### Post by meindian523 on 2007-09-10
> **Erick87 said:**
> I just finished installing the 64-bit version of ubuntu on my brother's laptop and it was def challenging and as far as flash goes (it is not supported by adobe at all) but the script provided in one of the forums which is basically an automated installation did the trick for me and now my brother's laptop is running ubuntu 64-bit flawlessly. The wireless card was also a bit tricky but through googling I was lucky enough to get it to work as well as beryl (along with his ati mobility card). Definitely check to see if your ATI card is supported (because I know modern ones aren't as well supported).


Please refer this thread and help other *buntu users:

[http://ubuntuforums.org/showthread.php?p=3340200#post3340200](http://ubuntuforums.org/showthread.php?p=3340200#post3340200)

---

### Post by por100pre1 on 2007-09-10
> **ROUBOS said:**
> Linus prefers KDE
[http://www.desktoplinux.com/news/NS8745257437.html](http://www.desktoplinux.com/news/NS8745257437.html)

Forget Linus' opinions, try KDE yourself:

```
sudo aptitude install kubuntu-desktop
```

(kdm will be installed but at prompt select gdm)

Go to login screen and select KDE and have fun.

---

### Post by Brightbelt on 2007-09-10
With all due respect to Roubos (and Linus!), I probably would have stuck with KDE were it not for the mounting issues.  There is a lot about KDE that is very likable. 

I am still not sure whether I like the one-click folder access or not. In some ways, it is very convenient, but at times, it has gotten me into trouble when I moved too fast and all of the sudden something was open that I didn't mean to be, and I was somewhere I didn't want to be etc. 

But regarding Linus and his seeming contempt for Gnome, it's also not the first time a creation (ie, gnome/a linux desktop in general) has ended up turning on its creator(!) It's a loose analogy, I know.

Just a thought, ;) ...Frank B.

---

