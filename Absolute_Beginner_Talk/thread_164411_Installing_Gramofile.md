---
title: "Installing Gramofile"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by Gary Nored on 2006-04-22
Total newbie tries for hours to install Gramofile. Downloaded the .deb file and ran it. It returns an error saying it needs fftw2 and fftw2-double. 

So I go off and download lib6-2.3.2.dsl-22sarge3_i386.deb (which is supposed to have both fftw2 and fftw2-double in it). Run it with no errors, so presume ok.

Go back and try to install Gramofile. Same error -- wants fftw2 and fftw2-double libraries. 

OK. I give up! I'll jump through more hoops, if only I know where they are ...

Gary

---

### Post by croak77 on 2006-04-22
apt-get install gramofile

It's in the repo's. Maybe you need to enable universe.

---

### Post by halfvolle melk on 2006-04-22
Hi,
It would sem that Gramofile is in the Ubuntu repositories:
```
jz@bc:~/c$ sudo apt-cache search gramofile
Password:
gramofile - Transfer sound from gramophone records to CD
jz@bc:~/c$ sudo apt-cache policy gramofile
gramofile:
  Installed: (none)
  Candidate: 1.6-7
  Version table:
     1.6-7 0
        500 http://nl.archive.ubuntu.com breezy/universe Packages
```
As you can see the program is in the "universe" repository.

If you haven't already enabled th universe repository type this in a terminal:
```
sudo gedit /etc/apt/sources.list
```
and change this line (yours might look slightly different)
```
# deb http://nl.archive.ubuntu.com/ubuntu breezy universe
```
to this (only remove the hash (#))
```
deb http://nl.archive.ubuntu.com/ubuntu breezy universe
```
and save the file.
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

If you have type this in a terminal:
```
sudo apt-get update
sudo apt-get install gramofile
```
That will also install the fftw2 and fftw2-double stuff you need.

---

### Post by Gary Nored on 2006-04-22
Thanks so much for your help. It worked. At least, gramofile is there, and runs. Will test soon. 

Gary :)

---

### Post by Bob Reid on 2007-08-03
Hi, I am a total newbie to this forum system & computers, so pse excuse any "errors"!
I have d/loaded Gramofile ,using Synaptic - it says it's been loaded but I cannot find where it is to launch etc. I would really appreciate some help on this from anyone.
Many thanks,
Bob.

---

