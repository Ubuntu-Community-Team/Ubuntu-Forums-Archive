---
title: "Installing Inkscape"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by Badojo on 2005-12-21
I really dont understand any apps on linux it probley simple but anyways I downloaded the sutopackage from the inkscape website and when I did what it said then ran it I didnt know what to do next to install it can somebody please help me.

---

### Post by Iandefor on 2005-12-21
Slow down lol... AFAIK, Inkscape comes with Ubuntu, or you can get it
from the [repositories]("https://wiki.ubuntu.com/Repositories"). If you're using a clean Ubuntu installation (IE, you 
just installed it and haven't played with the settings at all) then you need
to [add extra repositories to your computer]("https://wiki.ubuntu.com/AddingRepositoriesHowto"). Once you've done that, open up
Synaptic (System --> administration menu) and install it. If you don't know 
how to use Synaptic, [here's a guide]("https://wiki.ubuntu.com/SynapticHowto").

---

### Post by Badojo on 2005-12-21
Let me get this straight...
All those programs are already on the Ubuntu you just need to activate them basically?

---

### Post by Iandefor on 2005-12-21
lol...if you mean like in Windows, no. It's either already installed, and all you need to do is look under the "graphics" menu under the applications menu to start it, or you just have to get it from the repositories, which exist as a way to simplify the usually complex process of acquiring and installing software under Linux. That make sense? And no, all the software available in the repositories is not already on your computer. That's a listing of possible software packages you can choose to install on your computer.

---

### Post by aysiu on 2005-12-21
Read the second link in my sig.
Then follow the instructions in the first link in my sig.
Then open a terminal and type ```
sudo apt-get update
sudo apt-get install inkscape
inkscape
```

---

### Post by BobSongs on 2005-12-21
Greetings Badajo, and welcome to the fun and sometimes puzzling world of Linux.

Once you get Inkscape running I recommend the online tutorials.

**[INDENT]Help -> Tutorials -> [take your pick].[/INDENT]**

I did not know they were there initially. I actually stumbled across them in Windows since I've been planning to migrate to Linux for some time (by running cross-platform apps to make the transition easier).

Hope it helps.

---

### Post by Badojo on 2005-12-21
Does it matter that I dont have an internet connection set up?

---

### Post by aysiu on 2005-12-21
[QUOTE=Badojo]Does it matter that I dont have an internet connection set up?[/QUOTE] Yes! How about instead of trying to install Inkscape you try setting up your internet connection first?

---

### Post by Badojo on 2005-12-21
Well you misunderstand me then I have already downloaded Inkscape and its sitting on my desktop BUT I DONT KNOW HOW TO INSTALL IT! I believe it is a tar. file. Also I have no intension of setting up any network connection until POSSIBLY next January.

---

### Post by aysiu on 2005-12-21
Read the second link of my sig, especially the bottom bit.
You'll be hurting without an internet connection, though.

---

### Post by Evil Whisper on 2005-12-21
When following aysiu's guide I would recommend replacing **make install** with **checkinstall**.

Check install creates a deb package for you.  This makes for easier installation and removal of the application.

You can install check install by typing this in your console:

```

sudo apt-get install checkinstall

```

But installing check install requires an internet connection.

---

