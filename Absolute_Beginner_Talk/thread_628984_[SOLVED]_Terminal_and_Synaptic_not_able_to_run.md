---
title: "[SOLVED] Terminal and Synaptic not able to run"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by linuxisfree on 2007-12-01
HI everyone... as you can see my problem is 2 part (actually, its 2 problems)

1. My Terminal refuses to run (after i click it, it just doesn't show up)
2. Same is true for my synaptic.

PLEASE, HELP!!!

:(

In line with this, Is there anyway to repair install (incase i have to)?

---

### Post by victorbrca on 2007-12-01
1- How about if you press Alt + F2 and enter "gnome-terminal" (without the quotes)


Vic.

---

### Post by linuxisfree on 2007-12-02
HI:) Thanks for the reply! Just tried it, for both terminal and synaptic... neither worked :(. Thanks for the suggestion, though:)

---

### Post by corney91 on 2007-12-02
Can you get into Add/Remove under Applications?
If so, search for terminal and make sure it has a ticked checkbox (it should be the top one, but you can install others if you want). Same for Synaptic.

---

### Post by linuxisfree on 2007-12-02
Yes i can get into add/remove... will try that, but first... new development...
i tried to run gnome-terminal and synaptic in recovery mode, but it wouldn't because i seem to be missing some file or something

libpangoxft-1.0.so.0

Any ideas?

EDIT: just checked the add / remove suggestion... both synaptic and terminal boxes are checked. :)

---

### Post by corney91 on 2007-12-02
> **linuxisfree said:**
> 
i tried to run gnome-terminal and synaptic in recovery mode, but it wouldn't because i seem to be missing some file or something

libpangoxft-1.0.so.0

Any ideas?


You need libpango installed. I have libpango1.0-0,libpango1.0-common, and libpango1.0-dev installed. You may not need all of these but running the following should fix it:
```
sudo apt-get install libpango1.0-0 libpango1.0-common libpango1.0-dev
```

You probably don't need the -dev, so maybe try it without first and then install it if it still doesn't work

---

### Post by linuxisfree on 2007-12-02
> **corney91 said:**
> You need libpango installed. I have libpango1.0-0,libpango1.0-common, and libpango1.0-dev installed. You may not need all of these but running the following should fix it:
```
sudo apt-get install libpango1.0-0 libpango1.0-common libpango1.0-dev
```

You probably don't need the -dev, so maybe try it without first and then install it if it still doesn't work

Hi, actually a bit ahead of you there... i did install those when i was in recovery mode (including dev), but it still does not work. and, just an addition, even add/remove does not want me to install anything. Maybe a repair install (if there is such a thing) would do?

---

### Post by corney91 on 2007-12-02
> **linuxisfree said:**
> Hi, actually a bit ahead of you there... i did install those when i was in recovery mode (including dev), but it still does not work. and, just an addition, even add/remove does not want me to install anything. Maybe a repair install (if there is such a thing) would do?
Just remembered you couldn't open the terminal, and I gave you a command to run#-o
Anyway, how did you manage to install the pango packages?

---

### Post by victorbrca on 2007-12-02
Can you run xterm? Maybe you can try to add them from xterm, or even tty1.


Vic.

---

### Post by linuxisfree on 2007-12-03
> **corney91 said:**
> Just remembered you couldn't open the terminal, and I gave you a command to run#-o
Anyway, how did you manage to install the pango packages?

i couldn't open terminal in normal mode, but was able to install the packages in recovery mode (which is after all purely terminal - no gui, right?)

---

### Post by linuxisfree on 2007-12-03
> **victorbrca said:**
> Can you run xterm? Maybe you can try to add them from xterm, or even tty1.


Vic.

HI, um... possibly going to sound  really stupid here, but, what's xterm(SORRY)? I did add them from tty - at least thats what i think recovery mode is, am i right?

---

### Post by victorbrca on 2007-12-03
As I've been told before, no question is stupid!! :)

xterm is another terminals that comes with (i think) almost every version of Linux that has X server. Just go to Alt + F2 and type "xterm". It will look very simple, like this:

[IMG]http://www.paradigm.ac.uk/images/linux-tree-xterm.gif[/IMG] 

I don't think tty1 is recovery mode (I'm a noob). If you press from Ctrl+Alt+F1 to F6 you will get cli on your monitor (there's no X server). Type Ctrl+Alt+F7 to go back to X.

Vic.

---

### Post by linuxisfree on 2007-12-03
> **victorbrca said:**
> As I've been told before, no question is stupid!! :)

xterm is another terminals that comes with (i think) almost every version of Linux that has X server. Just go to Alt + F2 and type "xterm". It will look very simple, like this:

[IMG]http://www.paradigm.ac.uk/images/linux-tree-xterm.gif[/IMG] 

I don't think tty1 is recovery mode (I'm a noob). If you press from Ctrl+Alt+F1 to F6 you will get cli on your monitor (there's no X server). Type Ctrl+Alt+F7 to go back to X.

Vic.

Thanks Vic:) That pretty much solves my terminal problem... now there's just synaptic its also not showing up... any ideas?

Thanks again for the "xterm" tip!!!:D

EDIT: xterm's real simple looking... I LIKE IT!!!:D Oh, and corney91, i just now installed the rest of the libpango packages (i mean everything i could), you know, just to be on the safe side:) Thanks for the loads of help guys!!

---

### Post by Partyboi2 on 2007-12-03
You could try opening synaptic via gnome terminal and see if it shows up any error messages.
```
sudo synaptic
```

---

### Post by linuxisfree on 2007-12-03
> **Partyboi2 said:**
> You could try opening synaptic via gnome terminal and see if it shows up any error messages.
```
sudo synaptic
```

Hi Partyboi2, thanks for the suggestion. The following error message resulted...

```
synaptic: error while loading shared libraries: libpangoxft-1.0.so.0: cannot open shared object file: No such file or directory 
```

---

### Post by corney91 on 2007-12-03
> **linuxisfree said:**
> Hi Partyboi2, thanks for the suggestion. The following error message resulted...

```
synaptic: error while loading shared libraries: libpangoxft-1.0.so.0: cannot open shared object file: No such file or directory 
```

You could try reinstalling the pango packages. I think the only one you'll need is libpango1.0-0 but try the others if its still doesn't work:```
sudo apt-get install --reinstall libpango1.0-0
```

---

### Post by linuxisfree on 2007-12-04
> **corney91 said:**
> You could try reinstalling the pango packages. I think the only one you'll need is libpango1.0-0 but try the others if its still doesn't work:```
sudo apt-get install --reinstall libpango1.0-0
```

Hi, the following happened when i tired that...

Any idea what it means??? Thanks!!

EDIT: Just so everyone knows, It now works, corney91 was right, just needed to reinstall tha libpango1.0-0 package... Thanks all for the help:) NO NEED TO REINSTALL, YAY:D

i still am not sure what the message in the attached file means, though... could anyone explain it, please? THANKS!!! You were all extremely helpful!! :D
(I can now mark this as solved. PHEW!!!) hehehe

---

### Post by mahiyar on 2007-12-04
Just curious, how did you lose this package in the first place? From what I understand this is the base package for font rendering.

---

### Post by linuxisfree on 2007-12-05
> **mahiyar said:**
> Just curious, how did you lose this package in the first place? From what I understand this is the base package for font rendering.

Actually, its kinda my bad, i may have deleted something i shouldn't have touched in the first place:(

---

### Post by Partyboi2 on 2007-12-05
> **linuxisfree said:**
> Actually, its kinda my bad, i may have deleted something i shouldn't have touched in the first place:(
I find those times the best teacher.

---

