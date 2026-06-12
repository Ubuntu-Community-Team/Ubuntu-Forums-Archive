---
title: "Old laptop, looking for a quick solution"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by bob phillips on 2005-12-01
Hi

I've an old Sony Vaio (333Mhz, 20G HD, 256MB RAM) I recently installed Ubuntu 5.1 onto - runs beautifully, but slowly!

After reading a few threads about lighter environments (specifically Xubuntu), and having very limited requirements (*), I wondered if I would be better ditching the Breezy Badger and moving to it's cousin.

I have, from this, a few questions:

1. Is it a good idea?
2. How do I scrub the old installation and install the new one?
3. Is it easy/possible to install my 'required' programmes?

(Apologies if there's a New Xub Forum somewhere this would be better posted on)

Thanks in advance,

Bob

(*) = Wireless access via PCMIA card, USB stick auto-mounting, web browse, IMAP mail, OpenOffice2.0, media player, simple photo editing software, CD burning (and if I could, then Palm synch compatability too)

---

### Post by teaker1s on 2005-12-01
1) you don't need to scrub your install-this isn't ms windows just use add aplications and select advanced.
or konsole 'sudo synaptic'

search 'ubuntu-desktop' or 'kubuntu-desktop' or 'xubuntu desktop and install as required

---

### Post by aysiu on 2005-12-01
If you already have Ubuntu installed, you don't need to reinstall.

Follow the instructions in the first link of my sig to get extra repositories. Then:

1. ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```
2. Log out.
3. Under "Session" pick "XFCE"
4. Log in.

That's it.

---

### Post by MrFahrenheit on 2005-12-01
you may want to try iceWM as well

Also, I set up a similar laptop (vaio 266 Mhz) to use FreeNX with the server being a 2.4 Ghz computer.  It works amazingly well.

---

### Post by Iandefor on 2005-12-01
1) Sounds good for your system specs

2) There's not an official Xubuntu ISO yet, but you can install XFCE4 and a whole menagerie of packages for it alongside your current Ubuntu installation. Here's how:

Open up Synaptic. Make sure the Universe and Multiverse repositories are enabled. look for the package Xubuntu-Desktop and install it. 

Log out. When you log back in, before you press enter to begin logging in, click on "Sessions" and select XFCE4 (It might just be XFCE) . You'll have a fully functioning Xubuntu desktop that way. 

3) I don't know about wireless access, but XFCE4 comes with Sensible-browser, the OO that comes with Breezy should work fine, photo editing can be accomplished with the GIMP, and Beep Media Player works well and is available through Synaptic. Check the [wiki]("https://wiki.ubuntu.com/LowEndSystemSupport") for automounting on XFCE4, and there's a [howto on palm synching]("http://www.ubuntuforums.org/showthread.php?t=77387") in these forums already.

---

### Post by az on 2005-12-01
[QUOTE=MrFahrenheit]you may want to try iceWM as well

Also, I set up a similar laptop (vaio 266 Mhz) to use FreeNX with the server being a 2.4 Ghz computer.  It works amazingly well.[/QUOTE]

Install the icewm package and the menu package, too.  Otherwise, your will be confused as to how to run programs.

Once you install these other environments, when you boot into your login manager, select the session you want to run (XFCE or icewm) and you can even make it the default.

---

### Post by bob phillips on 2005-12-01
... well in my post title, i meant 'quick' as in 'runs quickly on my laptop' rather than 'before i can make my cup of tea and get a biscuit' !

Thanks very much - i'll attempt to Xubuntu and Ice my machine and see which one flies the fastest :D 

(It really **isn't** difficult to do Linux, is it?)

Bob

---

### Post by patrick295767 on 2005-12-02
[http://www.ubuntuforums.org/showthread.php?t=64557&page=8](http://www.ubuntuforums.org/showthread.php?t=64557&page=8)

---

