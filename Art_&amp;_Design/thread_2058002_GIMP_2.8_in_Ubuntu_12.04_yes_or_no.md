---
title: "GIMP 2.8 in Ubuntu 12.04: yes or no?"
date: 2012-09-14
forum: Art &amp; Design
---

### Post by Jenske on 2012-09-14
In 12.04 Gimp has version 2.6. I however want to install 2.8. As I understand this necessitates the installation via a PPA.
However, on many forum threads, I read warnings not to install programs lightly using ppa's.

So, what should I do? Install Gimp 


(I'm not sure whether this post belongs on this forum, but as there's no "software" forum, I think this is the best place.)

---

### Post by cbanakis on 2012-09-14
I'm not sure if 2.8 holds any improvements that you want, but I think you can trust their ppa.

The only reason why caution is advised with external ppa's, is because any Joe Blow can make and post a ppa that can contain harmful software.

The designers of Gimp are not some random hoods, and 2.8 will eventually be in the software center.

Adding the ppa just gives you a head start, because Canonical still has yet to evaluate and add the newer version to the software center.

This is usually the case will most major software developers.  (Libre Office for example.)

Thats my opinion anyway.

---

### Post by dniMretsaM on 2012-09-14
I have GIMP 2.8.2 installed from [this PPA](https://launchpad.net/~otto-kesselgulasch/+archive/gimp) with no issues. I say go for it.

---

### Post by heminder on 2012-09-14
As mentioned and as is my own opinion, PPA's should only be used when absolutely necessary, and with caution. 

If you want the latest version in a hurry another option is to get the source tarball directly from GIMP's website and compile and install it yourself. Complilation takes a little while for it to finish but it's not really that difficult, especially if you've done it before. You just say "go" and wait until it's done.

---

### Post by dniMretsaM on 2012-09-14
> **heminder said:**
> As mentioned and as is my own opinion, PPA's should only be used when absolutely necessary, and with caution. 

If you want the latest version in a hurry another option is to get the source tarball directly from GIMP's website and compile and install it yourself. Complilation takes a little while for it to finish but it's not really that difficult, especially if you've done it before. You just say "go" and wait until it's done.

Compiling GIMP 2.8 is a royal pain in the butt (take it from someone who tried before a PPA was available).

---

### Post by heminder on 2012-09-14
> **dniMretsaM said:**
> Compiling GIMP 2.8 is a royal pain in the butt (take it from someone who tried before a PPA was available).
Really? I compiled GIMP 2.8 on Lucid, which needed me to fetch all the new depenencies too. Getting the dependencies was a little annoying but it wasn't that bad.

---

### Post by dniMretsaM on 2012-09-14
> **heminder said:**
> Really? I compiled GIMP 2.8 on Lucid, which needed me to fetch all the new depenencies too. Getting the dependencies was a little annoying but it wasn't that bad.

I had a lot of dependency issues on 11.10/12.04. Never did figure it out, so it may have been something really simple. Either way, I'd still recommend the PPA, but that's just my personal preference.

---

### Post by osarusan on 2012-09-16
Go ahead and use that PPA. I've been using it since 2.8 came out with no issues at all.

GIMP 2.8 is much better than 2.6, hands down.

---

### Post by jrog on 2012-09-16
You definitely *should *be cautious about using PPAs, but, as others have said, that is generally because every PPA added is an additional source of possible bugs/security issues, particularly if the PPA is managed by a "Joe Blow" who isn't that skilled at keeping things neat and up-to-date. Typically, for major and widely-used pieces of software, the PPAs are more reputable. The GIMP 2.8 PPA is likely to be fine.

I would go ahead and use it if only for the single-window mode available in GIMP 2.8, assuming that you're using the Unity desktop. The single-window mode works much more nicely with Unity.

---

### Post by vexorian on 2012-09-16
It is good to be wary about PPAs, just double check that the PPA you are installing is legit and that there are no major bugs in the packaged version (the version of the PPA is stable and not a cutting edge, test one).

In the case of the 2.8 PPA, it works well and GIMP is so much nicer now.

---

### Post by NNJRob on 2012-09-20
> **vexorian said:**
> It is good to be wary about PPAs, just double check that the PPA you are installing is legit and that there are no major bugs in the packaged version (the version of the PPA is stable and not a cutting edge, test one).

**In the case of the 2.8 PPA, it works well and GIMP is so much nicer now**.


I agree with this!

---

### Post by ofnuts on 2012-09-20
> **heminder said:**
> Really? I compiled GIMP 2.8 on Lucid, which needed me to fetch all the new depenencies too. Getting the dependencies was a little annoying but it wasn't that bad.I'm on Lucid and compiled the early 2.7 but after that the dependencies started getting hard to manage (beyond Gegl/Babl). IIRC you need at least a recent Glib, but it's not clear if I can run that Glib specifically for Gimp (nor where can I get it). Would you have any recommendations?

---

### Post by contributor on 2012-09-22
> **osarusan said:**
> Go ahead and use that PPA. I've been using it since 2.8 came out with no issues at all.

GIMP 2.8 is much better than 2.6, hands down.

Agree. I will also recommend to use PPA. Good Luck.

---

