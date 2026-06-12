---
title: "I've tried very hard ........."
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by DennisOS2 on 2008-02-11
OK.  Here is my story.   (Dell XPS 400 with an ATI Radeon graphics card)

I've installed Kubuntu three times. 

---  After install and when I've tried updating or install/updating ......... Adept Updater will not 'commit' because it says other Adept apps are running or committing changes will brake other packages.  Apps are installed, but 'commit' doesn't happen.  I've tried to KILL Adept apps,  and invoked other suggested command line commands  to no avail.  There are NO other Adept apps running.

---  When changing ATI driver resolution the screen blanks the next time I boot.  No options to recover.  So, do I have to re-install?

If open source is to be successful it needs easy and bullet-proof install/configure. from this perspective it would seem that Ubuntu is NOT ready for prime time.

---

### Post by oedha on 2008-02-11
have you turn on your software sources for updating and installing ?
for ATI...you need to do something to activate it after you install buntu
for blank screen :==> sudo dpkg-reconfigure -phigh xserver-xorg

---

