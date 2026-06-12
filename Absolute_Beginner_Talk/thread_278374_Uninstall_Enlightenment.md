---
title: "Uninstall Enlightenment"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by Hairyred on 2006-10-16
I've been messing with enlightenment, but I don't like it. I tried removing it with Synaptic, but that was not a success. How do I uninstall Enlightenment? I have searched, but find nothing.
Ubuntu 6.06, installed enlightenment with synaptic.

---

### Post by brt on 2006-10-16
i assume that you have deinstalled enlightenment, and its still running, so fire up a terminal and type:

killall enlightenment && metacity --replace&

this should quit enlightenment and start metacity, which is gnome's default windowmanager.

---

### Post by Hairyred on 2006-10-16
I forgot to say, I re-installed E so that I could get into Ubuntu! E changes some files, would it be presession? and when I remove E via Synaptic my pc throws a wobbly and refuses to run because it can't find E. I am a beginner and have stuffed up! I couldn't find anything about uninstallation on the (confusing) E website. Any ideas?
I can't find where to start a terminal in E, when I tried I got an error, wrong p.w. (it's not!)

---

