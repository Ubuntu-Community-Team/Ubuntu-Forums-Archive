---
title: "Versioning for .deb packages"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by Ruskie on 2005-12-15
Hello,

I've got a question on how Ubuntu treat debian packages. I've almost always installed them through Synaptic so maybe I'm asking stupid question, but I don't know which format Synaptic uses.
The question is: since dosemu 1.2.1 currently in Ubuntu doesn't work (crashes stright away) and there isn't a newer version in Ubuntu repositories, I've been given 1.2.2 deb packages for dosemu, freedos-dosemu and xfonts-dosemu, and they told me to install it with dpkg -i.

I know it's easy to do but... what happens to Synaptic: will it be able to "see" the new version installed? And most important: will it be able to recognize it needs update when a new version (say 1.2.3) comes out in Ubuntu repositories?
Or should I monitor it on my own?

Thanks
Marco

---

### Post by ChrisC on 2005-12-18
It seems that lots of people are complaining about dosemu crashing.

Bumping up so maybe we'll get an answer to the questions above about system behavior if you do a manual install of a deb ...

---

### Post by endersshadow on 2005-12-18
Yes, it will be able to see and recognize when a new version comes out.  Make sure your .deb is built for Ubuntu, and not for Debian.  While Debian and Ubuntu share the same package management systems, the two are compiled slightly differently sometimes.

Otherwise, yes, Synaptic will see it and update accordingly.

---

### Post by Ruskie on 2005-12-18
Well, it ran, however I only got to make it work text-mode (hung with graphics); though, I admit, I didn't take the time to play a little with the settings.
Still I doubt it was compiled for Ubuntu, really... There's room for a backport request, perhaps...

---

### Post by endersshadow on 2005-12-18
You can do it yourself if you have the source for it.  Just run this:

```
sudo apt-get install build-essential checkinstall
cd
wget 'http://easynews.dl.sourceforge.net/sourceforge/dosemu/dosemu-1.3.2.tgz'
tar xzf dosemu-1.3.2.tgz
cd dosemu-1.3.2
./configure
make
sudo checkinstall -D make install
```

Say y to creating docs, let it run, and then it'll ask you if the info is right.  Make sure that the name is dosemu and not dosemu-1.3.2.  It'll build and install the deb file for you.

Oh, and don't forget to sudo -k afterwards.  Then, you should be all set.

---

### Post by Ruskie on 2005-12-19
[QUOTE=endersshadow]You can do it yourself if you have the source for it.  Just run this:

[code]sudo apt-get install build-essential checkinstall
cd
...
[/QUOTE]

If I do that, I compile & install from the source code, isn't it? In that case, the dkgp wouldn't show the package as installed, and would not be able to upgrade it, isn't it?

Thanks
Marco

---

