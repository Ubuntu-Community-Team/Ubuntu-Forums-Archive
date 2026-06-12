---
title: "Things to know before installing"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by crackling on 2006-11-17
Hi. I'm completely new to Linux. I would like to know if there is anything I should know before installing. My main concerns are finding drivers for all my hardware, I have a Dell laptop and it came with a disc with all of the drivers. I don't have it with me right now (I'm at school), so I'm just wondering if the same disc will still work with Ubuntu (I really hope so but doubt it). I read around this forum and saw many topics about graphics drivers, it seems a little different from Windows, to say the least. People were posting snippets of code which I assume is to paste into the terminal, in what situations is installing drivers via terminal necessary? Also, I searched up some of my Intel drivers online and for OS type do I select Linux?

Sorry for the block of questions (and probably the tons more to come), I am completely new so bear with me! :D

---

### Post by Antrix on 2006-11-17
The disc that came with your laptop most likely only contains drivers for windows; so you will not be able to use this with Ubuntu or any other Linux distro.

However I'm quite confident that you will find that ubuntu will run "out of the box" on your laptop, and that you will not have to worry about installing drivers separately *unless* you want/need the official binary display drivers for gaming, or have a wireless card that isnt very linux friendly for example.

In cases like above you will find yourself installing drivers using the terminal, but there are good writeups offering step-by-step guidance for these situations.

The best thing you can do is to post the model/spec of your laptop here. This way I and everybody else can help you out better.
As I said there is a very good chance you will not have to "install" any drivers at all. IF you do, try not to worry to much.

These forums are packed with people willing to help. :)

---

### Post by 56phil on 2006-11-17
Yes, you would select Linux. However, I doubt that you will need to. Ubuntu will load most of the the drivers automatically. You may need to install a video driver yourself. 

It would help us if you posted more information about your system.

I suggest you start by installing Ubuntu with a dual boot setup. Once you boot the live CD, the installer will give you the option to create a partition for Ubuntu. You should create at least two. One for swap (this should be about 1 to 2 times the amount of memory installed) and one for everything else (make this one at least 2.5GB, more is better). The installer will then resize the existing partition and create new ones as requested.

Two weeks ago, I never heard of Ubuntu. Now, I use nothing else at home. I don't miss Windows at all. The installation process was pretty easy. Most of the questions I had were answered in this forum. If you want a book, get one that is Ubuntu specific. There are enough differences between Ubuntu and other Linux distributions to drive one batty. A good choice is *The Official Ubuntu Book *.

I hope this helps. Good luck.

---

### Post by izvie on 2006-11-17
Yep, Antrix is right, just load it, Ubuntu will likely figure out your PC without anything more than the installation PC.  I have loaded it on 5 PC's and it worked on all of them...some were old Win98 PC's and others were fairly new, like my Compaq P4.  It understood all the video cards.

---

### Post by CatKiller on 2006-11-17
Welcome to the community.

> **crackling said:**
> People were posting snippets of code which I assume is to paste into the terminal, in what situations is installing drivers via terminal necessary?

Don't be scared off by the fact that you'll usually be given instructions as commands to type into the Terminal. There are graphical tools for most things that you might want to do. It's just that command line instructions are far more concise. Instruction on how to use one of the graphical tools might be impossible without pictures, and since the colour, position, style and language of all of them are configurable to some extent, even pictures might not be enough. Whereas a command you can just copy-and-paste from your browser. Job done.

EDIT: Oh, and another reason why it might be useful to be able to configure your graphics driver from the command line is because that might be all you have to fix it with if you do it wrong ;) At least you **can** fix it from the command line, which is possibly more than you can say for other Operating Systems...

---

