---
title: "Kde Apps in Gnome?"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by bluevoodoo1 on 2006-01-19
Is it safe to install KDE while still keeping Gnome? I want to use Rosegarden (music software) but it requires KDE. From Gnome do I simply do...

sudo apt-get install kde 
or is it... 
sudo apt-get install kubuntu-desktop  

?? one of those? 

I'm assuming I can't use both at the same time, but can I log in to ether at startup correct?

Do I need another partition? Will /home be safe? (it's on its own partition)

I'm most afraid of breaking my Gnome system, but I'd like to mess around with Rosegarden and KDE for that matter. 

I've already read about saving the packages it installs to a text file for easy removal later, but there doesn't seem to be a definitive "Get KDE without breaking your Gnome" thread. Any tips??

---

### Post by tim15856 on 2006-01-19
"sudo apt-get install kde" installs only KDE.

"sudo apt-get install kubuntu-desktop" installs KDE and all the default KDE programs. 

Are you sure Rosegarden requires KDE? It may be a KDE program but still work fine in Gnome. I run several KDE programs in Gnome. If you install the kubuntu desktop, when you login, you'll be given a choice of which desktop you want to load. Installing KDE won't hurt Gnome at all.

---

### Post by Karma_Police on 2006-01-19
You probably only need the kdelibs. Anyway, if you install through synaptic, it should install everything it needs.

You can try this guide to make kde apps look better in gnome :) :
[http://ubuntuforums.org/showthread.php?t=56630&highlight=gnome+kde+skype](http://ubuntuforums.org/showthread.php?t=56630&highlight=gnome+kde+skype)


EDIT:

From the rosegarden [faq]("http://www.rosegardenmusic.com/resources/faq/#toc2"):

> 1.1.  Do I have to be using a particular desktop environment (KDE or whatever)?

No. Rosegarden uses the KDE libraries for various common controls, but you can run it under any window manager or graphical environment you like with no change in functionality. 

---

### Post by bluevoodoo1 on 2006-01-19
[QUOTE=Karma_Police]You probably only need the kdelibs. Anyway, if you install through synaptic, it should install everything it needs.

You can try this guide to make kde apps look better in gnome :) :
[http://ubuntuforums.org/showthread.php?t=56630&highlight=gnome+kde+skype](http://ubuntuforums.org/showthread.php?t=56630&highlight=gnome+kde+skype)


EDIT:

From the rosegarden [faq]("http://www.rosegardenmusic.com/resources/faq/#toc2"):[/QUOTE]

Shoot, I forgot to look at their FAQ, I've just been searching around here! THANKS!!!

---

