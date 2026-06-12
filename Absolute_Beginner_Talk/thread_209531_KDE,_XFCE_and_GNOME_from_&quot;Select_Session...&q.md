---
title: "KDE, XFCE and GNOME from &quot;Select Session...&quot; on the splash screen."
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by SonicChao on 2006-07-05
Hi, I want to be able to boot into XFCE, Gnome or KDE from "Select Session..." on the splash boot-up screen. I tried this once with the followinf commands:

> 
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop


I thought that would work, until my splash screen changed and I got help from a support IRC channel (I accidently put a space before a command) and I had to reinstall Ubuntu because there was a Kernel Panic.

That being said, now that I have it reinstalled, how do I install KDE and XFCE as choices in "Select Sessions...."?

---

### Post by Jucato on 2006-07-05
the same way you did.
```

sudo aptitude install update
sudo aptitude isntall kubuntu-desktop
sudo aptitude install xubuntu-desktop

```

Btw, you choose KDE, Xfce, or GNOME from the *login screen*, after which you see the splash screen (some animated text/icons/mouse).
Each Desktop Environment (meaning KDE, Xfce, and GNOME) uses it's own splash screen, so they will really all be different. Unless you can find a common splash screen theme that all of them can use.

---

### Post by SonicChao on 2006-07-05
I mean, I want to keep the Ubuntu screen...the brown one, and I want to keep the screen where you log into Ubuntu to start with, the defualt.

Thanks,
SC

---

### Post by Jucato on 2006-07-05
oh, what you meant was that you want to keep the Ubuntu login sreen (where you enter your user name and password) as the default?

During the installation process (after everything has been dowloaded), you will be asked whether you want KDM to be the default display (login) manager, or keep GDM. Answer that you want to keep GDM as the default. So you will still have your brown Ubuntu/GNOME login screen, but still have the option to choose which desktop environment to run.

---

### Post by SonicChao on 2006-07-05
Ok, I did that, but the problem I had last time is that when I did:

```

sudo apt-get install xubuntu-desktop

```

it shows the Xubuntu Splash Screen, and the Xubuntu Login Screen. So that's why I'm nervous to try "xubuntu-desktop" again.

~SC

---

### Post by Jucato on 2006-07-05
AFAIK, Xfce (Xubuntu) and GNOME (Ubuntu) both use GDM as the login screen. The only difference is the themes, so you can switch back to using the brown GNOME theme by going to System > Administration > Login Window then choosing the Human theme. 

As for the splash screens, KDE will use it's own splash screen, GNOME will use its own splash screen, and Xfce will use its own splash screen. So they will all be different, unless you can find a splash screen that has KDE, GNOME, and Xfce versions.

---

### Post by SonicChao on 2006-07-06
Ok, I think I screwed it up. I did:

```

sudo apt-get install kubuntu-desktop

```

Is "aptitude" different from "apt-get install"? Because when I did an **apt-get install** it gave me a Kubuntu desktop.

What I mean by Splash Screen, I mean the beginning boot-up screen, that, looks roughly looks like this:

                                        (symbol thingy) kubuntu

Loading drivers...                                                                     ok
Blah....                                                                                     ok
Blah....                                                                                      ok

Does that let you know what i mean?

---

### Post by shoot2kill on 2006-07-06
yes i know what u meen... but when i installed xubuntu, it didnt change that at all...

aptitude is a bit different from apt-get, but i do not have the link for the details... someone else will post...

i would try the xubuntu-desktop and see what u get

---

### Post by aysiu on 2006-07-06
If one of the desktop environments takes over, you can change it back:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

The difference between apt-get and aptitude:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by shoot2kill on 2006-07-06
thanks aysiu... i know i could rely on you for the links.. :)

---

### Post by SonicChao on 2006-07-06
Thanks aysiu! That solved my problem perfectly. :-D

---

### Post by linuxluver on 2008-01-07
Alright, my browser says that that link to the site about the splash screen is trying to redirect me in a way that will never complete! Somebody give me another website please!
P.S. If you could help me, I'm running Edubuntu 7.10 (as you can see) with KDE, Xfce, and GNOME and I want it to go back to the default Edubuntu Splash.

---

