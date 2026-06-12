---
title: "[SOLVED] No 3D Chess -- Python Related"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by Therion on 2007-10-23
Whenever I try to play Chess from the Applications/Games menu and switch the view from 2D to 3D I'm given the following error message:
> Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.
Could someone explain how I would go about installing the necessary applications, please?  I'm sure my nVidia 8800GTS can handle 3D chess and I can run 3D screensavers, so I'm not sure what the problem is.

Thanks in advance!!

---

### Post by Paul820 on 2007-10-23
From the terminal:

> sudo apt-get install python-opengl python-gtkglext1

---

### Post by Dr Small on 2007-10-23
> **Paul820 said:**
> From the terminal:
> sudo apt-get install python-opengl python-gtkglext1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python-gtkglext1

I would like to have 3d chess too :p

---

### Post by mivo on 2007-10-23
python-gtkglext1 is not in the Feisty repository, so if you are using Feisty, use these:

```

sudo apt-get install python2.4 python-imaging python2.4-opengl libgtkglext1
wget -c http://prdownloads.sourceforge.net/glchess/python-gtkglext1_1.1.0-2feisty_i386.deb
sudo dpkg -i python-gtkglext1_1.1.0-2feisty_i386.deb

```

Taken from [here]("http://ubuntuforums.org/showpost.php?p=3182568&postcount=12").

---

### Post by Paul820 on 2007-10-23
It's on mine:
EDIT: I'm using Gutsy though, so maybe that's it?

---

### Post by Dr Small on 2007-10-23
> **mivo said:**
> python-gtkglext1 is not in the Feisty repository, so if you are using Feisty, use these:

```

sudo apt-get install python2.4 python-imaging python2.4-opengl libgtkglext1
wget -c http://prdownloads.sourceforge.net/glchess/python-gtkglext1_1.1.0-2feisty_i386.deb
sudo dpkg -i python-gtkglext1_1.1.0-2feisty_i386.deb

```

Taken from [here]("http://ubuntuforums.org/showpost.php?p=3182568&postcount=12").
That worked absolutely perfect!
I haven't ever had 3D Chess to work in glChess!

This calls for an entry on my blog, so I do not forget!

Thanks.

---

### Post by mivo on 2007-10-23
The 3D is a little underwhelming, but I used Chessmaster for many years, so I'm probably a bit spoiled. :) For a bit more impressive visuals, take a look at Brutal Chess (package: brutalchess). There are some screenshots [here]("http://brutalchess.sourceforge.net/?cat=2").

---

### Post by Dr Small on 2007-10-23
Yeah, my mom has Chessmaster 9000 for windows, but it wouldn't work on wine :(
But brutalchess looks nice too. :D It works for me ;)

---

### Post by Therion on 2007-10-23
> **Paul820 said:**
> 

From the terminal: ...
Most excellent... Thank you, Sir!!

---

### Post by subs on 2007-11-24
this is gr8.... thnx

---

