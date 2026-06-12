---
title: "I finally did it!"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Irmis on 2007-07-05
I knew that with enough tinkering I'd eventually create a problem I couldn't fix. Last time I opened Adept Package Manager it crashed, since then it opens in a mode that will not let me make any changes. I tried restarting but that didn't work. I looked for it on the process table, I got nothing. Soo any ideas on how to fix this?

---

### Post by taurus on 2007-07-05
What is the error message when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
gksudo synaptic
```

---

### Post by Irmis on 2007-07-05
"The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found"

Wow gksudo is something I never used before, sweet more to tinker with.

---

### Post by fastpakr on 2007-07-05
Are you in Ubuntu or one of the other versions?

---

### Post by taurus on 2007-07-05
Looks like you are running KDE instead of Gnome.  How about

```
kdesu synaptic
```
or
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by BlueNoteExpress on 2007-07-05
His profile says he's using Kubuntu.  I'm still a newbie myself, but I think he'll have to use the KDE equivalent of gksudo.  Unfortunately, I don't know what that is.

---

### Post by Irmis on 2007-07-05
For Kdesu Synpatic it said "synaptic: not found"

For the update one it returned "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." at the end.

Oh yea using Kubuntu, I think its prettier.

---

