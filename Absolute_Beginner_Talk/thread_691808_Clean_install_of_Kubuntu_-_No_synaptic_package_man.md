---
title: "Clean install of Kubuntu - No synaptic package manager?"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by person_99 on 2008-02-09
I know this is probably a question that my dog can answer, but anyway.
In Kubuntu 6.10 Edgy Eft, I had Synaptic package manager. I am used to that package manager,  (Different computer, now is toast.)
However, on this computer, I just installed Kubuntu 7.10. I pretty much have installed Kubuntu itself and my Nvidia drivers (Which seems to favor some insane resolution to where I need a magnifying glass to see text). I was expecting to be able to install Synaptic package manager from adept, but it isn't on the list.

Can I get some help installing Synaptic Package Manager again, if that is even possible?

---

### Post by smartboyathome on 2008-02-09
You have, instead of synaptic, Adept Package Manager. Try this, and if you don't like it, install Synaptic through it.

---

### Post by ubuntu27 on 2008-02-09
It's normal for Kubuntu to not come with Synaptic package Manager.

But it is Strange that you cannot find the package with Adept

Try installing it from the terminal:

```
sudo apt-get install synaptic
```

---

### Post by smartboyathome on 2008-02-09
Ubuntu27: It isn't strange, the Kubuntu team just didn't want to include it in favor of the QT package manager Adept (Synaptic is a GTK package manager).

---

### Post by Dev'olution on 2008-02-09
Ditto.

person_99 are u using 32 or 64-bit edition. I've been hearing things similar from those using 64-bit.

---

### Post by amingv on 2008-02-09
Try:

```
sudo apt-get update
```

and then

```
sudo apt-get install synaptic
```

Should work fine...

---

### Post by person_99 on 2008-02-09
return was:
E: Package has no install candidate.

---

### Post by r4ik on 2008-02-09
I use Gnome so can't be sure anyway you could download it from here,

[http://www.nongnu.org/synaptic/index.html](http://www.nongnu.org/synaptic/index.html)

Install it and see if it works.

If you are more comfortable with a .deb file see,

[http://packages.debian.org/etch/i386/synaptic/download](http://packages.debian.org/etch/i386/synaptic/download)

Good luck !

---

### Post by hyperair on 2008-02-09
Post the contents of /etc/apt/sources.list.

---

### Post by ubuntu27 on 2008-02-09
> **smartboyathome said:**
> Ubuntu27: It isn't strange, the Kubuntu team just didn't want to include it in favor of the QT package manager Adept (Synaptic is a GTK package manager).

No, I don't find it strange that Kubuntu comes with Adept and not Synaptic. 
What I find it strange is that he cannot find synaptic using Adept. Does that mean that Kubuntu has its own repository now, and it does not include Synaptic? I doubt it.

---

### Post by hyperair on 2008-02-09
Personally I think that he messed up his sources.list. Either way we'll find out when the contents of the sources.list file is posted.

---

### Post by Reih on 2008-02-10
Kubuntu noob here.

I suffered from the same problem when I installed Kubuntu earlier today. Adept just didn't cut it when compared to Synaptic, but I couldn't seem to pull it down with apt-get.

First thing I tried was uncommenting all the entries in my source.list. No love, still didn't work.

What I had to do was comment out the first line that references the install disc as a repository. Once I did that followed by an apt-get update, I was able to access all the repositories.

Hope this helps the TC.

---

