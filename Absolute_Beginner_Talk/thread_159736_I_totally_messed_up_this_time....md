---
title: "I totally messed up this time..."
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-13
Some of you probably remmember my question about KDE. Well, I've installed it, but I certainly didn't like all the KDE apps that appeared in my menus, so I've used the script that's going around here to try and delete it. 

The trouble is, instead of deleting KDE apps, it deleted Gnome apps...
Fortunately I realised what was happening before it deleted everything.

I then reinstalled the Gnome components from synaptics, and manually removed all the KDE stuff I could find.

I then restarted the computer, and here comes the big problem;
I can't get into Gnome. And obviousley I can't get into KDE as well, so I'm stuck in the terminal...
I don't know enough about the terminal to try and fix it from there, so now I'm on another computer downloading the ubuntu ISO image.

Before I go ahead with the ubuntu installation, if I manage to get there, I thought to ask here, maybe I can fix it another way, I'm probablly just too used to windows...

Is there anything I can do to fix the Gnome? 
Or do I have to Install ubuntu all over again?

If it's the latter,
since it's no me who installed ubuntu the first time, how do I do it?
Do I just put the CD in and it'll go to the installation process? Or do I need to mess with the bios?
should I format the disc(I don't have anything important, I just did a format...), or does it automatically fix the problem? is the a "repair" option like in windows?
And what kind of knowledge do I need to have for the installation? I understood that it's not complicated, is this true?

I hope somebody can help me here...
Thank you,
Josh:)

---

### Post by Tiede on 2006-04-13
when you are at the terminal, login with you username and password, and then at the prompt, type: ```
 sudo gdm 
```
if it doesn't work, post output here and try ```
 startx 
```.


If, as I suspected, the gnome login manager was uninstalled, you can do this: ```
 sudo apt-get install gdm 
```
\!/: I assumed that you have an "always-on" internet connection for the previous step, it will probably not work otherwise.

---
Suggestion: As you said that some gnome-specific procs were uninstalled, you can always do a ```
 sudo apt-get install ubuntu-desktop
``` to verify that all the basic gnome components of ubuntu are still in your system.
Hope that helps.

---

### Post by Caligula on 2006-04-13
It worked, thank's:D

---

