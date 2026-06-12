---
title: "Terminal has stopped working"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by supertails on 2008-01-11
Applications >> Accessories >> Terminal 

This program isn't working. It works for simple code but when I try to install a program by running the terminal it only pops open for 1 second if that and just doesn't work. I have try copying the code into the terminal but it closes before I can even press enter. I also drag the program in the terminal and that doesn't work but it works better though. Mainly because it doesn't close instantly after put it in. How do I fix the problem?

---

### Post by yabbadabbadont on 2008-01-11
Hit Alt-F2 (in Gnome) and enter "gnome-terminal" without the quotes.  Does the terminal open and stay open?

---

### Post by supertails on 2008-01-11
Yes it does but I don't have a problem with it opening up and staying open. I have a problem with it closing when I try to run a program though it and enter code.

---

### Post by yabbadabbadont on 2008-01-11
Please provide the exact command that you run in the terminal that causes the problem.

---

### Post by taurus on 2008-01-11
What program or code did you enter from a terminal?

---

### Post by supertails on 2008-01-11
It's called Frozen Bubble. It's a game that is in tar.bz2 format.

---

### Post by yabbadabbadont on 2008-01-12
It is already available in the universe repository.
```
/home/daffy $ aptitude show frozen-bubble
Package: frozen-bubble
State: not installed
Version: 2.1.0-1
Priority: extra
Section: universe/games
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 729k
Depends: libsdl-perl (>= 1.20-8), perl (>= 5.8.8-6.1), perlapi-5.8.8, libc6 (>= 2.5-0ubuntu1), libglib2.0-0 (>= 2.12.0), libpango1.0-0 (>= 1.15.0),
         libsdl-mixer1.2 (>= 1.2.6), libsdl-pango1, libsdl1.2debian (>= 1.2.10-1), frozen-bubble-data (= 2.1.0-1), fb-music-high | fb-music-low
Replaces: frozen-bubble-lib
Description: Pop out the bubbles !
 Frozen-Bubble is a clone of the popular "Puzzle Bobble" game, in which you attempt to shoot bubbles into groups of the same color to cause them to pop. It
 features 100 single-player levels, a two-player mode, music and striking graphics. 
 
 This game is widely rumored to be responsible for delaying the Woody release. 
 
 URL: http://www.frozen-bubble.org/

```
System->Administration->Synaptic Package Manager
Then Settings->Repositories
Make sure that the universe repository is enabled and ok the dialog.  If you had to enable it, then hit the Reload button next.  Now search for frozen-bubble and install it.

---

