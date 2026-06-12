---
title: "A Complete Install of Beryl and Emerald?"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by izizzle on 2007-07-01
I am trying to install beryl and emerald on my computer from synaptic. However, when I check  the box to mark beryl and emerald for installation, I notice that it picks up some of the other software that needs to be installed as well, but some of it synaptic leaves unchecked, like the emerald themes. Can anyone provide me with **ALL** the software I need to install from the repositories to have an **ABSOLUTELY COMPLETE** Beryl and Emerald?

---

### Post by cwood06 on 2007-07-01
```
 sudo apt-get install beryl beryl-manager emerald emerald-themes 
```

this should install it all as long as your useing nvida you should have no problems

---

### Post by ThrobbingBrain66 on 2007-07-01
```
 sudo apt-get install beryl beryl-manager beryl-plugins-unsupported emerald emerald-themes
``` will give you a fully functioning Beryl experience.  If you have a Metacity theme that you are particularly fond of, install Heliodor instead of Emerald.

---

### Post by Motoxrdude on 2007-07-01
> **ThrobbingBrain66 said:**
> ```
 suod apt-get install beryl beryl-plugins-unsupported emerald
``` will give you a fully functioning Beryl experience.  If you have a Metacity theme that you are particulalry fond of, install Heliodor instead of Emerald.

btw, its sudo, not suod ;).

---

### Post by ThrobbingBrain66 on 2007-07-01
> **Motoxrdude said:**
> btw, its sudo, not suod ;).

haha...caught and fixed.  thanks.

---

### Post by AlexenderReez on 2007-07-01
how about refer this guide....

> [http://doc.gwos.org/index.php/HowToInstallBeryl](http://doc.gwos.org/index.php/HowToInstallBeryl)

---

### Post by ThrobbingBrain66 on 2007-07-01
> **reez0105 said:**
> how about refer this guide....

That guide uses an unofficial repo that's compiled against Debian and 'unstable'.  Ubuntu is Debian based, but it's always best to use stable, official Ubuntu repos.

---

### Post by AlexenderReez on 2007-07-01
yup...i agree with that...regarding stable....but if anybody want to get all plugins that ever exists in beryl(till project stopped) ...this is the best guide...and as far as i'm using it...i got no problem at all...

---

### Post by thierce on 2007-07-02
Beryl itself isn´t really stable, is it :P
But I agree with you, unless you got ATI graphiccard it should work...
And now with Compiz Fusion it should get on even better.

---

