---
title: "wine changing to winxp version from win2000"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by findik1 on 2007-09-21
Hi

I need to install a software with xp version but I installed wine with win2000 default(I remember when I first installed wine, it asked me which operation system to choose and win2000 was default). Now I wanted to install and xp version of a software(this default version of wine cannot install the software, and I think it is because I chose win2000 as default), not win2000 version. I uninstalled wine and reinstalled  to set winXP as default but apperantly it remembers pre version (win2000), since it did not ask me anything abouth chooseing the version (whether XP or 2000). 

Any suggestions?
Thank you
findik

---

### Post by mysticmatrix on 2007-09-21
Reinstalling doesn't removes default settings. They are stored under /home/<username>/.wine.

BTW, you can change Wine version as well as many other options by typing this in terminal```


winecfg
```

---

### Post by asmoore82 on 2007-09-21
::This goes for almost all software on GNU/Linux systems::

Linux is a multi-user system so settings have to be stored on a per user basis.
This is done by creating hidden "dotfiles" in your home directory. These files begin
with a single dot(.) to make them hidden and are usually named after the program
that makes and uses them.
Typically, a large scale application will want a whole folder to save hidden stuff in
so it will create a directory in your home folder. Removing software via package
managers never removes these "dotfiles" with your settings; this is not a bug,

This setup causes several convenient side-effects:
1. You may setup your preferences the way you like them and then remove the application,
but should you want to use the application and re-install it again in the future, your
preferences are still there.
2. If you backup your entire home folder; your preferences for 100's of applications
can even follow you across multiple distros.
3. [and most importantly] you never have to uninstall/re-install user-space applications
because of botched preferences; you can just "nuke"[delete] the dotfiles of that application;
preferably when the app is not running of course.

Long story short(!!warning!! this will remove all data on your virtual "C:" drive):
```
~$ rm -rf ~/.wine
```

---

### Post by findik1 on 2007-09-21
I did your suggestions, but still not working for some reason that I dont understand

---

### Post by James7 on 2007-09-21
I don't know if this will help, but have you tried going by the regular menus?

System --> Preferences --> Wine Configuration

and then down at the bottom of the tab that automatically opens you can select which Windows to report to your programs ?

---

