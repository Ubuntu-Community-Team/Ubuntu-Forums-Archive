---
title: "installation software"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by ColinP on 2007-02-22
I know I am a learner,  but I have tried several ways to install a Web site copier - with no success.
The 2 main complaints are: Cannot access archive and no such file or directory.   The file  
(httrack_3.33.15-1_i386.deb) is on my desktop.
All help appreciated !

Colin

---

### Post by johnc4510 on 2007-02-22
since it's a deb file, gdebi package installer should install it.
menu>system tools>gdebi package installer

---

### Post by nickoli_02 on 2007-02-22
in a terminal, type

```
sudo dpkg -i httrack_3.33.15-1_i386.deb
```

---

### Post by ColinP on 2007-02-22
Many thanks for your advice. When I open the gdebi installer, the package installer reports : Error: A later version is installed.  So, I have come to yet another big halt !

---

### Post by johnc4510 on 2007-02-22
this means that a new version of httrack is already install on your computer. the 3.33 version your trying to install is an older version. If you open synaptic package manaager and search for httrack, you will see version 3.40 listed. that is if you are using edgy. so, you don't want to revert to an older version of the same software.

---

### Post by ColinP on 2007-02-22
I have already tried the sudo dpkg ...... route - it's was the source of the faults I listed. I have searched for the latest version with Synaptic P.M.  which states that version 3.33 is installed.
Edgy ?  Haven't a clue what that is yet !

---

### Post by ColinP on 2007-02-22
Sorry, forgot to ask.  If the Web copier is installed ; how do I find it, then open the application to use ?

---

### Post by johnc4510 on 2007-02-22
well, edgy is a version of ubuntu. As for your problem, version 3.33 is installed on your system, so the installation of a 3.33 deb package wil not proceed because it is the same version as what you already have installed. a package wil not install over itself if it is the same version or if you have a newer version already installed. In other words, you have the correct version of httrack already on your computer ready to use.

---

### Post by johnc4510 on 2007-02-22
here is a screenshot of the info from synaptic. Please notice at the bottom is a short description and web address of the app., where you should be able to find out all you need to know.

---

### Post by annda on 2007-02-22
> **ColinP said:**
> Sorry, forgot to ask.  If the Web copier is installed ; how do I find it, then open the application to use ?

type httrack in the terminal. if you hit enter/return on the prompt it will tell you all about the options etc.

---

### Post by ColinP on 2007-02-22
I have tried that also !

This is what I get:
"
Press <Y><Enter> to confirm, <N><Enter> to abort
y
Mirror launched on Thu, 22 Feb 2007 21:10:47 by HTTrack Website Copier/3.33-2-nossl [XR&CO'2005]
mirroring [www.stainesramblers.co.uk/bob/bobby](www.stainesramblers.co.uk/bob/bobby) +* with the wizard help..
Done.[www.stainesramblers.moonfruit.com/bob/bobby](www.stainesramblers.moonfruit.com/bob/bobby) (306 bytes) - 404
Thanks for using HTTrack!
colin@colin-desktop:~$
"

So, I ask myself, where is the copy ? How can I look at in my browser ?  Life can be difficult !

---

### Post by ColinP on 2007-02-22
With terminal, this is the response I get:colin@colin-desktop:~$ httrack
"
A cache (hts-cache/) has been found in the directory
That means you can update faster the remote site(s)
OK to Update httrack httrack?

Press <Y><Enter> to confirm, <N><Enter> to abort
y
Mirror launched on Thu, 22 Feb 2007 21:43:31 by HTTrack Website Copier/3.33-2-nossl [XR&CO'2005]
mirroring [www.stainesramblers.co.uk/bob/bobby](www.stainesramblers.co.uk/bob/bobby) +* with the wizard help..
Done.[www.stainesramblers.moonfruit.com/bob/bobby](www.stainesramblers.moonfruit.com/bob/bobby) (306 bytes) - 404
Thanks for using HTTrack!
colin@colin-desktop:~$
"
So, where is the copy ?    I have looked everywhere !

---

### Post by annda on 2007-02-22
if you hit return for defaults it should be in your home directory under websites.

---

### Post by nickoli_02 on 2007-02-22
try 
```
man httrack
```

to find out more info on how to use httrack. Or,

```
httrack --help
httrack -h
```

One of those two should give you a list of command line options and an explanation

---

### Post by annda on 2007-02-22
by the way: if you know the name (or part of it) of what you are looking for, run
```

updatedb
```

and then type

```
locate name_of_the_file_you_are_looking_for
```

---

