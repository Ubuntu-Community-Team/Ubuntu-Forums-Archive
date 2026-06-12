---
title: "VEry newby Q."
date: 2005-11-23
forum: Absolute Beginner Talk
---

### Post by GlobeCoder on 2005-11-23
I am on the main command line and i want it to start to the desktop.. how do i do that.. i know im supposed to type a command of some kind but i have no idea what.

-Nico

---

### Post by Kapre on 2005-11-23
[QUOTE=GlobeCoder]I am on the main command line and i want it to start to the desktop.. how do i do that.. i know im supposed to type a command of some kind but i have no idea what.

-Nico[/QUOTE]

If you mean the GUI desktop - try typing "startx" without the quotes.

K

---

### Post by GlobeCoder on 2005-11-23
the startx wont work, it says:

-bash: startx: command not found

---

### Post by raublekick on 2005-11-23
sounds like you might have done a server install instead of a desktop install. did you just install ubuntu?

if this is the case simply type:
```
sudo apt-get install ubuntu-desktop
```
This will get your computer up to a normal Ubuntu install.

If you want to install Kubuntu as well, type:
```
sudo apt-get install kubuntu-desktop
```

And finally, you can install XFCE4 by typing:
```
sudo apt-get install xubuntu-desktop
```

You can have all three at once, and select which to use before you login by selecting the session option. I would start with ubuntu-desktop first.

I guess I should mention that you will be prompted for your password after these commands, it is your user password. And it won't look like you're typing, but you are :)


Hope this helps.

---

