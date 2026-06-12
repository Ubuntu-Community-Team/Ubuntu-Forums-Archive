---
title: "[SOLVED] Package Manager won't work"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by yersi on 2007-07-27
I installed Ubuntu yesterday and I've liked it a lot so far. My only problem was that desktop effects wouldn't work, I'm on an Acer Laptop with an ATI Radeon Xpress200M card so beryl et al aren't easy to get running. 

This sent me into a world of guides on how to run an XGL session under Gnome, Beryl versions, eventually I moved along too fast and in the process probably edited a whole lot of things I shouldn't have. Among the things I have done (links to relevant articles embedded):

- installed beryl via apt-get but removed the existing beryl packages manually via Synaptic Package Manager to make room for the old version
- run dpkg-configure xserver-xorg, screwing up my display in the process. I managed to revert my settings by renaming a backup of xorg.conf. 
- followed the advice in [this article](http://obtown.com/2007/06/15/how-to-beryl-on-ubuntu-feisty-with-ati/)
- followed a [thread](http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m) on this forum which was very similar to the link above
- Another guide I followed was [this](http://spellbook.infinitiv.it/2007/01/28/daniel-robitaille-playing-with-compizdesktop-effects-in-feisty.htm), but I didn't follow his first suggestion.

Now when I try to update via the package manager, I get the following error message:

```
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Invalid record in the preferences file, no Package header'
```

I did a search for the error message and found a Spanish site which unfortunately didn't help due to me not understanding much Spanish. Whoever had the error message had obviously been following the same guide as me to get his laptop working with desktop effects. 

Can anyone help me out with this? The system is fully functional otherwise and I don't want to reinstall if it is not absolutely necessary!

---

### Post by Mornedhel on 2007-07-27
If no one else has any input on this, I can translate the relevant parts of your Spanish link, if you still have it.

---

### Post by yersi on 2007-07-27
[http://elnorber.wordpress.com/2007/04/05/beryl-settings-mi-configuracion/](http://elnorber.wordpress.com/2007/04/05/beryl-settings-mi-configuracion/)

That's the link. CP the error message and you'll find the post I. For all I know, the site could be completely unrelated to my problem, so don't waste your time if you're short on it.

---

### Post by Mornedhel on 2007-07-27
OK.

Could you cat /etc/apt/preferences ?

Mine looks like this :

Package: *
Pin: release o=lupine
Pin-Priority: 1000


The guide does mention this at one point, doesn't it ? (Or something like it.)

---

### Post by yersi on 2007-07-27
It does.

I used my head and the only thing I needed to do was to remove the preferences file via the terminal. Thanks for your help though.

---

