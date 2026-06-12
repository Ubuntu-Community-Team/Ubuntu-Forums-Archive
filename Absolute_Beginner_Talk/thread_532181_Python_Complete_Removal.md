---
title: "Python Complete Removal"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by JamesA on 2007-08-22
Hey everyone - i think i may just of done the most stupid thing i've ever done on a linux machine.

Last night, at 4am, i decided to delete python 2.4 using synaptic. However i chose 'complete removal'. When watching the delete bar move along quite slowly, i relised it was removing other applications such as amsn and xchat. To my horror when i clicked on the menu bar, i could see random applications disapearing at an extreamly alarming rate.

As i couldn't cancel i immediatly turned off my machine by holding in the button.

Did i just delete every application that has some sort of python in it? Am i now completely fubard?

Now when i login all i get is my mouse icon with a gray screen, no gnombe, no fluxbox.

Is there anyway, anyway at all, by command line, to restore the programs my machine just uninstalled? Or am i going to have to apt-get them one by one? If its the latter, i'd be better of just wiping my Hard drive and resintalling, but i really don't want to do that.

Please help, any suggestion welcome, not matter how small and trivial you think they might be.

If i could go back intime, i'd punch myself in the face.

---

### Post by irish_flu on 2007-08-22
First, try

```

sudo apt-get install ubuntu-desktop

```

The "ubuntu-desktop" package has a dependency set up for all the packages ubuntu needs to run (including all the default-installed apps).

That ought to set you right.

EDIT: I added the word "install" into the command I posted above.  Apparently, I haven't had enough coffee yet (sorry about that).

---

### Post by JamesA on 2007-08-22
nice one irish!

I'll give it a go asap and tell you how i got on.

---

### Post by JamesA on 2007-08-22
Thanks man, making this post from ubuntu :)

Go raibh maith agat

---

### Post by irish_flu on 2007-08-22
No problem, glad it worked out for you!

---

