---
title: "[SOLVED] Installing Ubuntu Desktop"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by rh10023 on 2008-01-05
I have installed the packages on my 6.06 LTS Server, but I am unable to figure out how to get the Ubuntu logon screen.  My past experience with Fedora was that I changed the inittab file to make this happen, but this does not seem to work.  Can someone give me a quick answer?

---

### Post by lgambett on 2008-01-05
What packages do you have installed to obtain Ubuntu desktop ?
The system you used in Fedora (setting runlevel at 5 instead of 3) is not working in Debian / Ubuntu, that always work at runlevel 2.
I suppose you have already tried startx....

---

### Post by aktiwers on 2008-01-05
```
sudo apt-get install ubuntu-desktop 
```
```
startx
```

---

### Post by rh10023 on 2008-01-05
Here is the command that I used to install.

aptitude install ubuntu-desktop

So I should not need to change the inittab file to get the ubuntu-desktop logon screen?

---

### Post by aktiwers on 2008-01-05
Aptitude is fine too.
And nope, startx will do.

But now you are already logged in, so it will start x without the login screen. Next time you boot though, the login screen should be there

---

### Post by Martje_001 on 2008-01-05
> **aktiwers said:**
> Aptitude is fine too.
And nope, startx will do.

But now you are already logged in, so it will start x without the login screen. Next time you boot though, the login screen should be there
Or go to 'Services' in the Administration menu and enable 'gdm'.

---

### Post by rh10023 on 2008-01-05
> **lgambett said:**
> What packages do you have installed to obtain Ubuntu desktop ?
The system you used in Fedora (setting runlevel at 5 instead of 3) is not working in Debian / Ubuntu, that always work at runlevel 2.
I suppose you have already tried startx....

Decided to re-run the install of ubuntu desktop.  Some reason it quit too early.  Now everything is working  as expected.  Thanks.

---

### Post by SOULRiDER on 2008-01-05
Thats good to know.
Remember, **aptitude** is better than **apt-get** for for some reason people use it less =/

Could you please markt he thread as solved? You can do that from the Thread Tools Menu.

---

### Post by jaz.spb on 2008-01-05
not always aptitude is better than apt-get. For example in Arch in kde I have typed "aptitude install gnome". It deleted all network configs and managers, openoffice.org and some other packages, then it installed gnome, but deleted packages didn't come back. I don't no why it happened. May be it happens only in Arch. It is very unpleasant trouble. In xubuntu I never met this problem. May be anyone knows what is it?

---

