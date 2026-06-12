---
title: "Package management without internet?"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by wrycatcher on 2006-12-20
OK, **newbie** question...

My main computer is Ubuntu Edgy with a broadband connection.  My secondary computer is older with _no_ internet connection or network connection.   If I want to load a package onto the older PC, I can't use things like apt-get or Synaptic which depend upon an internet connection.  What is the simplest way to go about doing package management?  Perhaps via a burned CD or a USB flash drive?

---

### Post by bodhi.zazen on 2006-12-20
You will have to resolve dependencies on your own.

Transfer the .deb file to you computer.

Install with:

dpkg -i package_name.deb

---

### Post by slackjack on 2006-12-20
Yea, you could put the .deb or files ot source code on a flash drive. But some apps that you need may also be on the ubuntu install disk. You can use "Add/Remove Programs" for this. Just search for the package, and if its on the cd, install it.

---

### Post by wrycatcher on 2006-12-20
And how do I get the .deb file?  (now I'm *really* showing my ignorance)

---

### Post by wrycatcher on 2006-12-20
Great.  However, what if the older system is running something like DSL instead of Ubuntu (for performance reasons).

---

### Post by bodhi.zazen on 2006-12-20
You have to download and transfer the deb files....

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

As far as DSL, well although I like it, you will likely have compatibility problems.

Try Fluxbuntu, 100 % Ubuntu compatible 8)

[Main page](http://fluxbuntu.org/)

	[forums](http://community.fluxbuntu.org/)

	[ Download fluxbuntu-nbuild1-rev2-desktop-i386.iso](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/fluxbuntu-nbuild1-rev2-desktop-i386.iso)

	MD5SUM  : 
	> c054428c46a1b5ffaab4295bc7db3c9b  fluxbuntu-nbuild1-rev2-desktop-i386.iso

---

### Post by wrycatcher on 2006-12-20
Fluxbuntu, huh?  Looks promising.  Is it just a very lightweight Ubuntu?  I've managed to do some things to speed up Ubunu on my main system but no amount of optimization of Ubuntu is likely to be adequate on the slower machine.

Thanks for the tips about non-online package installation.  That's good stuff.  I'll give Fluxbunu a try, definitely.

---

### Post by bodhi.zazen on 2006-12-20
Fulxbuntu is in fact speed optimized, it is not "just Ubuntu + fluxbox"

---

### Post by xabbott on 2006-12-20
I recommend check out this [guide]("http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/") as well.

---

### Post by jbayone on 2006-12-20
There are a few ways to go about it.  You can download and burn Ubuntu Plus, which has some codecs and other nice stuff on it, not too big of a download.  There is also APTonCD, just google it.  Its a script that burns all the dependencies you want from your internet Ubuntu machine to the one with no connection.

---

### Post by seijuro on 2006-12-20
this is a cool way to do package downloads w/o having internet if you can get internet to your computer at least once to update your repos. open a terminal and run:

```
sudo apt-get -qq --print-uris install package-name | cut -d\' -f 2 > urilist
```

then just take your text file urilist to somewhere you have access to internet and download the files from the list save them so some kind of media(cd most likely) bring them home drop them into /var/cache/apt/archives then run whatever method of package install you like apt-get, aptitude, synaptic.

---

### Post by K.Mandla on 2006-12-20
> **jbayone said:**
> There is also APTonCD. ...
Ditto that. I think [APTonCD]("http://aptoncd.sourceforge.net/index.html") is what you need, since I think what you're after is a way to download entire software packages plus all the dependencies to an offline machine. 

APTonCD makes it infinitely easier than the old way. ](*,)

---

### Post by bodhi.zazen on 2006-12-20
> **seijuro said:**
> 

```
sudo apt-get -qq --print-uris install package-name | cut -d\' -f 2 > urilist
```



8)

---

### Post by wrycatcher on 2006-12-21
Great stuff folks. I will definitely check these out.  I think Fluxbuntu might be something for me to investigate further, and I can use the APTonCD for additional packages no matter what derivative of Ubuntu I run.  Is *derivative* the right term for things like Xbuntu, Kbuntu and Fluxbuntu?

---

### Post by TwoWordz on 2006-12-21
1

---

### Post by wrycatcher on 2006-12-30
Here's my experience, for the benefit of others...

Installing Ubuntu on main machine and Fluxbuntu on the second machine, then using ATPonCD to basically transfer some applications from one to the next:  uh...less than optimal, a lot of dependency issues because Ubuntu Edgy is a couple versions ahead of Fluxbuntu's debian.  Most everything I tried failed with several depenency issues starting with "libc.."

At this point I figured if I was going to have to resolve a lot of dependencies myself, I'd just go with DSL on the second machine.  Trying to resolve dependencies manually is painful.  I would rather do a root canal on myself.

Where I'm at:  Uh...vanilla DSL now on 2nd machine.  Will update with appropriate applications manually as I find time (and patience).

---

