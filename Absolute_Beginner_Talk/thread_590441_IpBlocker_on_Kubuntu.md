---
title: "IpBlocker on Kubuntu"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Fred_E _krugar on 2007-10-24
I have been using IPBlocker for Ubuntu, but I have decided to try out Kubuntu for awhile.
 I figured that I could just install IPBlocker the same way I did in Ubuntu...well that doesnt work. What do I need to do different to get it installed. 
 When I try to install the .deb file it just opens it as if it were just a zipped file. But while in Ubuntu you just click on the .deb file and it installs instantly. 
  What gives, what do I need to do??

---

### Post by Pumalite on 2007-10-24
I don't use Kubuntu, but let's do a couple of things. Make sure you have installed build-essential. Second: do you have File Roller in Kubuntu?

---

### Post by Matakoo on 2007-10-24
If I remember correctly, in  Kubuntu Feisty you right-click on the .deb files and you should find a "Install" in the Actions menu. Much improved in Gutsy though :)

And if the above doesn't work, you can always install it from a terminal (my preferred version of installing stand-alone .deb files, which is why I don't remember exactly how it worked in GUI-mode only in Feisty).

Open the folder where the .deb file is. Right-click and choose "Open terminal here" from the Actions submenu.

Type this:

sudo dpkg -i IPblocker.deb

And off you go (assuming all dependencies are satisfied)

---

### Post by Fred_E _krugar on 2007-10-24
to puma: no it is not file roller it is ark.
 Mata: that did work but I had to install a few dependencies
 Thanks to all of ya.:)

---

