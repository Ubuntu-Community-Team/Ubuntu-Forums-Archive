---
title: "Downgrading to Firefox 1.5"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by crooked on 2007-01-15
I am very new to Ubuntu [about 3 days] and i think i have gathered the basics. i have many questions and problems but my most immediate one is this:

I used Firefox 1.5 for a long time and was bitterly disappointed by 2.0. I found downgrading  to 1.5 was easy enough with windows XP but I have looked around for a few hours and havn't found anything helpful about how to do it with Ubuntu.

I would really appreciate any help with where to find it and how to install it.

thanks in advance.

---

### Post by useResa on 2007-01-15
I was also disappointed in FF2 and also have looked for a way to downgrade back to 1.5 but could not find a solution.

Looking for a solution I was introduced to [Swiftfox](http://www.getswiftfox.com/).
Since I have installed this - btw: it is based on firefox - I have not had the problems that I had with FF2 (being slow and unexplainable crashes).
To install Swiftfox I have used the instructions that were given for installing Swiftfox in Debian, which can be found [here](http://www.getswiftfox.com/debian.htm).

Maybe Swiftfox can solve your problems as well.

---

### Post by pistcivet on 2007-01-15
Sorry, I can't really help. Though I am also unimpressed with Firefox 2.
I'm using Dapper and Firefox 1.5.0.9 (maybe you should install Dapper instead of Edgy)

In any case, Firefox 1.5 will be discontinued in July, 2007.
We will all be dumping FF 1.5 soon enough. (pity)

Maybe its time to try Epiphany, or Opera.

---

### Post by useResa on 2007-01-15
> **pistcivet said:**
> Maybe its time to try Epiphany, or Opera.
Or Swiftfox  ;)

---

### Post by K.Mandla on 2007-01-15
> **crooked said:**
> I am very new to Ubuntu [about 3 days] and i think i have gathered the basics. i have many questions and problems but my most immediate one is this:

I used Firefox 1.5 for a long time and was bitterly disappointed by 2.0. I found downgrading  to 1.5 was easy enough with windows XP but I have looked around for a few hours and havn't found anything helpful about how to do it with Ubuntu.

I would really appreciate any help with where to find it and how to install it.

thanks in advance.
Assuming you're using 6.10, and you're already at Firefox 2.0, open a terminal and ...

```
sudo apt-get remove firefox
```
Then download the 1.5.0.9 version from the 6.06 repository with this line ...

```
wget http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb
```
All your dependencies should be met (I simulated it on mine), and so you should be able to ...

```
sudo dpkg -i firefox*.deb
```
I should note that I haven't actually done it, but that's what I would do if I wanted to do what  you seem to want to do. :-k

I think the next time you update your system it will try to install Firefox 2.0, though. If you use Synaptic you can just unselect it; from the command line I think you should be able to omit it by including *-firefox* on the command line.

Again, I haven't done these things, so I'm not so sure I'm giving good advice. :roll:

---

### Post by K.Mandla on 2007-01-15
> **pistcivet said:**
> In any case, Firefox 1.5 will be discontinued in July, 2007.
We will all be dumping FF 1.5 soon enough. (pity)
You could download Iceweasel 1.5.0.7 and keep the tarball on hand, so you don't have to use Firefox if you don't like it.

I have it in storage on one drive because I don't like Firefox 2.0 either (too heavy for my tastes), and Iceweasel 1.5.0.7 flies on older machines.

[https://wiki.ubuntu.com/InstallIceweasel](https://wiki.ubuntu.com/InstallIceweasel)

---

### Post by crooked on 2007-01-15
thanks a lot for all your swift replies guys. i am using 6.10.

I tried to do this

> **K.Mandla said:**
> 
```
sudo apt-get remove firefox
```
Then download the 1.5.0.9 version from the 6.06 repository with this line ...

```
wget http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb
```
All your dependencies should be met (I simulated it on mine), and so you should be able to ...

```
sudo dpkg -i firefox*.deb
```



but got this error message

```
dpkg: regarding firefox_1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb containing firefox:
 mozilla-firefox-locale-en-gb conflicts with firefox (<< 1.99)
  firefox (version 1.5.dfsg+1.5.0.9-0ubuntu0.6.06) is to be installed.
dpkg: error processing firefox_1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb (--install):
 conflicting packages - not installing firefox
Errors were encountered while processing:
 firefox_1.5.dfsg+1.5.0.9-0ubuntu0.6.06_i386.deb

```

---

### Post by useResa on 2007-01-16
> **crooked said:**
> 
 mozilla-firefox-locale-en-gb conflicts with firefox (<< 1.99)

My understanding of the error message is that you have this specific package installed for FF2 and that it needs to be removed.
My suggestion, search this package in Synaptics and remove it.
Next try the installation again.

Good luck.

---

### Post by Colonel Kilkenny on 2007-01-16
I haven't tried removing firefox but I think that it may be a little more complicated operation than one would think. Firefox and it's components (Gecko etc.) are more than just a web browser and firmly integrated into Ubuntu. Other parts of Ubuntu may need firefox 2.0 for doing something which has nothing to do with you surfing on the net.

I'd suggest you let Firefox 2 stay and just install another browser (Opera, Epiphany, Konqueror, older Firefox...).

But as I said, I have no experience about the current situation between Firefox and it's dependencies..

---

### Post by crooked on 2007-01-16
i have found a solution now. thanks a lot for everyone's help. much appreciated.

---

