---
title: "3D chess error?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by izizzle on 2007-07-26
I want to enable 3d mode in the chess that came with ubuntu, but when I go to View>3D, it gives an error about openGL, and says that I have to install something. Can someone help me out, I really want to play in 3d mode.

---

### Post by Old Pink on 2007-07-26
Ditto ;) 

Been working on it for weeks. Still no luck.

What video card you using? It support direct rendering/3D? :)

---

### Post by RomeReactor on 2007-07-26
you will need to download [this package]("http://sourceforge.net/project/showfiles.php?group_id=6348&package_id=179437"); to install it, double click on it. You also need **python-opengl** and **libgtkglext1**; look for them in Synaptic (or Adept if you're running KDE), or to install from the terminal:
```
sudo apt-get install python-opengl libgtkglext1
```
After those packages are installed, you should be able to play in 3D mode.

Having said that, [Brutal Chess]("http://brutalchess.sourceforge.net/") looks much better, though the AI isn't as good as GLChess. You can find Brutal Chess in Synaptic, Add/Remove (or Adept); or to install from the terminal:
```
sudo apt-get install brutalchess
```

---

### Post by izizzle on 2007-07-28
TO ROMEREACTOR

Don't ask me why I am asking you this, but how do I uninstall the .deb that you told me to download.

---

### Post by RomeReactor on 2007-07-28
For **python-gtkglext1_1.1.0-2feisty_i386.deb** or **python-gtkglext1_1.1.0-1_i386.deb**:
```
sudo apt-get --purge remove python-gtkglext1
```
then:
```
sudo apt-get update
```
For **python2.4-gtkglext1_1.0.1-1_i386.deb** or **python2.4-gtkglext1_1.1.0-1_i386.deb**:
```
sudo apt-get --purge remove python2.4-gtkglext1
```
then:
```
sudo apt-get update
```

If installing python-gtkglext1 didn't work for you (as originally posted by [DoktorSeven]("http://ubuntuforums.org/showpost.php?p=2510684&postcount=11")), the solution posted in [Mike's Planet]("http://www.mikesplanet.net/2007/03/turning-on-3d-chessboard-in-feisty/") seems to work for most people.

---

### Post by psterrett on 2007-08-05
Thanks, this worked for me... although I must admit that you were right about it being uglier than Brutal Chess.

---

### Post by Macros42 on 2007-08-05
> **RomeReactor said:**
>  the solution posted in [Mike's Planet]("http://www.mikesplanet.net/2007/03/turning-on-3d-chessboard-in-feisty/") seems to work for most people.

I just followed the instructions here and it works perfectly. Thanks.

---

### Post by barbaricrunner on 2007-08-07
Worked like a charm. however, brutal chess may not work smoothly if you have no/crappy graphics card, but thats a problem that is easily fixed. :)

---

