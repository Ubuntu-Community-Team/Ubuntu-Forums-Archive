---
title: "[SOLVED] Fluxbuntu for wimpy machine"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by anchor1te on 2007-10-21
Just installed Gutsy and am over the moon.  Now that I have some sea legs, was wondering what the consensus is on Fluxbuntu.  My desktop is a bit wimpy (not really an issue with Gutsy, seems to be going quite well) and was wondering if installing that would make a noticeable difference  in performance.

---

### Post by corney91 on 2007-10-21
Fluxbox can be run on lower end machines. Posting specs could be more helpful though:).
Also you can give Fluxbox a go by running the below command which will allow you to select it on login, in sessions.

```
sudo apt-get install fluxbox
```

---

### Post by anchor1te on 2007-10-21
Would it make more sense to install Fluxbox to my Ubuntu install, or install Fluxbuntu itself?

---

### Post by corney91 on 2007-10-21
> **anchor1te said:**
> Would it make more sense to install Fluxbox to my Ubuntu install, or install Fluxbuntu itself?

I'd recommend adding it to your current install as you can easily switch to it simply by logging out (it also beats backing up and reinstalling:)). I read in [this thread]("http://ubuntuforums.org/showthread.php?t=581033") that it's not just ubuntu with fluxbox but I don't know what other features would be added, so you may want to check out Fluxbuntu when it's out. But by all means install it fluxbox, as you can always get rid of it.

---

### Post by anchor1te on 2007-10-21
Thank you muchly.  Gonna give it a try.

---

### Post by corney91 on 2007-10-21
> **anchor1te said:**
> Thank you muchly.  Gonna give it a try.

One thing I should mention is that it is highly configurable but relies on text files for keybindings, menu, startup etc. If you prefer a GUI to configure you could try fluxconf which is very simplistic.

---

### Post by RedSquirrel on 2007-10-21
> **anchor1te said:**
> Thank you muchly.  Gonna give it a try.
After you install it, you'll need to generate the menu using the following command in a terminal:

```
sudo update-menus
```

---

### Post by HermanAB on 2007-10-21
The problem is the Gnome and KDE window managers.  Both of those suck big time and are horribly slow.  Faster window managers are available and you can configure KDE or Gnome to use for example IceWM as its window manager.  This will speed things up enormously.  

However, I prefer to simply install Xubuntu which uses Xfce, a very fast desktop system.  Then I install KDE Base as well, only to get a copy of Konqueror, which is the Swiss Army Knife of file managers - Xfce with Konqueror works really well.

Cheers,

Herman

---

### Post by bodhi.zazen on 2007-10-21
FYI: Fluxbuntu is due out soon and I have run the Beta (no, the Beta is not public :) )

It is noticeably faster then Ubuntu + fluxbox in installs in 1.1 Gb (compared to 2.2 Gb for Gutsy)

---

### Post by anchor1te on 2007-10-21
I'm liking the sound of that.  1.5 days to wait!!

---

### Post by bodhi.zazen on 2007-10-21
ooo ... there is a new beta, and a x64 beta as well :)

---

### Post by RedSquirrel on 2007-10-21
> **bodhi.zazen said:**
> FYI: Fluxbuntu is due out soon and I have run the Beta (no, the Beta is not public :) )

It is noticeably faster then Ubuntu + fluxbox in installs in 1.1 Gb (compared to 2.2 Gb for Gutsy)

I wonder if it is faster than my tweaked Ubuntu **command-line system** + Fluxbox... :grin:

---

### Post by markp1989 on 2007-10-21
do the desktop effectts work with fluxbuntu?

---

### Post by RedSquirrel on 2007-10-21
> **markp1989 said:**
> do the desktop effectts work with fluxbuntu?
If you are referring to the effects associated with Compiz Fusion, the answer is no. Compiz is a window manager and so is Fluxbox. You can only run one window manager at a time. ;)

---

### Post by bodhi.zazen on 2007-10-21
> **RedSquirrel said:**
> I wonder if it is faster than my tweaked Ubuntu **command-line system** + Fluxbox... :grin:

I doubt it is faster, but I bet is is close, assuming you did a minimal install + fluxbox.

---

### Post by Orbital75 on 2007-10-21
Not trying to HighJack the thread but how would you compare BlackBox to FluxBox?

---

### Post by bodhi.zazen on 2007-10-22
Blackbox is very similar to fluxbox, although I do not think blackbox is in active development.

---

### Post by RedSquirrel on 2007-10-22
> **bodhi.zazen said:**
> I doubt it is faster, but I bet is is close, assuming you did a minimal install + fluxbox.

Yes, that's what I did (plus a number of speed tweaks). Once Fluxbuntu is out, if I have some time I'll try it and see how it compares.

---

### Post by RedSquirrel on 2007-10-22
> **Orbital75 said:**
> Not trying to HighJack the thread but how would you compare BlackBox to FluxBox?
They are similar. Fluxbox is based on Blackbox code, but it adds a few new features and it is being worked on regularly (bug fixing and adding even more features :)). Blackbox is no longer in active development, as far as I can tell.

---

