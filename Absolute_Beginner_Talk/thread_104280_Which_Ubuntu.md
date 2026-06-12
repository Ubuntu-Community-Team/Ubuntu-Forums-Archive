---
title: "Which Ubuntu?"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by Chiaro on 2005-12-15
I need to reformat my cousin's computer. Somehow it got a virus. I thought, "Hey, if it got a virus, put Linux on it!". BUT, their computer isn't fit for regular old Ubuntu. They have a P2 350Mhz, 128MB of RAM and 2.43GB. If I installed Ubuntu, they'd have just under 400MB. And that's without adding additional things. Then I thought about Xubuntu. Small, good, it would've been the way to go. But the only good P2P client for it is aMule. My cousin loves her LimeWire. 

So, without thinking, I thought about just typing in this in a server install:

```
sudo apt-get gnome firefox gaim xmms
```

Would this work? Or should I think of something else?

---

### Post by Zelut on 2005-12-15
Well that would isntall the basic programs that your cousin uses but those also depend on other packages, which would include gnome or some other desktop GUI.  So, you're going to need to pick a GDM and do your best...  maybe get a larger drive for cheap?

---

### Post by Chiaro on 2005-12-15
So, uncomment the universe lines, then type in

```
sudo apt-get install gnome firefox win32codecs xmms gaim gdm
```

and then add limewire via the Ubuntuguide.org after install?

---

### Post by hod139 on 2005-12-15
You can[ install limewire]("https://wiki.ubuntu.com/P2PHowTo?highlight=%28limewire%29#head-7fb2803e9171c3a6b582e29c5bf1a7b907b4044b") on ubuntu if you want.  That said, I like your first idea of Xubuntu, and then installing limewire.

---

### Post by Chiaro on 2005-12-15
>_> I know how to install Limewire, I've looked up UbuntuGuide. I'll follow the instructions on that.

That said, is it possible to install Limewire on Xubuntu?

---

### Post by Kyral on 2005-12-15
For that level I'd skip Xubuntu (not even XFCE would perform well) and try something minimal like Fluxbox. There is wikipage (written in part by me :P) that explains how to make it go far

[http://wiki.ubuntu.com/Fluxbox]("http://wiki.ubuntu.com/Fluxbox")
[]("http://www.ubuntuforums.org/wiki.ubuntu.com/Fluxbox") 
It ain't gonna be pretty mind you, but it runs fast. 

Oh the better link to install Limewire is [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2511334]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2511334")

---

### Post by Estariel on 2005-12-16
[QUOTE=Chiaro]>_> I know how to install Limewire, I've looked up UbuntuGuide. I'll follow the instructions on that.

That said, is it possible to install Limewire on Xubuntu?[/QUOTE]

Yes, limewire does not depend on GNOME. (very very few programs depend on all of gnome - or on all of KDE...)

---

### Post by Deaf_Head on 2005-12-16
BTW how well does a system like taht run ubuntu? I have the same setup with a little more ram and 15 gigs of space ina  closet i've been trying to figure out what to do with =X

---

### Post by Chiaro on 2005-12-16
I used to run Ubuntu on my P2 400 with 128mb RAM. It worked pretty well, give it a shot.

And Kyral, all I have to say is ;_;. Really long install. I need some kind of Linux that's easy to use for people who are used to Windows. Basically, I want GNOME, but not Ubuntu. I want GNOME without the programs, which I'll add manually.

Any help with that?

---

### Post by majikstreet on 2005-12-16
You could use xfce, but not gnome!!!

---

### Post by Chiaro on 2005-12-16
Trust me dude, GNOME works with their system. Granted, their system is about 66mhz slower, but it isn't that big of a difference. Now, assume I wanted GNOME and please, *please* answer this:

> Basically, I want GNOME, but not Ubuntu. I want GNOME without the programs, which I'll add manually.


---

### Post by hod139 on 2005-12-17
[QUOTE=Chiaro]I used to run Ubuntu on my P2 400 with 128mb RAM. It worked pretty well, give it a shot.

And Kyral, all I have to say is ;_;. Really long install. I need some kind of Linux that's easy to use for people who are used to Windows. Basically, I want GNOME, but not Ubuntu. I want GNOME without the programs, which I'll add manually.

Any help with that?[/QUOTE]

I've never heard this asked before.  You may try a **server** install of ubuntu, and then install gdm and gnome-core.  This is just a guess though, not sure if it will give a fully working gnome desktop.
```

sudo apt-get install gdm gnome-core.

```

---

### Post by DigitalAxis on 2005-12-17
I've got a PII-333 Mhz system that runs XFCE 4 very nicely.  It's fast (not mindblowing, but fast), and that's with ALL of XFCE 4, plus the extras, installed.  XFCE 4 is surprisingly modular; you can remove practically any piece you don't want.

<snip>

EDIT: Realized you weren't interested in XFCE 4 anyway

---

