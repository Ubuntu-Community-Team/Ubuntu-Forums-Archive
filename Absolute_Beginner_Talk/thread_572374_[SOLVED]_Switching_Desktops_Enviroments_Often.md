---
title: "[SOLVED] Switching Desktops Enviroments Often?"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by Krextyl on 2007-10-10
I've been getting familar with Linux thru the Live Cd's and have settled on pretty much everything but haven't really payed much attention to KDE vs Gnome (or others). Should I make the decision prior to my install (by default i would just pick gnome in the standard ubuntu package) or is it not a big deal to switch back and forth between enviroments. 

Part two of my question is I know you can install some app's written for the other such as K3B can be installed on a system running a Gnome enviroment even though it was intended for a KDE enviroment, but can I port over certain specific features that relate to one of the enviroments (forgive me here the following may be a bad example, but like I said I haven't experimented much yet) I saw a screenshot of the KDE enviroment having several a pretty nifty photo preview options when your browsing your photos, is this feature easy to bring over (if Gnome doesn't do it just like this) or is that to far in the code to try and translate over with out getting pretty advanced into the programing aspects of Linux - which by no means do I want to tackle anywhere in the near future.

Thanks All.

---

### Post by Dr Small on 2007-10-10
You can install multiple environments on top of your default installation, and it can run the applications designed for that environment.

Dr Small

---

### Post by swisscow on 2007-10-10
Good question about porting the features between desktop environments. From what I have seen there are different features offered by Gnome and KDE which essentially do the same thing, but there are also some features which only appear in one of them. Best thing to do is to install both, play around until you decide what you like best. Then when you get bored swap back or try the other ones out there!

---

### Post by LaRoza on 2007-10-10
You can have many DE's at once, you choose which one to use before logging on. Assuming you install GNOME, you can get KDE with:

```

sudo aptitude install kde-core

```

To get the Kubuntu apps:

```

sudo aptitude install kubuntu-desktop

```

To get Fluxbox, the DE of my choice:

```

sudo aptitude install fluxbox

```

I never had a problem with "K" apps or GNOME apps on the other.

I think I have 14 DE's installed at the moment. Fluxbox is the default, but I use KDE or GNOME sometimes.

---

### Post by Krextyl on 2007-10-10
First off thanks for the quick reply posts.

And all I got to say is SWEET!! I didn't know you could have multiple DE's installed at once to switch between - That's awesome!

LaRoza you said you have 14 DE's, holly cow. I need to do some reading up I had no idea there was even near that many out there - I assumed there where others I knew of one (but forgot the name) for low powered computers but other than that, hadn't really searched'em.

Where do you find most of yours is there a list by chance of them out there kinda like distro watch for the vairous distros???

I would still like to find out about porting over the features though once I settle on the one that best fits, I will probably like to bring over a few things here and there if possible with out to much headache. Humm this maybe a seperate thread for a later date cause ppl probably need to know specifics in order to address the question instead of the broader question. :roll:

---

### Post by Dr Small on 2007-10-10
I would too, like to find out where he got all of his DE's :p
But before I reinstalled, I had fluxbox, gnome, icewm, blackbox, amiwm, enlightenment, dwm and xfce4. I hate KDE :p

Dr Small

---

### Post by rsambuca on 2007-10-10
Here is a [good website]("http://xwinman.org/index.php") listing many Desktop Environments and Window Managers.

---

### Post by maybeway36 on 2007-10-10
I've used kde-core + kubuntu-default-settings + xorg on some computers. (But not my main computer, it's just regular kubuntu-desktop.)

---

### Post by Perpetual on 2007-10-10
I haven't been able to figure out how to have say Gnome and install kubuntu-desktop without it screwing up the menus.  Meaning, gnome then has kde apps listed and kde has gnome apps listed.  other than installing kubuntu and tri-booting ubuntu, kubuntu and windows.

Is there a way around this?

---

### Post by Dr Small on 2007-10-10
> **rsambuca said:**
> Here is a [good website]("http://xwinman.org/index.php") listing many Desktop Environments and Window Managers.
+1
That is a nice list ;)
* Dr Small bookmarks it.

---

### Post by rsambuca on 2007-10-10
> **Perpetual said:**
> I haven't been able to figure out how to have say Gnome and install kubuntu-desktop without it screwing up the menus.  Meaning, gnome then has kde apps listed and kde has gnome apps listed.  other than installing kubuntu and tri-booting ubuntu, kubuntu and windows.

Is there a way around this?

I don't know about KDE, but in gnome you have to edit the menus by hand.  A total pain, yes!

---

### Post by Perpetual on 2007-10-10
> **rsambuca said:**
> I don't know about KDE, but in gnome you have to edit the menus by hand.  A total pain, yes!

Hmm, I hadn't thought about doing that.  I assumed if I deleted it from one, it would effect the other since the installation adds to both.  Might try that tonight.

---

### Post by swisscow on 2007-10-10
Have a look at this

[HTML]http://www.kde-apps.org/content/show.php/K+Menu+Gnome+(source)?content=31025[/HTML]

Gnome menu in KDE

---

### Post by Perpetual on 2007-10-10
> **swisscow said:**
> Have a look at this

[HTML]http://www.kde-apps.org/content/show.php/K+Menu+Gnome+(source)?content=31025[/HTML]

Gnome menu in KDE

Thanks!

---

### Post by Krextyl on 2007-10-10
> **Dr Small said:**
> I would too, like to find out where he got all of his DE's :p
But before I reinstalled, I had fluxbox, gnome, icewm, blackbox, amiwm, enlightenment, dwm and xfce4. I hate KDE :p

Dr Small

I thought enlightenment was a windows manager not a desktop enviroment?

---

### Post by Krextyl on 2007-10-10
> **rsambuca said:**
> Here is a [good website]("http://xwinman.org/index.php") listing many Desktop Environments and Window Managers.

thanks for the site :-)

---

### Post by bodhi.zazen on 2007-10-10
Not only can you install multiple desktops, but you can run multiple desktops at the same time :

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

This does not eat up much in terms of resources :twisted:

---

### Post by Krextyl on 2007-10-10
bodhi, nice thread - Thanks.

---

