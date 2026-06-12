---
title: "Can I un-install XUbuntu?"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Tristicus on 2007-12-09
Well, in my other thread about my PC freezing up, I installed XUbuntu to make this old piece run faster. Well, it runs a little faster, and I should probably leave it, but I like this better (Gnome instead of Xfce).

So, can I just run 

```

sudo apt-get uninstall xubuntu

```

or what?

Running on a P3 500mhz, 256mb RAM machine, so it is slow, and this is why I installed Xubuntu.

---

### Post by overdrank on 2007-12-09
> **Tristicus said:**
> Well, in my other thread about my PC freezing up, I installed XUbuntu to make this old piece run faster. Well, it runs a little faster, and I should probably leave it, but I like this better (Gnome instead of Xfce).

So, can I just run 

```

sudo apt-get uninstall xubuntu

```

or what?

Running on a P3 500mhz, 256mb RAM machine, so it is slow, and this is why I installed Xubuntu.

HI and maybe this will help
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by spiderbatdad on 2007-12-09
```
sudo apt-get remove --purge xubuntu-desktop
```

---

### Post by PmDematagoda on 2007-12-09
Are you sure you want to use GNOME again on 256Mb ram? It may slow down the PC even more.

Why don't you try Fluxbox? It may be better than Xfce for you and would also be faster, you can install Fluxbox using this [guide.]("https://help.ubuntu.com/community/Fluxbox")

---

### Post by nikoPSK on 2007-12-09
> **Tristicus said:**
> Well, in my other thread about my PC freezing up, I installed XUbuntu to make this old piece run faster. Well, it runs a little faster, and I should probably leave it, but I like this better (Gnome instead of Xfce).

So, can I just run 

```

sudo apt-get uninstall xubuntu

```or what?

Running on a P3 500mhz, 256mb RAM machine, so it is slow, and this is why I installed Xubuntu.

sorry, I find that funny. :lolflag:

---

### Post by Tristicus on 2007-12-09
Thanks for the quick repsonses.

I would install Flux, but I heard it is non GUI, and I am a noob and need a GUI interface. Plus I will be upgrading to a P4 with 1.5gb RAM soon anyways (These are my messing around computers BTW). 

I will install flux probably once I get the new build up and running though!

---

### Post by PmDematagoda on 2007-12-09
Fluxbox is not CLI, it is a GUI, if you want some screenshots of it, look [here]("http://images.google.lk/images?q=FLuxbox&hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=hps&um=1&ie=UTF-8&sa=X&oi=images&ct=title").

---

### Post by Tristicus on 2007-12-09
Nice...this shot looks nice,

[http://www.freesbie.org/share/1.1/manual/fluxbox.png](http://www.freesbie.org/share/1.1/manual/fluxbox.png)

Might install it later.

---

### Post by nikoPSK on 2007-12-09
yes, fluxbox is great. :popcorn:

---

### Post by Tristicus on 2007-12-09
Now for more noob questions!

What is the code to just install it here without erasing all my info?
Will it erase everything?
Is it hard to run? It looks a lot less GUI than Ubuntu, but still GUI.

---

### Post by aysiu on 2007-12-09
> **Tristicus said:**
> Now for more noob questions!

What is the code to just install it here without erasing all my info?
Will it erase everything?
Is it hard to run? It looks a lot less GUI than Ubuntu, but still GUI.
**Step 1**
[Make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources)

**Step 2**
Paste this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update && sudo apt-get install fluxbox
```

**Step 3**
Log out of Gnome. At the login screen go to Options and select the session to be Fluxbox instead of Gnome. Then log in.

Beware! The Fluxbox you see in all the cool-looking screenshots is highly customized. If you install just Fluxbox, it'll be very plain-looking with minimal immediate functionality.

---

### Post by nikoPSK on 2007-12-09
I know with ubuntu you can go like:

sudo apt-get install gnome-desktop

or something.

---

### Post by aysiu on 2007-12-09
> **nikoPSK said:**
> I know with ubuntu you can go like:

sudo apt-get install gnome-desktop

or something.
No, it would be ```
sudo apt-get install gnome-desktop-environment
``` or ```
sudo apt-get install gnome-core
``` or ```
sudo apt-get install ubuntu-desktop
```

---

### Post by nikoPSK on 2007-12-09
> **aysiu said:**
> **Step 1**
[Make sure you have extra repositories enabled]("http://www.psychocats.net/ubuntu/sources")

**Step 2**
Paste this command in [the terminal]("http://www.psychocats.net/ubuntu/terminal"): ```
sudo apt-get update && sudo apt-get install fluxbox
```**Step 3**
Log out of Gnome. At the login screen go to Options and select the session to be Fluxbox instead of Gnome. Then log in.

Beware! The Fluxbox you see in all the cool-looking screenshots is highly customized. If you install just Fluxbox, it'll be very plain-looking with minimal immediate functionality.

aha, well now I know as well, thats aysiu.

---

### Post by Tristicus on 2007-12-09
Thanks guys!

---

### Post by nikoPSK on 2007-12-09
np:popcorn:, we are all here to help. Remeber, everyone had to begin, so we know about it.

---

### Post by RedSquirrel on 2007-12-09
After you install fluxbox with that apt-get command, be sure to generate the default menu:

```
sudo update-menus
```See the link in my signature if you want a more complete/interesting menu...

---

### Post by Tristicus on 2007-12-09
Alright thanks. And can I do the same thing I did with Xubuntu? Like install, and switch between sessions, and if I do not like it, remove it?

---

### Post by nikoPSK on 2007-12-09
@aysiu, I forgot the command, I was just rescanning through my ubuntu book (one of three) and saw it and remembered. :)

---

### Post by aysiu on 2007-12-09
> **Tristicus said:**
> Alright thanks. And can I do the same thing I did with Xubuntu? Like install, and switch between sessions, and if I do not like it, remove it?
Yes. This can be done with any desktop environment (Xfce, Gnome, KDE) or window manager (IceWM, Fluxbox, Enlightenment).

---

