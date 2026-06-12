---
title: "Obsolete Packages"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by G2k on 2007-02-24
I just recently installed Ubuntu and haven't installed all that much on it but have downloaded and removed many programs with synaptics for shits and giggles. Is there a way to remove obsolete files? I am coming from Gentoo and I know that cleaning the portage distfiles directory would get rid of a few gigs of unneeded space. Is there something like that on Ubuntu, be it getting rid of .deb files or something along those lines?
Thanks

---

### Post by i.am.canadian on 2007-02-24
Hi there,

I'm not sure as to a direct answer to your question, though I know the tools are available.  But what I do know is that if you use aptitude from the command line it is must better at removing unnecessary dependencies than apt-get (which, I believe, is the backend that synaptic uses).

What I do is I search synaptic for the stuff I'm looking for, type the package name(s) into the terminal using 
```
sudo aptitude install [insert package name here]
```

Then close synaptic (you can't use aptitude and synaptic at the same time) and then hit enter.  Its kind of a round about way, but its the best way I've found to keep my system clean.  I hope this helps!

Cheers.

---

### Post by christhemonkey on 2007-02-24
I think the equivalent of cleaning the portage distfiles directory would be to remove all the old archives from /var/cache/apt/archives/ or you can do this automagically like this:
```
sudo apt-get clean 
```

---

### Post by sjbrun on 2007-02-24
Open a terminal and type:
```
sudo apt-get clean
```
to delete all downloaded files from your apt-get/synaptic cache.

---

