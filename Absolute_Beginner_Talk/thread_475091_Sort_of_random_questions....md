---
title: "Sort of random questions..."
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by ts51 on 2007-06-15
Ok, just have some quick Ubuntu questions. First off, how do you remove the hard drive icons off your desktop? (Not all of them, just certain ones)

[COLOR=Red][SOLVED][/COLOR]Also, how do you configure Beryl to run automatically when you sign? I have my account set to automatic login, so I boot right to my user. [COLOR=Red][SOLVED] [COLOR=Black]Thanks, andrax! [/COLOR][/COLOR]

Last, does anyone know of an os x like dock readily available in the Package Manager? 


Please help me out, andrax

TS51

---

### Post by Andrax on 2007-06-15
For beryl to start automatically, go inot System>Preferences>Sessions and create a new one, called Beryl with the command beryl-manager.

PS. For the command, type it just as I did, **_no caps_**

Andrax

---

### Post by Andrax on 2007-06-16
I'm glad I could help you :D

About the other stuff, as I'm a beginner too, I don't really know how to do it.

~Andrax

---

### Post by aktiwers on 2007-06-16
> **ts51 said:**
> [/COLOR]

Last, does anyone know of an os x like dock readily available in the Package Manager? 


Please help me out, andrax

TS51

Sorry it ain't in the repo but install instructions are on the site:
[http://www.thelinuxdock.blogspot.com/](http://www.thelinuxdock.blogspot.com/)

---

### Post by corney91 on 2007-06-16
For the dock I would recommend Avant Window Manager - it might be in your Synaptic Package Manager. If not, [this tutorial]("http://ubuntuforums.org/showthread.php?t=385981")is relatively simple to follow. All the other docks I could find were really tedious to install and set up but this one you can drag and drop icons into it. Oh but this one doesn't have the larger icons when moused over. Hope this helps.

---

### Post by bapoumba on 2007-06-16
> **ts51 said:**
> Ok, just have some quick Ubuntu questions. First off, how do you remove the hard drive icons off your desktop? (Not all of them, just certain ones)
You have to mount them in another file than /media (anything mounted in /media is set up to show on the desktop by default. This can be changed also).
Please post the output to
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by grifftel on 2007-06-16
Last, does anyone know of an os x like dock readily available in the Package Manager? 

You could also try Kiba Dock, again not in the repo.

[http://www.kiba-dock.org/](http://www.kiba-dock.org/)

This one is lots of fun with animated jumping spinning icons, and very configurable!:p

Geoff

---

### Post by Andrax on 2007-06-16
For an OS like dock, you could try AWN with Avant, if you want to read this for instalation:

[http://http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+manager]("http://http://ubuntuforums.org/showthread.php?t=385981&highlight=avant+window+manager")

There you can find the steps to install it both trough the synaptic package manager and steps for manual installation.

---

### Post by mahiyar on 2007-06-17
Beryl + Kiba Dock == Lots of fun && some edgy moments too

---

### Post by Andrax on 2007-06-17
Could anybody please put a screen shot of the Kiba Dock, and a question, Which dock does the funny thing of like when you grab an icon and move it around pushing the others and stuff like that?

---

### Post by mahiyar on 2007-06-17
Search "you tube" for kiba dock videos, you will find tons of them.

---

### Post by Andrax on 2007-06-17
I like it, should I switch to it?

If I did, how do I uninstall AWN and install Kiba?

Does Kiba have any problems?

---

### Post by meborc on 2007-06-17
[http://www.linux.org.ru/gallery/bigkHUDlc.jpg](http://www.linux.org.ru/gallery/bigkHUDlc.jpg)

:)

---

