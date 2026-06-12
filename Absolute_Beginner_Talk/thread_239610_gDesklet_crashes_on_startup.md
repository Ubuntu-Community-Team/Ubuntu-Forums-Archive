---
title: "gDesklet crashes on startup"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by MyBigToe on 2006-08-19
Sorry to bother you all again, but i cant get gdesklet to run.

I use the osx-style program launcher as my main way of strting programs too, so i feel a bit lost without it.

When gDesklet is started, the window comes up, but then promptly closes.
Ive tried reinstalling, then removing and installing again, but with little help

---

### Post by ComplexNumber on 2006-08-19
can you give a little more detail. for example, hopw are you starting gdeskelts? are you running them by typing the following into the terminal:
gdeslets open gdesklets-name.display
?


which window closes?

---

### Post by MyBigToe on 2006-08-19
nope, i was starting gDesklets via Applications > Accessories > gDesklets

The main window closes, and none of the desklets i previously had starting, start at all

---

### Post by ComplexNumber on 2006-08-19
> **MyBigToe said:**
> nope, i was starting gDesklets via Applications > Accessories > gDesklets

The main window closes, and none of the desklets i previously had starting, start at all
in that case, i would bet that you're missing some dependencies. install all the gnome-python packages you can find, then try again

---

### Post by MyBigToe on 2006-08-20
in synaptic?
i see no gnome-python packages.

And would it be that? i had it running ok, but just not anymore

---

### Post by MyBigToe on 2006-08-23
Apparently, my brother tried to create his own desklet and kept trying to open it with gDesklet, which caused gDesklet to crash, and it hasnt worked since.

Would that cause this?

TIA.

---

### Post by MyBigToe on 2006-08-23
^

---

### Post by Peverel on 2007-05-23
Pretty old thread, but current problem...

It's strange, I start gdesklets via Applications>Accessories>gdesklets

It loads up, looks funky for about 10 or 15min but then somehow totally disappears...when I try to run it again the shell window comes up and freezes, so I have to force quit it...

Any suggestions what to do?

---

### Post by piege on 2007-10-22
I have the exact same problem

---

### Post by DerekInGermany on 2007-10-22
I'm having the same problem.

When I try to start it in the terminal this is what happens:

me@me-desktop:~$ gdesklets
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!


Hope someone can help.

Derek

---

### Post by jonah1980 on 2007-10-22
> **MyBigToe said:**
> Sorry to bother you all again, but i cant get gdesklet to run.

I use the osx-style program launcher as my main way of strting programs too, so i feel a bit lost without it.

When gDesklet is started, the window comes up, but then promptly closes.
Ive tried reinstalling, then removing and installing again, but with little help

this is an old bug that's been around forever!! here, see this thread, it includes a deb file of a fixed gdesklets package. [http://ubuntuforums.org/showthread.php?t=423883](http://ubuntuforums.org/showthread.php?t=423883)

---

