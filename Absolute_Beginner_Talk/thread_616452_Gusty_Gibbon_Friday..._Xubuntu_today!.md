---
title: "Gusty Gibbon Friday... Xubuntu today!"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Warren in Japan on 2007-11-18
Hi there,

I last used my computer on Friday and all was well.  Tonight (Sunday) I logged on and there was only the Firefox button, and a "?" button which, when pressed, said ":Welcome to** XU**bunbtu"!  I downloaded the Gutsy Gibbon upgrade a few weeks ago so this was a BIG surprise.  There are no applications visible and all my data is gone (I backed up though).  The log off panel is of a different design too.  The only thing I can think of is the abortive switch to xubuntu I did three weeks prior to the October upgrade has some bearing on this dramatic event.  I am a newbie to ubuntu and I like it and want to get to know how to use it well so any pointers to help me figure out the issue will be greatly appreciated.

---

### Post by FurryNemesis on 2007-11-18
Sounds like your xubuntu session is still around. Did you uninstall xubuntu-desktop after the abortive move? Also, I think your default session has changed. At the login window, try changing to your preferred session and log in to that. Then go to system>preferences > session and set up whatever you want as the default.

---

### Post by puterboy on 2007-11-18
Do you have access to Synaptic Package Manager? You could try removing Xubuntu desktop. if you don't have access to the package manager, try "sudo apt-get remove xubuntu-desktop", and then, for good measure, try "sudo apt-get install ubuntu-desktop". You're trying to remove the desktop, then reinstall the gnome desktop.

---

### Post by Warren in Japan on 2007-11-18
Thanks for that.  Sounds logical.  I am greatful.

---

### Post by Warren in Japan on 2007-11-18
Cheers, yes I think xubuntu is lurking there.  Best wishes.

---

### Post by Warren in Japan on 2007-11-24
> **FurryNemesis said:**
> I think your default session has changed. At the login window, try changing to your preferred session and log in to that. Then go to system>preferences > session and set up whatever you want as the default.

Hi there,

That was indeed the problem.

I would like to say to both the people who answered my question **"thank you for answering this post!"**

---

