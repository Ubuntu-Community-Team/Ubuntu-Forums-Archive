---
title: "installing .deb files."
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by equal on 2005-12-17
okay. here's the deal. I downloaded the binaries to install snes9x super nintendo emulator. I transformed the .tar.gz file into a .deb file. I ran the dpkg -i snes9x-1.43-linux_x86-2_all.deb command, and it made a big show of installing it. Now, however, I have NO CLUE where this program has installed to, or how to access it. The .deb file was originally located in ~/Desktop/My Documents/SNES/

Any clue folks?

---

### Post by Kyral on 2005-12-17
How exactly did you transform it into a deb pack? CheckInstall?

Anyway it prolly installed into the PATH someplace, trying executing the command snes9x. BTW you could have just used apt-get to install it

```
sudo apt-get install gsnes9x
``` will install SNES9x and a nice frontend

---

### Post by aysiu on 2005-12-17
Don't forget to enable the Multiverse repositories before apt-getting.
See the first link of my sig for more details.

---

### Post by equal on 2005-12-17
Thanks for the help guys! One of these days I'll figure out how to install programs from .tar.gz files.

---

### Post by jackwhite on 2005-12-18
I've downloaded a .deb for truecrypt to my desktop. (I checked on synaptic but couldn't find it there).

The instructions are just to type 'dpkg -i truecrypt.deb'.

When I try that i get :

```
dpkg: error processing truecrypt.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 truecrypt.deb
```

I don't really have a clue what could be going on, any help?

---

### Post by aysiu on 2005-12-18
If you downloaded it to your desktop, you should be typing this into your terminal: ```
cd Desktop
sudo dpkg -i truecrypt.deb
```

---

### Post by jackwhite on 2005-12-18
I knew it must have been something simple! Thanks for your help. 

...think i'm going to have to learn some comand line basics

---

### Post by aysiu on 2005-12-18
[QUOTE=jackwhite]I knew it must have been something simple! Thanks for your help. 

...think i'm going to have to learn some comand line basics[/QUOTE] Actually, the problem is that just about *every* other distro except Ubuntu uses a separate root account instead of sudo. So if you ever get instructions from a website, they'll always say ```
dpkg -i blah.deb
``` and you'll always have to put a *sudo* in front of it.

---

