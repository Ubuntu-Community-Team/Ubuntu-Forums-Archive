---
title: "[SOLVED] Problems With ALSA. (Or maybe it's something else)"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by I0nSt0Rm on 2008-03-18
Hey everybody, I've been having problems with ALSA lately so I decided to reinstall it. I went into synaptic and searched for ALSA. Then I found all the packages that I had installed that started with "alsa" and marked them for reinstallation. I rebooted and then waited for Ubuntu to load up. It got to the screen with the Ubuntu logo and an orange bar that fills up. Just before it was finished loading, it switched over to a terminal-like screen that had a bunch of information on it and then on the line with the cursor it said "ubuntu login:" and sat there. I used ```
sudo shutdown -r now
``` and then I booted into Windows. Is the problem because I uninstalled(reinstalled) ALSA? or is there some other reason? What's wrong with my Ubuntu? Any help would be greatly appreciated! Thanks!

---

### Post by Xiong Chiamiov on 2008-03-18
Did all of the packages uninstall and reinstall successfully?  Usually for me when I don't get the graphical login it's 'cause I've screwed up my Xorg.conf.

---

### Post by tlink on 2008-03-18
There was a problem when uninstalling alsa and.... I think pulse-audio where it will uninstall your gnome desktop.  If I remember right it goes something like

sudo apt-get install ubuntu-desktop

but you might need the alsa-base installed first.  Not positive, and I'm working from memory here.  Might do a quick google search on this.

Tip: Always watch what it wants to uninstall when you choose to remove something.  Had you reinstalled gnome-desktop before the reboot everything probably would be fine.

---

### Post by Xiong Chiamiov on 2008-03-18
And, in case you are having difficulty logging in (or just forget everytime like me), when you get to the login, you type your login name, *then* your password.

---

### Post by I0nSt0Rm on 2008-03-18
Yes, all the packages reinstalled successfully. I'm fairly certain it didn't uninstall my gnome-desktop because it didn't bring up any of the confirmation boxes that says something like "these additional packages will be removed". I'll try running 
```
sudo apt-get install ubuntu-desktop
```
and see what happens.

I don't even get to the login screen. The screen goes black and then some information pops up that fills about half the screen. after all the information, there's the words "ubuntu login:" and then my cursor. If I log in I can type in commands as if it were a terminal.

---

### Post by I0nSt0Rm on 2008-03-20
Alright! it worked! Thanks so much!

---

