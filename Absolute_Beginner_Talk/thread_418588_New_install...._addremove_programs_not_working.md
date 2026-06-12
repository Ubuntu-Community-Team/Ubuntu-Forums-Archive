---
title: "New install.... add/remove programs not working"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Eduardo Serra on 2007-04-22
Ok, so I recently got Feisty installed..... all I have done so far is try to run an xvid video... Totem said it didnt have the codecs so it automatically downloaded them.... it worked fine..... I dont know if it has anything to do with it but bow every time I try to open add/remove programs it loads anc closes without letting me click or do anything.... Synaptci package manager does the exact same thing....

---

### Post by mabelrxu on 2007-04-22
try typing sudo synaptic into the command-line / terminal, and see what errors come up ...

---

### Post by flameproof on 2007-04-22
> try typing sudo synaptic into the command-line / terminal, and see what errors come up ...

For me it asks for "password" - I type it in - and nothing happens, back to command prompt.

Actually that happens with whatever I type in in Terminal, also Gedit etc. will not open. I also can't open synaptic from the screen menu

---

### Post by mabelrxu on 2007-04-22
uh oh ... try this:

do cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup to backup your xorg.conf
then do sudo nano /etc/X11/xorg.conf and check your InputDevice sections ... just look with your eyes ... does anything seem weird or odd or blatantly wrong?

possible sources of error include: gdm (to be more specific, the panels), keyboard (less likely since terminal works), and mouse (more likely, unless you used the mouse to open the terminal within your gdm instead of using the ones under ctrl + alt + f1 through F6

---

### Post by Eduardo Serra on 2007-04-23
I tried sudo synaptic..... it says: Segmentation fault (core dumped)..... I think I might just have  had a faulty install..... the cd wasnt in the best of conditions

---

### Post by mabelrxu on 2007-04-24
it it's a live cd, do a cd check first before booting into the live cd ... it takes a while, but should turn up any errors you have

---

