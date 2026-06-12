---
title: "KDE for PPC?"
date: 2005-03-27
forum: Apple PPC Users
---

### Post by dherren on 2005-03-27
I'll probably be impaled for asking this....

OK, I've tried Gnome now...don't like it. I'm not a complete idiot, but I'm definitely not a linux wiz... I come from the NeXTStep world...

How do I switch my desktop environment to KDE on ubuntu?

---

### Post by poofyhairguy on 2005-03-28
[QUOTE=dherren]I'll probably be impaled for asking this....

OK, I've tried Gnome now...don't like it. I'm not a complete idiot, but I'm definitely not a linux wiz... I come from the NeXTStep world...

How do I switch my desktop environment to KDE on ubuntu?[/QUOTE]

Well, first open up the Universe repository. Then

sudo apt-get install kde

then after it works, I would logout and change my session to KDE. Simple as pie. If you like, I would suggest doing a clean install of Kubuntu! Its much better than the Warty universe kde....

---

### Post by pvz on 2005-03-28
Indeed, try [Kubuntu](http://www.kubuntu.org.uk/) 
All the goodness from Ubuntu and KDE without all that Gnome stuff  :grin:

---

### Post by Firefishe on 2006-11-25
> **poofyhairguy said:**
> Well, first open up the Universe repository. Then

sudo apt-get install kde

then after it works, I would logout and change my session to KDE. Simple as pie. If you like, I would suggest doing a clean install of Kubuntu! Its much better than the Warty universe kde....

Is there a difference between the kubuntu cd and the Universe Repository's kde?  I thought it was all the same.

--Firefishe

---

### Post by Tipo on 2006-11-25
IIRC, downloading the source from the repository is just downloading the same files that are on the CD (maybe even newer files if there have been updates since the CD was released)

---

### Post by Firefishe on 2006-11-25
> **Tipo said:**
> IIRC, downloading the source from the repository is just downloading the same files that are on the CD (maybe even newer files if there have been updates since the CD was released)

Thanks.  I appreciate you responding to my post.  I'm also having trouble starting kde, now that I've downloaded everything.  KDE seems to have trouble writing to my home directory, essentially to the DOT files (~/.xxxxxxx).

Here's a link to a pastebin site of my most recent .xsession-errors and X Server output log from /var/log.  Perhaps you might be able to make something out of it.  Gnome is working fine.

[http://www.rafb.net/paste/results/beGgVz50.html](http://www.rafb.net/paste/results/beGgVz50.html)

Thanks in advance,
Firefishe

---

### Post by AlphaMack on 2006-11-26
I know that this thread is from prehistoric times, but for those reading this I recommend using Aptitude instead of apt-get as the former will remember all of the dependencies should you decide to uninstall KDE later on.

```
sudo aptitude install kubuntu-desktop
```

---

### Post by stream303 on 2006-11-26
> **dherren said:**
> I'll probably be impaled for asking this....

OK, I've tried Gnome now...don't like it. I'm not a complete idiot, but I'm definitely not a linux wiz... I come from the NeXTStep world...

Nobody impales here - even if you run NO gui interface you are still welcome!  For years I was quite happy with nothing but xterm and twm.  Eye-candy consisted of X-eyes. :)

If you dug the NeXTStep, be sure to check out GNUstep available in the repositories.

Take a look at the project pages at:
[http://www.gnustep.org](http://www.gnustep.org)

I've never installed gnustep (or even openstep) with Ubuntu, but it worked quite well on my freebsd boxes.

---

### Post by EuroCity on 2006-11-26
In general, the desktop environment meta-packages are:

- **ubuntu-desktop** for Ubuntu GNOME;

- **edubuntu-desktop** for Edubuntu GNOME;

- **kubuntu-desktop** for Kubuntu KDE;

- **xubuntu-desktop** for Xubuntu Xfce.

So, if one installs Ubuntu first, from the CD, then it is always possibile to include any other desktop environment by installing one or more of the meta-packages above, with Synaptic, apt-get or aptitude.

---

### Post by dpny on 2006-11-26
> **EuroCity said:**
> So, if one installs Ubuntu first, from the CD, then it is always possibile to include any other desktop environment by installing one or more of the meta-packages above, with Synaptic, apt-get or aptitude.

True. I initially used the standard Gnome installation, but installed XCFE afterwards, even going as far as to install newer XFCE than is in the Ubuntu repositories. My Gnome install is there if I ever want to go back.

---

