---
title: "Installing Wine on i386 Edgy?  It doesn't work for me."
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by chrisf79 on 2007-04-08
Greetings,

I just installed Ubuntu 6.10 for the first time (i386) and am really enjoying it.  I got my NVIDIA drivers installed, beryl, etc and it's fantastic.  Just one problem... I can't get Wine installed.

sudo apt-get install wine returns:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate


Is there a good how-to on installing wine or is there something I'm missing?  Any help would be greatly appreciated!

Thank you,

Chris Farrugia

---

### Post by rugglesworth on 2007-04-08
[Here]("http://ubuntuforums.org/showthread.php?t=149585&highlight=howto+wine")'s a pretty good wine+ubuntu howto.  I wouldn't recommend trying to install wine the way you're doing it because the wine in the repos is wayyyyy outdated, it probably wouldnt work anyway.

---

### Post by zvacet on 2007-04-08
Wine from repositories will work just fine.And for rugglesworth:how to you advice to use will in the end bring to the upgrade from repositories.That how to is good and you can learn to use wine tools but nothing else.

---

### Post by Maestro23 on 2007-04-08
Make sure you have all your repositories enabled: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

