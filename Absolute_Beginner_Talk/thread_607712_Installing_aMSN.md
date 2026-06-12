---
title: "Installing aMSN"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by kenflyken on 2007-11-09
I just installed Ubuntu 7.1 (Gusty) an hour ago.  I have used Windows all my life and have no idea about how to install stuff on Linux.

So...after I downloaded the aMSN (Ubuntu package) from their website, when I try installing, it shows:
[COLOR="Red"]Error: Dependency is not satisfiable: tcl8.4[/COLOR]

So...I tried finding tcl8.4...and I found it from
[https://launchpad.net/ubuntu/gutsy/+source/tcl8.4/8.4.15-1build1](https://launchpad.net/ubuntu/gutsy/+source/tcl8.4/8.4.15-1build1)
...but I don't know how to install it...

And so...I tried searching the forums and found out that aMSN can be installed through Synaptics.  But when I try searching for aMSN in Synaptics, there are no results.

Please don't just say go get another IM program, cuz I've tried GAIM and KMess on my friend's PC and I just don't like it.

Thank you so much!!!

Ubuntu has been great so far...except for installing things T T

---

### Post by mcduck on 2007-11-09
Go to System/Administration/Software sources (or whatever it was called), make sure that you have both Universe and Multiverse repositories enabled, and then search in Synaptic again.

---

### Post by amingv on 2007-11-09
Hi,

aMSN can be installed through synaptic. (Or at least could when I installed it) Assuming you have a new installation maybe this can help; type this in a console:

```
sudo apt-get update
```

And search for it again on your favorite package manager. It should come up.

Also, [this guide]("http://monkeyblog.org/ubuntu/installing/") helped me beat my installing paranoia, maybe it can help you too.

---

### Post by Shinbu-Otaku on 2007-11-09
if i remember rightly, go to 'Add/Remove Programs' at the bottom of the main menu, change the option on the top right to 'all available software' and search for aMSN. Just tick the box next to it, click apply, and let ubuntu do the rest. that should install it without a problem.

---

