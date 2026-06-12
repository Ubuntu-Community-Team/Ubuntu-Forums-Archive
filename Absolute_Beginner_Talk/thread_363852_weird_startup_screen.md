---
title: "weird startup screen"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by alastair560 on 2007-02-17
Okay I've been using Linux for a couple of years but my commandline skills aren't the best, at best minimal.
My friend installed Ubuntu 6 (2.6.15-27-686) on a secondhand Celeron desktop he had donated to me. Everything works fine and so I installed my favourite window manager kde-or kdm? But when I installed kubuntu-desktop and attempted a reboot I got a black screen at login and a smaller white screen in the top left hand corner with my login asrosie@ubuntu. I can't type a command into that wee white box, nor does Ctrl-Alt F1 take me to a commandline. I did manage to reboot by pressing the reset and hitting escape to get me to safe recovery mode.
Here it gets interesting. I got to a commandline and typed startx and got into Gnome where I was able to uninstall kubuntu-desktop and reboot. Same problem happened again but now it gets weirder.
Going into safe recovery mode on reboot and typing kdm gets me nowhere, but typing gdm gets me into kde albeit in safe recovery mode.
I reinstalled kdm on my friend's advice now running kde 3.5.2. I would like to try and resolve this without dragging him away from his own computer but am struggling to know where to start. I can only assume that installing kubuntu-desktop over kdm/kde has corupted something.
Confused

---

### Post by bender5788 on 2007-02-17
Ok lets clarify this the weird startup screen in question is the it the boot splash?
Because although i can probably only be of very little help with more info many other may be able to help you.
Ok but here is what i have interpreted of it if you are not referring to the boot splash (if its even in your version)  then id hazard a guess that you mean the logon screen am i correct??
Also this sounds kind like a graphics issue in the way you describe the first part so try the following command.
```
sudo dpkg-reconfigure xserver-xorg
```
also you could still try to reinstall kubuntu desktop from the command line
```
sudo apt-get install kubuntu-desktop
```
though i dare say you would need to install kubuntu first.... also by ubuntu 6 do you mean 6.06 dapper drake???

---

### Post by alastair560 on 2007-02-17
There is no bootsplash screen until I boot into safe mode and type either startx, which gives me gnome or gdm, which strangely enough gives me kde.
I had uninstalled kubuntu-desktop after this (from gnome) but the same thing keeps happening and now I'm in safe mode the printer, apache, USB support AND the numeric keyboard are all gone (obviously I guess, that's why it's safe mode.)
will try to reinstall kubuntu although someone else from this forum suggested I reinstall gnome and stick to it:-) But I will keep an eye on this forum from my Mandrake laptop and keep you posted.
Thanks for helping, kind of lost out here without all my toys:-)
Alastair

---

### Post by bender5788 on 2007-02-18
Ok attached is an xorg.conf for nvidia but even with an ATI when the x crashes 
just type this command 
```
sudo dpkg-reconfigure xserver-xorg
```bare in mind if it isnt a newish Nvidia  (geforce5 or later) thats this probably will crash your X.
If it is a newish card the command to get it where you want is
```
sudo cp ~/Desktop/xorg.conf /etc/X11/
```
Also just to point out if you have got a Nvidia card even on board you should still run the top command and select the       NV        driver module also whilst your there you may as well check everything else out to spot some weird stuff.

---

### Post by alastair560 on 2007-02-18
Thanks mate, I will look at that tomorow but my problems could be over soon, I've got my mate in the next village who is going to drop by Thursday night and look at it, he's the one who set the system up for me when he donated this computer. It's about four years old by the way. He will hopefully be able to show me what went wrong so as I can document it and post a final reply on this forum.
This has been the weirdest problem I've ever come across with Linux:-) I'll keep you posted though and I've copied out your commands verbatim.
In the meantime, I can still boot in safe mode and do most of the things I need to do, like write my next novel:-) Roll on Thursday.
Thanks for all your help.
Alastair

---

### Post by bender5788 on 2007-02-18
[SIZE=3][SIZE=2]no worries mate sorry i couldn't be of more help although i think i did alright seeing as how ive only been using linux 6 months if you ever need help ive done my fair share of OS killing so i am getting quite proficient at fixing them. [/SIZE]:)
[SIZE=2]Also as a bit of a side note that is at least according to your description probably the weirdest issue ive heard of before as well as it appears to overwriting each each even though they should and normally do install very very separately not to mention the garbage thats been added to your xorg.conf. :confused:[/SIZE]
[/SIZE]

---

### Post by alastair560 on 2007-02-18
And ditto to that as well! I ran Linux on my old laptop for two and a half years prior to getting this desktop machine and broke a few distros. I will keep  you posted though once my mate sorts this problem on Thursday. IMO the best way to learn a system is to break it, otherwise it gets boring.
Have a good hacking week.
Cheers,
Alastair

---

