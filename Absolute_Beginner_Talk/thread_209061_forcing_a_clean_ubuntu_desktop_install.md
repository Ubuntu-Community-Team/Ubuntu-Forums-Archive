---
title: "forcing a clean ubuntu desktop install?"
date: 2006-07-04
forum: Absolute Beginner Talk
---

### Post by Bob Walsh on 2006-07-04
Newbie screwed up! installed u-server, should have installed u-desktop. Tried to install u-desktop from live CD - fails.

1. How do I remove ubuntu from the hard disk using the live CD? or,
2. How do I do I force a clean install of ubuntu desktop?

---

### Post by bonzodog on 2006-07-04
does the u-server set-up boot from hard disk?
I would assume it does, in which case, you simply login using your username and password in the console (sorry, yes, you will have to live with it for a very short while...). Then, at the command prompt, simply type;
```
sudo apt-get install ubuntu-desktop
```

It will ask for your password, which you just type in - remember, the password is not visible in ANY way when you type it in. 
It will then proceed to download and install the dekstop env with gnome. It is interesting to note that you have inadvertantly given yourself the choice of one of 3 desktop envs from clean install. change 'ubuntu-desktop' to 'xubuntu-desktop' and you will get the xfce desktop env, or 'kubuntu-desktop' will give you the KDE env.

---

