---
title: "Cannot get ccsm with sudo apt-get"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by eimor on 2007-11-16
Hi, i cant get to download the ccsm package via terminal. What am i doing wrong?
The last line that shows in terminal says that ccsm package could not be found, what does this mean?:(

---

### Post by Rmantingh on 2007-11-16
That's because it isn't called ccsm, it's called compizconfig-settings-manager.

sudo apt-get install compizconfig-settings-manager

Give that a try.

---

### Post by eimor on 2007-11-16
couldnt find compizconfig-settings-manager either, i tried to look this up in
synaptics and didnt find anithing. Cant understand why

---

### Post by overdrank on 2007-11-16
> **eimor said:**
> couldnt find compizconfig-settings-manager either, i tried to look this up in
synaptics and didnt find anithing. Cant understand why

HI are you using feisty or gutsy? you may want to enable your repos. You can add repos under system, administration, software sources. The ubuntu software and updates tab. Hope this helps and good luck!

---

### Post by Rmantingh on 2007-11-16
What version of Ubuntu are you using?
I myself am using Gutsy 7.10.

Is compiz itself installed?

sudo apt-get install compiz

---

### Post by runemaste644 on 2007-11-16
if you are using Feisty, just add a repository that has compiz in it, like trevino's feisy eyecandy repository.

---

### Post by dhobbs on 2007-11-16
Use synaptic and search for "compiz config settings manager" that will show you what the package is actually called.

Or search for Advanced Desktop Effects in Add/Remove Programs and you should find it as well, it's listed under a different name though.

Edit:  If the above doesn't work then you should tell us which version of Ubuntu you are running.

---

### Post by eimor on 2007-11-16
hi, im back from work, the thing is i dont have repositries activated, could that be the reason of my problems? if it is so, how can i activate or update my repositories

---

### Post by forestpixie on 2007-11-16
try software sources in system> admin 
enable main, universe, multiverse and probably restricted

reload
and try again - but you still haven't said which version of ubuntu you're using - it makes a difference I believe to the compiz software

---

### Post by eimor on 2007-11-16
that fixed it, then i went to synaptics and got the ccsm, thank you all. im so happy
:)

---

### Post by overdrank on 2007-11-16
> **eimor said:**
> that fixed it, then i went to synaptics and got the ccsm, thank you all. im so happy
:)

Great please mark the thread as solved with the thread tools thanks and good luck!

---

