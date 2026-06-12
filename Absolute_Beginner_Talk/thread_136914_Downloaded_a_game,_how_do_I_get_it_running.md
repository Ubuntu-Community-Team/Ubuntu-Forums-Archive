---
title: "Downloaded a game, how do I get it running?"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by bulletbutter on 2006-02-26
Sorry for the newb question but this is driving me nuts!  I just downloaded the linux souce for a game and I need to know how I install/play the game.  The help documentation just told me to use 'make' or 'make install'.  It gives me the following error message when I try sudo make / sudo make install in terminal
```

make:*** No rule to make target 'install'.  Stop.

```

---

### Post by Kurt` on 2006-02-26
Which game is it?

Did you read the README or INSTALL file that came with the source?

Did you run the ./configure command first?

---

### Post by Sutekh on 2006-02-26
Someone's gonna have to say, you need to install the basic components needed for compiling.  They can be covered with the package build-essential
```
sudo apt-get install build-essential
```
Usually```
./configure
make
sudo make install
``` is the way to go. 

Often```
sudo checkinstall
``` is recomended over 'make install'.

[Installing Software in Ubuntu - by ]("http://www.psychocats.net/linux/installingsoftware.php")[aysiu]("http://www.ubuntuforums.org/member.php?u=21941") - Section 4 is a better explanation than above

---

### Post by bulletbutter on 2006-02-26
[QUOTE=Kurt`]Which game is it?

Did you read the README or INSTALL file that came with the source?

Did you run the ./configure command first?[/QUOTE]

The game is Pong.  I read the readme and it told me to just use 'make' or 'make install'.  Also
```

./config: No such file or directory

```
I am really new at this linux stuff.  I am sure nothing is wrong with the game, its just that I have NO idea what I have to do.

---

### Post by Sandlst on 2006-02-26
Please post where you downloaded it from-that way we can see whats up ourselves.

---

### Post by Sutekh on 2006-02-26
Well the link I posted above should help out, you need to use ```
./configure
``` NOT ```
./config
```thats why it says no such file.



I think pong is available through **Synaptic**.  Synaptic is a program that provides an easy way of installing software in Ubuntu.  It's available from the **System -> Administration Menu**.  It will require your password to open, then you can browse through and select the packages you want to install.

To get pong in this way, first you need to enable the **universe repository**.  A repository is basically an online location that hosts a huge number of packages that can be installed in Ubuntu.

This link will show you how to enable the universe repository - [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

Once that is done, you can either go into Synaptic and search for pong and mark if for installation and click Apply.  Or you can use this code to install it from the command line

```
sudo apt-get install pong2
```

---

### Post by bulletbutter on 2006-02-26
Alright, got it thanks guys. 

Sutekh, I was posting my reply before you made yours.  Sorry I wasn't quick enough.

---

### Post by Sutekh on 2006-02-26
If you got it working in the end, then its all good!

---

