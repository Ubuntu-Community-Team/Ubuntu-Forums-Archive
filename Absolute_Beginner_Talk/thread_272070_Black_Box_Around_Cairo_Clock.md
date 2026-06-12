---
title: "Black Box Around Cairo Clock?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Sheepish on 2006-10-05
hi i was just wondering how to get rid of the black box around the cairo clock, im using ubuntu, gnome. any ideas? thankyou.

---

### Post by phido on 2006-10-05
AFAIK you need to run xgl/aiglx to get ride of it.
The other solution is a black background..

---

### Post by jstueve on 2006-10-05
or run xcompmgr...  (in edgy, aiglx is default (cmiiw) but metacity's composite manager isn't enabled, xcompmgr will make the cairo apps work without the back borders)

---

### Post by Kivech on 2007-02-02
Color me blind (I'm really new to Ubuntu and the Linux world) but I have Ubuntu Edgy Eft running, got the clock installed and the black background as well.

However, I have no clue how to run those apps you guys are talking about. In a root terminal I don't get any of them showing up. All packages are installed (I verified this in the package manager).

So I'm completely clueless on how to do what you guys suggested for a solution. Would someone be so kind to give me some "Linux for Dummies" type of instructions? I really like this clock and it would be a shame if I ended up not using it just because I cannot figure out how to fix it, at least not with some more newbie-friendly instructions.

Thanks,

Kivech

---

### Post by paddax on 2008-03-02
I've just hit the same problem and thought I'd elaborate the the previous post, firstly you need to install xcompmgr, this is accomplished from the terminal with the following.  You can use Synaptic if you want.

sudo apt-get install xcompmgr

This will install the sample compositing manager, you can then run xcompmgr from a terminal by simple typing 

xcompmgr &

This will run the compositor for the current session you should really Install xcompmgr as a service but I'll leave for someone else to answer (cop out sorry).

---

