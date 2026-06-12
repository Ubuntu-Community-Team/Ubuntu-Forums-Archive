---
title: "Compiz updates"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by dgbearcat on 2008-03-08
I read on Digg about compiz updates, but I guess that since it's sort of a "beta" release, Synaptic isn't picking it up to install. 

How do I grab those, then? I tried downloading the tar.gz, but I'm not sure how to install that or put things where they need to go.

---

### Post by JoshuaRL on 2008-03-08
Well, all of Compiz is kind of in perpetual beta.  What is the page on Digg, and what exactly are you trying to get?

---

### Post by dgbearcat on 2008-03-08
[http://lists.compiz-fusion.org/pipermail/community/2008-March/000168.html](http://lists.compiz-fusion.org/pipermail/community/2008-March/000168.html)

I meant to include that, but somehow forgot. 

I don't need the Atlantis, but the main and extra (particularly the 3d windows and sessions manager) plugins look wonderful.

---

### Post by glennric on 2008-03-08
The extra and main plugins are in the repositories.  The package names are
compiz-fusion-plugins-extra and compiz-fusion-plugins-main.
The 0.6.0 version of compiz and those plugins are in the gutsy-backports repository.  The older 0.5.2 versions are in the main gutsy repositories.

---

### Post by dgbearcat on 2008-03-08
Ok, so, er...how do I get those, then? Is it an apt-get command?

---

### Post by glennric on 2008-03-08
Yes.  Assuming you have the repositories enables, type
```
sudo apt-get install compiz-fusion-plugins-main compiz-fusion-plugins-extra
```
Any package can be installed this way.  Although you can also open Synaptic and look for the packages there.  This may be easier for you.

---

### Post by dgbearcat on 2008-03-08
It told me there was nothing new to install, but I didn't update them previously. Are they stored somewhere else because they're not full release versions?


Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-fusion-plugins-main is already the newest version.
compiz-fusion-plugins-extra is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a libartsc0 guile-1.8 lilypond-data texlive-base
  texlive texlive-fonts-recommended kdelibs-data texlive-common liblualib50
  texlive-base-bin guile-1.8-libs tetex-bin libgmp3c2 libcurl3 libavahi-qt3-1
  texlive-latex-recommended texlive-latex-base libraptor1 liblua50
  texlive-doc-base tex-common texinfo
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by glennric on 2008-03-08
The packages are installed.  I thought they might be as they are installed by default in gutsy.  Install the package "compizconfig-settings-manager" to change the plugins and settings for compiz.  Then you can add the plugins and effects that you may have seen elsewhere.

---

### Post by glennric on 2008-03-08
By the way, after installing that package go to System->Preferences->Advanced Desktop Effects Settings to change the settings for compiz.

---

### Post by dgbearcat on 2008-03-08
Er....I've had compiz installed. I know how to do that, that's easy.

I'm trying to get the most recently updated version that was released today that has 3dwindows and such. It doesn't seem to be included in the normal repository version, so I assume it is somewhere else.

---

### Post by glennric on 2008-03-08
No the 3dwindows plugin is not in the repository version.  I have debs compiled from the git source if you want them.  I can email them to you if you like.  They are to big to post on the forums.

---

