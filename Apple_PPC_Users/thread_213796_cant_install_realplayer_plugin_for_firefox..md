---
title: "cant install realplayer plugin for firefox."
date: 2006-07-11
forum: Apple PPC Users
---

### Post by macgig on 2006-07-11
what am I doing wrong? its on the desktop. it's a executable file. double clicking dont work. run command dont work. :confused: :confused:

---

### Post by Titus A Duxass on 2006-07-12
Try using automatix, it does what it says on the tin!

---

### Post by macgig on 2006-07-12
what is that? where do I find it? sorry, im new to linux.

---

### Post by 3rdalbum on 2006-07-13
When you say "the run command doesn't work", exactly what about it doesn't work? Does it ignore the command, or does it give some kind of error message, and if so what message?

The first thing that comes to mind is that the file may not have Execute permission. Right-click on it (F12) and go to Properties. Click the Permissions tab, and then check all three Execute checkboxes. Now, running the program through the terminal should work.

As far as Automatix goes, there are good instructions here:

[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

---

### Post by macgig on 2006-07-13
didnt work. get this error. 

 ./RealPlayer10GOLD.bin
bash: ./RealPlayer10GOLD.bin: No such file or directory


the file is on the desktop. Im looking at it. 

Im going to read the link you putt up. thanks. :)

oh, installing automatix like someone suggestion didnt work either. ](*,)

---

### Post by macgig on 2006-07-13
tried something else, now I get this

 ./RealPlayer10GOLD.bin
bash: ./RealPlayer10GOLD.bin: cannot execute binary file

---

### Post by macgig on 2006-07-14
I sure wish this came with the default live cd download... for the life of me I cant install it. :-k

---

### Post by RRS on 2006-07-14
Add this line to your sources list:

```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

Then; "sudo apt-get update" and you'll be able to install Realplayer 10 with synaptic.

---

### Post by avtolle on 2006-07-14
The reason that difficulty is being incurred with installation of realplayer seems to be related to the fact that the version available is not for ppc. If you find differently, please let us all know. I cannot install it from the commercial repo, the message being essentially that maybe my architecture is not supported. I have a g4 Cube, and have come to the conclusion (after messing around with the commercial repo and visiting the real.com site) that the binary the OP and others are trying to install is for x86 only.

---

### Post by macgig on 2006-07-14
not sure what a sources list is, but I will try this tonight. if it works or dont, I will report back here. 

btw, I have a G4 sawtooth tower.... os x 10.3.9 on it. if that matters..

---

### Post by gThree on 2006-07-14
Yup, like Flash, no Real player for PPC (that I"m aware of).  MPlayer and MPlayer Firefox plug-in can handle some Real media ... not sure what the limits are.

Makes you appreciate open formats ....

---

### Post by macgig on 2006-07-14
hmm, sounds like im sol as they say. :confused: 

is it possible that linux suffers from the same problems the mac had for years... little or no software? 

I doubt I'll ever go to linux as my main os... as I like OSX alot.... seems that linux does have many limitations? :???:

---

### Post by avtolle on 2006-07-14
macgig: if you're feeling adventuresome, you can go to real.com, navigate around to the "Helix archives" (I recall), and dl the "experimental" installer for realplayer as shown on the table under ppc. I haven't the time nor ability to mess w/it right now, so if you decide to proceed, let us know how it comes out. It also appears that the source code is also available there for a dl and self-compilation.

---

### Post by kadymae on 2006-07-15
> **avtolle said:**
> The reason that difficulty is being incurred with installation of realplayer seems to be related to the fact that the version available is not for ppc. If you find differently, please let us all know. I cannot install it from the commercial repo, the message being essentially that maybe my architecture is not supported. I have a g4 Cube, and have come to the conclusion (after messing around with the commercial repo and visiting the real.com site) that the binary the OP and others are trying to install is for x86 only.

Yup, that would be the problem.  It is **x86** only.

---

### Post by kadymae on 2006-07-15
> **macgig said:**
> hmm, sounds like im sol as they say. :confused: 

is it possible that linux suffers from the same problems the mac had for years... little or no software? 

I doubt I'll ever go to linux as my main os... as I like OSX alot.... seems that linux does have many limitations? :???:

It's not that Linux have a lot of software, but when you're on PPC it's that a lot of frelling companies can't be bothered to put out a PPC port of the Linux software they release on x86.

](*,)

---

