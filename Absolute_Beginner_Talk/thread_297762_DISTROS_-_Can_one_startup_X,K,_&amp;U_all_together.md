---
title: "DISTROS - Can one startup X,K, &amp;U all together?"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Shibby73 on 2006-11-11
Is it possible to run all of the distros under or overtop of say DAPPER?

I have noticed some threads about "the best media player" and what not.
Hey I don't even know how to find media files and streams using this bird... but I don't want to reinstall or erase my HDD to try one out either.  I definitely do not want to do a bunch of programming to make them each work in Dapper.

So what gives, where should someone start?  U, X, K?

Perhaps I have to go to the IRC channels and hope I don't seem like a young boy to a strange man... afterall getting free apps on this thing is kinda like TRICK OR TREAT at your neighbors.  You don't know what your getting and what it does.  I imagine the old pros from Linux in here could make their own spyware and give it to you and you'd never know the difference.

I would like to use Privoxy and Torr on this computer, I want total anonymity when I go to sites and browse, especially if I am going to IRC advertising my nubile nature.

Also I want to download some music to test these apps out, is there free music around?  I am sure there is free ILLEGAL music around, I am asking for the free stuff, or even FM or Video feeds etc.


Thanks,

-Steve 

:twisted:

---

### Post by Peepsalot on 2006-11-11
The only main difference in these "distros" are the desktop environments, which can easily be installed on the same installation.
```

sudo aptitude install kubuntu-desktop
sudo aptitude install xubuntu-desktop

```
When you get to the desktop login screen, there is a button that i think says Session where you can choose to go to KDE, XFCE, or gnome

---

### Post by Tomosaur on 2006-11-11
I don't really understand what you're asking. A Linux distribution is just the Linux kernel, probably customised with a few modules, and then everything else is just an application. The most obvious difference is branding: you generally can't tell the difference between one distribution and another until you get into the more complex stuff. You won't need to install a whole new distribution to play music either. Just download whichever program you want from synaptic, or get it from a website if it's not available there.

The differences between Ubuntu, Kubuntu, and Xubuntu are only cosmetic, and each can become another simply by installing Gnome, KDE, or XFCE.

---

### Post by strabes on 2006-11-11
peepsalot is correct in what he said.

When I did this dapper, those packages installed KDE and XFCE like they should, but they also changed my bootsplash (the initial screen after GRUB when dapper is loading) which I didn't like. If you want to change your bootsplash back to the default one, run this command:

```
sudo update-alternatives --config usplash-artwork.so
```

Then you can select which bootsplash you want to use.

---

### Post by Sef on 2006-11-11
You can install different apps under the different distros.  For example, I use Ubuntu, but have download K3b, a KDE app.  The download installs all the depedencies needed.

---

### Post by Velotix on 2006-11-11
I have a [minor problem related to this](http://www.ubuntuforums.org/showthread.php?t=297662). The best package to start with if you want to test all the Ubuntu distros is vanilla Ubuntu. Starting with Xubuntu does strange things.

---

