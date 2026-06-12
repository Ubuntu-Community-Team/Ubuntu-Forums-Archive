---
title: "Questions about command line, extracting, etc...."
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by degree on 2005-10-21
Hi, I'm pretty uber1337zorz with windows, but just installed linux on a dual boot system. Much to my dismay, I found out I am super nub and cannot even extract downloads in .deb, let alone find the console (unless that is the terminal....in which case I've allready found it...I just don't know how to use it..). So yeah, if anyone here could walk me through how to unpack files and, if I havent found the console, find it, that'd be great.

---

### Post by Perfect Storm on 2005-10-21
Is it a .deb file you want to install?

sudo dpkg -i XXXXXXXX.deb

XXX =name of the package

---

### Post by aysiu on 2005-10-21
[QUOTE=degree]Hi, I'm pretty uber1337zorz with windows, but just installed linux on a dual boot system. Much to my dismay, I found out I am super nub and cannot even extract downloads in .deb,[/quote] As the first answer to your post suggests, you don't actually have to extract .debs. You just install them. However, most of the time, you don't even need to download a .deb. Just install through Synaptic (see second link in my sig
> let alone find the console (unless that is the terminal....in which case I've allready found it...I just don't know how to use it..). The console is the terminal--you're right. As for how to use it, you just copy and paste commands people tell you to type in... until you understand those commands well enough to use them yourself.

---

### Post by degree on 2005-10-21
The problem is that I try the sudo dpkg -i xxxx.deb thing and it has an error...I would tell you that error if I did not suck and somehow made it so that my console did not open anymore....

On another thread I saw that the guy had the word "Desktop" in the name part of his command line and I was thinking that maybe that was my sudo dpkg.... problem, so I fooled around with some of the settings. Now whenever I try to open the terminal it opens, is black, and then closes. I'm really sorry for sucking.

-edit**
by some miracle I had the terminal open on another workstation and I was able to delete the test profile I made..so the terminal is up and working now. So I'm back to my original problem (plus 1 more)..the sudo dpkg.... thing doesnt work when I try it and I cant figure out how to start the programs I've installed off of synaptic

-edit#2
Here is the error I get btw...

bobby@Bobby-linux:~$ sudo dpkg -i rufus_0.6.5-0ubuntu1_i386.deb
dpkg: error processing rufus_0.6.5-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 rufus_0.6.5-0ubuntu1_i386.deb
bobby@Bobby-linux:~$

---

### Post by kanem on 2005-10-21
[QUOTE=degree]
Here is the error I get btw...

bobby@Bobby-linux:~$ sudo dpkg -i rufus_0.6.5-0ubuntu1_i386.deb
dpkg: error processing rufus_0.6.5-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 rufus_0.6.5-0ubuntu1_i386.deb
bobby@Bobby-linux:~$[/QUOTE]

That probably just means that the folder you were in did not contain the deb package. In the terminal there is still the folder structure you see when browsing through your system. When you open a terminal it usually starts in your home folder. If that's not where you put the deb package you would get that error. So that command (the dpkg -i blah.deb one) has to be run in the folder that has the deb package. If the deb package is on your desktop for example you open a terminal and use the command "cd /home/bobby/Desktop" which moves your location in the terminal to Desktop.

But I strongly suggest to just bypass the whole dpkg thing and use Synaptic as Aysiu said.

---

### Post by degree on 2005-10-21
woo...thanks, I would have never guessed that home directory thing for some reason...

but yeah, i think I'm going to try to stick to apt-get and synaptic as much as I can from now on..thanks for the help though

---

