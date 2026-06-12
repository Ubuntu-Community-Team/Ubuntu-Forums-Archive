---
title: "How to run scorched3d?`"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2006-09-30
How do I run scorched 3d. I click the .deb file and installed it what should I enter in terminal to open it? and how can I add it to the menu?

---

### Post by spyker3292 on 2006-09-30
bump

---

### Post by Perfect Storm on 2006-09-30
try with:
```
scorched3d
```
in the terminal.

No need to bump a thread after 8 min.

---

### Post by spyker3292 on 2006-09-30
> **Artificial Intelligence said:**
> try with:
```
scorched3d
```
in the terminal.

No need to bump a thread after 8 min.
Nope
Sorry

---

### Post by Perfect Storm on 2006-09-30
If you have installed scorched3d properly it should be:
```
scorched3d
```
(remember that linux is case sensitive).

Just tested it on my own box.

What error output does the terminal show?

---

### Post by spyker3292 on 2006-09-30
i installed it by clicking the deb file then when I type scorched3d the error is

error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared objedt file: no such file or directory

---

### Post by spyker3292 on 2006-09-30
and its version 40

---

### Post by Perfect Storm on 2006-09-30
The error means you need to install libSDL_net because it isn't installed.

You can do that through synaptic (System tabs ---> Adminstration) or by CLI:

```
sudo aptitude install libsdl-net1.2
```

---

### Post by spyker3292 on 2006-09-30
> **Artificial Intelligence said:**
> The error means you need to install libSDL_net because it isn't installed.

You can do that through synaptic (System tabs ---> Adminstration) or by CLI:

```
sudo aptitude install libsdl-net1.2
```
is there another way to install it I haven't gotten the internet set up. I'm using a jump drive to put stuff on it.

---

### Post by Perfect Storm on 2006-09-30
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libsdl-net1.2&searchon=names&subword=1&version=dapper&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libsdl-net1.2&searchon=names&subword=1&version=dapper&release=all) - libsdl net

for more packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Make sure all other requirements is met: [http://doc.gwos.org/index.php/Scorched_3D](http://doc.gwos.org/index.php/Scorched_3D)

---

### Post by spyker3292 on 2006-09-30
great... now the same thing happened but instead of libSDL it says libopena.so.0  where can I find this

---

### Post by Perfect Storm on 2006-09-30
Use my second link in my previous post and search for libopenal0a

---

### Post by Panic_Gamer on 2006-12-30
> **spyker3292 said:**
> great... now the same thing happened but instead of libSDL it says libopena.so.0  where can I find this
Hey I'm kinda new at Ubuntu and I&#8217;m running Drapper, I've got Scorched 3D and some other games for it. I too don't have internet and have to go get the extra packages manually. But when I get the packages usually I just click on then off the desktop then try to install the game, but it still doesn't work. What I'm I doing wrong, I mean is there another way to add the packages to the system rather than clicking on it,  should I use the terminal and if so how would I type in the stuff.

---

### Post by Perfect Storm on 2006-12-30
Try with

sudo dpkg -i XXXXXXXXXXXX.deb

should do it, just run the command where the package is.

---

### Post by Panic_Gamer on 2007-01-02
Yeah i tryed that but for some strange reason it didn't work this time, but i know that command line works though. But what if the other files aren't in .deb? How would I then add them?

---

### Post by Perfect Storm on 2007-01-04
In which format are we talking about?

---

