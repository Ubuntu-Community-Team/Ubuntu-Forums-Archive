---
title: "Xubuntu or Ubuntu+xcfe"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by psweeney1967 on 2006-11-17
Hello newbie here...

I've got an older PC (Athlon-1200MHz, 384KB) and want a minimal desktop that flies.  As such I've been attracted to Xubuntu.  However, I've been curious as to whether I'll see the same performance with Ubuntu running xcfe.

I'd run Xubuntu.  But by the time I load some of the missing apps I want(OpenOffice), I think I might as well just load Ubuntu and enable xcfe.  However, I don't want to do this if I suffer realtime performance degradation.

Has anyone do this comparison?

Paul

---

### Post by taurus on 2006-11-17
Instead of using OpenOffice which will eat up a lot of your system resouces, why not use Abiword!!!  It's available in the repos so just aptitude/apt-get it...

```
sudo aptitude update
sudo aptitude install abiword
```

---

### Post by Bachstelze on 2006-11-17
Xubuntu *is* Ubuntu + XFCE. What you install with an "Ubuntu" CD is the core of the distro + the GNOME environment and what you install with a "Xubuntu" CD is exactly the same, only with XFCE instead of GNOME.

(Main reason why I still think having different names for the **same** distro is stupid.)

---

### Post by doobit on 2006-11-17
> **HymnToLife said:**
> Xubuntu *is* Ubuntu + XFCE. What you install with an "Ubuntu" CD is the core of the distro + the GNOME environment and what you install with a "Xubuntu" CD is exactly the same, only with XFCE instead of GNOME.

(Main reason why I still think having different names for the **same** distro is stupid.)

Actually, when you get the regular Ubuntu package, you get quite a few more, and heavier apps, than if you start with Xubuntu. You get the whole Open Office suite, a bunch of Gnome applets, and integrated applications, etc. If you really want it light, then start with a Xubuntu alternate install CD. If you want all the extras in Ubuntu, then start with Ubuntu or Kubuntu and then install the the XFce Xubuntu-desktop, then you will have a choice when you log in.
I've done it both ways on an older Gateway2000 with an AMD Athlon 800. I prefer the Xubuntu install, then add a few apps that I need.

---

### Post by K.Mandla on 2006-11-17
> **psweeney1967 said:**
> I've got an older PC (Athlon-1200MHz, 384KB) and want a minimal desktop that flies.  As such I've been attracted to Xubuntu.  However, I've been curious as to whether I'll see the same performance with Ubuntu running xcfe.

I'd run Xubuntu.  But by the time I load some of the missing apps I want(OpenOffice), I think I might as well just load Ubuntu and enable xcfe.  However, I don't want to do this if I suffer realtime performance degradation.

Has anyone do this comparison?
A bunch of times. If you want a sparse, lightning-fast desktop, start with Xubuntu and when you feel comfortable with it, drop down to a server installation and add xfce4. 

Then, when you're comfortable with *that*, start again with a server installation and add Openbox, Fluxbox, Blackbox or IceWM. 

Xubuntu is a huge leap in speed ahead of Ubuntu, and a server + XFCE is far speedier than Xubuntu. But if you really want to get close to the purest speed you can get out of that box, you have to try one of those four *box sisters (okay, so IceWM doesn't have *box in it ;) ).

The only problem is that they're a bit advanced. If you're comfortable with that, give it a shot.

Like Taurus said, I'd try Abiword if I were you. You get the same function as OpenOffice without all the encumbrances. And it goes along quite nicely with the lightweight idea. :)

---

### Post by psweeney1967 on 2006-11-17
I appreciate all the quick responses...

Again, my concern is, will my xfce interface be as zippy regardless of which distro I started with?  I'm worried if I have some GNOME dependecies/libs lying around that they will somehow slow my system down even if I'm running xfce.

---

### Post by Bachstelze on 2006-11-17
Well, if you don't need GNOME, then logic will tell you to not install it. If you need some GNOME apps, you can still install them with only the needed libs, not the full GNOME environment.

---

### Post by earobinson on 2006-11-17
Will the stock xubuntu cd install gnome? I didn't know it would do that, but then I have always installed ubuntu then done a ```
sudo apt-get install xubuntu-desktop
``` but then i'm not worried about performance.

---

### Post by Bachstelze on 2006-11-17
No it won't. It will install the core system, which is the same for all the 'buntus plus the XFCE desktop environment and a bunch of desktop-specific apps.

---

### Post by earobinson on 2006-11-17
> **HymnToLife said:**
> No it won't. It will install the core system, which is the same for all the 'buntus plus the XFCE desktop environment and a bunch of desktop-specific apps.
In that case the original poster should go with xubuntu instead of ubuntu

---

