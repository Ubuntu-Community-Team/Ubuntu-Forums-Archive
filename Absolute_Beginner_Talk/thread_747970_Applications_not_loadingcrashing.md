---
title: "Applications not loading/crashing"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by prodigy6630 on 2008-04-07
Hi 

I have a problems with certain applications not loading on Ubuntu7.10 (Gutsy Gibbon), such as firefox, gnome-system-monitor, Krusader and Evolution Mail to name a few.

I suspect it may be some issue with Java as it occurred soon after installing LimeWire or it could be due to   installing Krusader since I am running Gnome desktop.

I am new to Ubuntu/*nix and would like some advise as to how to go about fixing this.

Thanks for the help.

---

### Post by wormser on 2008-04-07
A good trouble shooting step with Linux is to start the program from the shell.  Try running firefox and posting the error.

Applications> Accessories> Terminal
```
firefox
```

---

### Post by prodigy6630 on 2008-04-07
That's the problem, it does not same when I launch it from terminal. 

The initial error I got was that firefix was already loaded. I tried loading it with Sudo firefox which worked for a while but then stoppped. I don't get any error now ... it just doesn't load.

---

### Post by prodigy6630 on 2008-04-07
Ok, so now I totally uninstalled Krusader and found that not to be the problem.

Then removed Firefox along with all the plugins and got Evolution working again. After that, I reinstalled Firefox and that seems to work now as well.

I then tried removing and reinstalling Gnome System Monitor and attempted to lauch it. Once again it tried to load and crashes. Then I tried loading it form terminal with 'Sudo gnome-system-monitor' and get the following error:

***gnome-system-monitor: error while loading shared libraries: libpcrecpp.so.0: cannot open shared object file: No such file or directory***

How can I get these libs back?

---

