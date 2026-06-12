---
title: "Switching screens getting slower"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by drewcoon on 2008-03-30
Hi, recently I've been noticing that between screen while booting up, there are longer breaks between screens.

I have my computer set up dual boot XP and Ubuntu, and I've never had problems with this before, but recently i've noticed that before the grub screen displays after startup, there is a black period long enough to make my monitor display "no signal input". this repeats between the grub and ubuntu loading screen, between the loading screen and the login screen, and between the login screen and the desktop loading.

This also occurs when fullscreen games and programs are started. What is causing this?

I can't think of any changed that I've made, besides experimenting with xcompmgr for it's shadow effects (later removed it because of bugginess), and I got xfce-desktop off the package manager because I was curious to see what XFCE is like. I'm pretty sure this problem didn't start directly after downloading either of these packages, so I don't think they're related.

It's not something that stopping my computer from working, it's just something that bugs me... Can anyone here figure out what's making this happen?

---

### Post by smurphy_it on 2008-03-30
Take a look at your system logs.  It will state a number on the left hand side in milliseconds I believe.

If you notice long gaps that might help in determining your problem.

Alternately, you can jump into a terminal and type dmesg > dmesg.log then post the contents of that file here.

---

### Post by drewcoon on 2008-03-30
EDIT - Nevermind it's not doing it today for some reason :confused:

Oh well, problem solved I guess. Thanks anyways :)

---

### Post by smurphy_it on 2008-03-31
Then could you mark this thread as solved :-)

---

