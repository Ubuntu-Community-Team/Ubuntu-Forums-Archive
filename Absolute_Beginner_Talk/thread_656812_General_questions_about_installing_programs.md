---
title: "General questions about installing programs"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Djalmahal on 2008-01-02
HI,

i just changed from Windows XP to Ubuntu, i got around fairly well in Windows but now I'm starting to find my way around Ubuntu, though slowly at first. So today I installed VLC Media Player (easy), Google Earth ( a bit more tricky). It's great to have this forum to look for anwers, feels good to be part of the the Ubuntu-Community. So now I did get to Skype and i thought it didn't install , till Synaptic told me that it was installed. But i can find it nowwhere, it is on the hardrive at  /usr/share/doc/skype, but i can't find an executable file there, nor does it show up in the Applications Menu. 

I'm sure the answer is relativly easy but for now i am stuck

Thanks
Andreas

---

### Post by p_quarles on 2008-01-02
What's the output of this?:
```
ls /usr/bin | grep skype
```

---

### Post by ~LoKe on 2008-01-02
Typing "skype" in the terminal without the quotation marks should bring it up.  Does it?  If not, it's not installed.  The path you listed is for the manual entries (documentation).  If it's not installed, try this:

**EDIT**: This is for 7.10 Gutsy Gibbon.  If you're not using Gutsy Gibbon, don't follow the following steps, and tell me which version you're using.

```
gksu gedit /etc/apt/sources.list
```
Add this to the end of the file:
> ## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
Save and close the file.  Now, in the terminal:
```
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```
```
sudo apt-get update && sudo apt-get upgrade
```
After that...
```
sudo apt-get install skype
```

---

### Post by PeterJS on 2008-01-02
In windows programs files are grouped by what program they're installed with, where in linux files are grouped by function. So the skype documentation is in /usr/share/doc/skype, but the program it self is in /usr/bin with the rest of programs on the system. The attached diagram gives a good idea what's where. The locate program is good for finding things in the system from the command line try:
```

locate skype | grep bin

```
The grep bin on the end tells it to ignore everything that doesn't have bin somewhere in the path. This is useful because you can safely assume than any program you'd want to run is in a bin folder somewhere, (/bin, /usr/bin, etc).

---

### Post by melopsittacus on 2008-01-03
Hello! I have another general question about software installation: what is the relationship between apt-get, Synaptic package manager and Apllications->add-remove software?

So far, I guess that apt-get and Synaptic use the same sources, but Synaptic has a graphical interface. And I think the the Add-remove software command manages a subset of the programs in Synaptic. Is this right?

---

### Post by hyper_ch on 2008-01-03
Applications-->add-remove software is the same as synaptic.
On KDE you normally have Adept installed that does this.

In the terminal you have aptitude and apt-get to download files from the repositories and install them.

The all basically use the same backend. Synaptic and Adpet are just GUI tools while apt-get and aptitude work from the command line.

---

### Post by billandteresa on 2008-01-03
> **Djalmahal said:**
> HI,

i just changed from Windows XP to Ubuntu, i got around fairly well in Windows but now I'm starting to find my way around Ubuntu, though slowly at first. So today I installed VLC Media Player (easy), Google Earth ( a bit more tricky). It's great to have this forum to look for anwers, feels good to be part of the the Ubuntu-Community. So now I did get to Skype and i thought it didn't install , till Synaptic told me that it was installed. But i can find it nowwhere, it is on the hardrive at  /usr/share/doc/skype, but i can't find an executable file there, nor does it show up in the Applications Menu. 

I'm sure the answer is relativly easy but for now i am stuck

Thanks
Andreas

Hello just thought i'd ask you if you if you right clicked on the menu screen and clicked edit....:)

---

### Post by melopsittacus on 2008-01-11
Hi! I have a strange issue when installing applications today: whichever package I try to install it warns me that it is not authenticated, whereas I did not use to get this warning before. Where should I start to look for, if I want to fix this problem?

---

