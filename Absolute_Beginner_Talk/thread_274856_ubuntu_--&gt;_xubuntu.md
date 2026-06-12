---
title: "ubuntu --&gt; xubuntu"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-10
Hello..
Just tried xubuntu and I gotta say it is nice. I would like to move my ubuntu to a xubuntu configuration but I would just be installing the xubuntu deb files and not really knowing what I am doing. If you change over from ubuntu, does it change the number or type of packages installed or can I be content knowing my favorite apps and games will be waiting for me when I am ready.

---

### Post by Medieval_Creations on 2006-10-10
> **saintj0n said:**
> Hello..
If you change over from ubuntu, does it change the number or type of packages installed or can I be content knowing my favorite apps and games will be waiting for me when I am ready.

It kind of depends on how you reload... the simplest way would just be to do
```
sudo apt-get install xubuntu-desktop
```
This will install xubuntu and shouldn't make any changes to your other programs.

Then when you log on just change you session from gnome to xfce & you should be all set...

---

### Post by %hMa@?b&lt;C on 2006-10-10
install it with aptitude, not apt-get that way you can uninstall if you wnat. just makes it easier because aptitude remembers dependencies.
sudo aptitude install xubuntu-desktop

---

### Post by saintj0n on 2006-10-10
The aptitude command returned an error about not being able to execute a bin file..I was su at the time so I don't understand why it wouldn't work?:confused:

---

### Post by zek725 on 2006-10-10
sudo aptitude install xubuntu-desktop ?

as easy as that? then what happens with gnome? It uninstalls? My box is a Pentium III 600MHz, I want to convert to xubuntu because I'm told it has lesser requirements, thus, will run faster in this old box of mine. :D

help... please? :D

---

### Post by PriceChild on 2006-10-10
> **zek725 said:**
> sudo aptitude install xubuntu-desktop ?

as easy as that? then what happens with gnome? It uninstalls? My box is a Pentium III 600MHz, I want to convert to xubuntu because I'm told it has lesser requirements, thus, will run faster in this old box of mine. :D

help... please? :DNope it stays there and you may enter it by choosing it in the "sessions" dialogue while logging in.

All the applications for both xfce and gnome will appear in both DEs.

---

### Post by WebSiteGuru on 2007-08-21
Cool, I think I might do that myself.


Will all the setting and software that was installed in ubuntu transcribed over toi xubuntu?

I am thinking of moving over to xubuntu, my ubuntu seem to be running kind of slow... on my PIII.

---

### Post by Zalbor on 2007-08-21
Synaptic works too, but if you want to use a terminal app aptitude is the choice (not apt-get).
Installing xubuntu-desktop will install everything you need for xubuntu.
Then if you remove ubuntu-desktop all the programs that were automatically installed for ubuntu and aren't necessary for xubuntu will be listed as auto-removable (I think so anyway).

---

### Post by WebSiteGuru on 2007-08-21
> **Zalbor said:**
> Synaptic works too, but if you want to use a terminal app aptitude is the choice (not apt-get).
Installing xubuntu-desktop will install everything you need for xubuntu.
Then if you remove ubuntu-desktop all the programs that were automatically installed for ubuntu and aren't necessary for xubuntu will be listed as auto-removable (I think so anyway).

So, all the software installed from ubuntu sympatic will be there until I remove it (if I chhose to), right?

Will it be the same as wine? Or, is t hat a different thing altogether?

---

