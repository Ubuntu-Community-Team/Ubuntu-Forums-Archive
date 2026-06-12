---
title: "controlling programs"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by ssaamon on 2007-10-22
Im just wondering how would you use the terminal to control say the networking program for ubuntu?

the program: gksu network-admin (i.e. change wireless connection, etc...)


is there a general protocol to follow when controlling programs?

thanks

---

### Post by molly_001 on 2007-10-22
I'll write here about three ways, the first of which is hardest - but bear with me because it affects the other two.

If a package is installed into your Ubuntu installation, then you can access the "executable" (so to speak) by navigating to the folder in which it is installed and then invoking the script name.

For instance, if you have installed the popular free game FreeCiv, a clone of Civilization, and you installed it into folder /usr/freeciv , then from the CLI (terminal) you would type:

$ cd ..    [  repeat until you reach /(root)   ]

$ cd /usr/freeciv

$ civclient   (the script to run game happens to be called CivClient)

The above implies that you are comfortable with the 

```
./configure --> make --> make install 
```
routine for installing Debian packages.

-------------------------

Now how many people know the name of the executing script for the application they desire, much less where in the file folder system it was installed if they used (for instance) Synaptic to do the installing?  Such information is not obvious for beginners.  (I am not implying you are a beginner.)

So another quick way to run a command for an *installed* package is to hit CTRL + F2 while in the GUI.  This is simply a "Run" (Windows-like) command.  Here again, you have the know the file name of the installed script.  So I would hit CTRL + F2 and then type civclient and hit enter.  Ubuntu is good about filling out the remaining characters for *installed* programs, when using this CTRL + F2, so when I started to type "civ..." it would provide me with the suggestion of "civclient" and I would not need to type the whole thing out.

------------

Your best bet when installing packages is to use Google to find the page where the author of the script has detailed everything one needs to know.  For instance, if you see a package out there that you want to try called "charlies-network-admin" then Google that first before installing and it will make your life a lot easier, in regard to knowing how to invoke the package to "run" once you have it installed.

---

