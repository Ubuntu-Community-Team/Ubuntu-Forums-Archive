---
title: "Can Ubuntu Do These Things?"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Stoat on 2007-06-14
I'm itching to switch to Ubuntu, having been totally burned out at the bad performance my laptop has on WinXP, but there's a few things I need to know if Ubuntu can do before I'm willing to switch to it.

**Stream Music From iPods**
Due to limited hard-drive space, I'm forced to keep all my music on my 60GB iPod video and stream it via the USB cable to Winamp using the ml_ipod plugin. Is there a way to do this on Ubuntu?

**Run Live Writer or similar**
I use Windows Live Writer to update my Wordpress blog with proper formatting, and was wondering if it's possible to run this or a similar program under Ubuntu.

Thanks in advance guys. I'm 99% ready to make the switch, I just want to be absoloutly sure I should.

---

### Post by bigken on 2007-06-14
yes to the ipod 

not sure about live writer you might have to use wine to install it

---

### Post by ukripper on 2007-06-14
If  there is any application only XP can run, one solution is, you can easily run XP under ubuntu by using Virtualbox creating a virtual machine. That is what i do when i have to use MS SQL but my ubuntu always runs underneath so I dont miss anything which carries on processing other stuff.

---

### Post by Stoat on 2007-06-14
> **bigken said:**
> yes to the ipod 

not sure about live writer you might have to use wine to install it

What program would you use to stream the music? Does it have the last.fm plugin available? This isn't essential but I love me some music stats :D

---

### Post by Kobalt on 2007-06-14
> **Stoat said:**
> What program would you use to stream the music? Does it have the last.fm plugin available? This isn't essential but I love me some music stats :D
You can use the new 0.11 version of Rhythmbox in order to do that.

---

### Post by Stoat on 2007-06-14
Fantastic! Time allowing, I will make the switch this evening! :)

---

### Post by Kobalt on 2007-06-14
Welcome to Ubuntu then :) !

---

### Post by onero on 2007-06-14
For music, I really like Amarok; it detects devices automatically and it has last.fm support as well. It's a KDE app though, so if Rhythmbox works for you it might be best to stick with it since it's the default. 

I also second the Virtualbox suggestion; it's surprisingly easy and I'm kind of in love with this program now :p

---

### Post by corney91 on 2007-06-14
> **onero said:**
> For music, I really like Amarok; it detects devices automatically and it has last.fm support as well. It's a KDE app though, so if Rhythmbox works for you it might be best to stick with it since it's the default. 

I also second the Virtualbox suggestion; it's surprisingly easy and I'm kind of in love with this program now :p

I'd also recommend Amarok - it's brilliant!

In what ways is Virtualbox different to wine?

---

### Post by Zzl1xndd on 2007-06-14
Also gonna toss my chips with Amarok great program. 

Also  Virtual box creates a Fully functioning windows enviroment like paralles for the Mac.

---

### Post by Anonii on 2007-06-14
> **corney91 said:**
> I'd also recommend Amarok - it's brilliant!

In what ways is Virtualbox different to wine?
Virtualbox emulates Windows. This means that you basically have a fully working Windows system running on your Linux. 
In the other hand, Wine is just an emulation layer, which tries to emulate programs (Gentlemen, don't start shouting "Wine Is Not an Emulator", because I don't know another way to explain it) but not the whole Windows enviroment.

[http://en.wikipedia.org/wiki/Virtualbox](http://en.wikipedia.org/wiki/Virtualbox)
[http://en.wikipedia.org/wiki/WINE](http://en.wikipedia.org/wiki/WINE)

---

### Post by livingtarget on 2007-06-14
VirtualBox is a virtual computer. It acts like it's a computer you can install windows on, except you can run it inside linux. So you have windows running as a program inside linux. There's no 3d acceleration in VirtualBox, so unless you play older games it's not really a gaming solution.

Wine however is more of an implementation of the Windows operating system on linux. Because windows is so complex you can't expect everything to work correctly. So it's hit and miss.

I use VirtualBox for apps like: Photoshop, Flash, Word and a few other things. I only use it occasionally because most of this I can do with linux apps as well.

I use Wine to run World of Warcraft (after tinkering this runs beautiful, a bit slower fps tho).

---

### Post by bluenova on 2007-06-14
> **Stoat said:**
> 
**Run Live Writer or similar**
I use Windows Live Writer to update my Wordpress blog with proper formatting, and was wondering if it's possible to run this or a similar program under Ubuntu.

Package: gnome-blog (0.9.1-3ubuntu1) [universe]
GNOME applet to post to weblog entries

gnome-blog is a panel object (aka applet) that can post to weblogs using bloggerAPI, advogato API, MetaWeblog API or LiveJournal API

It notably works with Blogger.com / Blogspot.com, Advogato.org, Movable Type, WordPress, LiveJournal.com and Pybloxsom.

---------------------------------------------------

Package: drivel (2.0.3-2ubuntu2) [universe]
Blogging client for the GNOME desktop

Drivel is a GNOME client for working with online journals, also known as weblogs or blogs. It retains an elegant design while supporting LiveJournal, Blogger, MovableType, Advogato, and Atom journals, as well as derivatives such as WordPress and Drupal.

It allows you to perform most functions that are supported by the server (posting, friends editing, friend page checking, post editing etc).

It is designed to utilize the new features of GNOME 2.0 including GConf and GTK 2.0.

---

### Post by ukripper on 2007-06-14
> **Stoat said:**
> Fantastic! Time allowing, I will make the switch this evening! :)

Goodluck with your switching. You won't be disappointed with your decision.

---

