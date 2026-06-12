---
title: "How to install OpenOffice off DVD-ROM?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-02-14
I run Xubuntu 6.10 and have a DVD-ROM with Ubuntu 6.10 and OpenOffice.org 2.0.4 on it.
I would like to install OpenOffice.org Writer off the DVD-ROM, and I want to avoid downloading large files as I'm still on dial-up.
So I have tried to install the archives "Core", "Writer", "Common" and "Base" with GDebi but each time I get an error message "Conflicts with the installed package".
So how the dickens do I install OO.o off the DVD?  How do I go about it, which archives do I install in which order?  Is it even possible to install off the DVD without incurring large downloads?
Thanks!

---

### Post by Blofeld on 2007-02-14
PS:  I'm losing sleep and hairs over this!

---

### Post by stef.s on 2007-02-14
Was OpenOffice not installed as standard with 6.10? It was with my installation, under Application>Office

---

### Post by Blofeld on 2007-02-14
@stef:  Nope.  I installed Xubuntu (note the X!) off a CD-ROM, and that only came with Abiword.

---

### Post by tchoklat on 2007-02-14
You should enable the DVD in your sources, this will allow you to install open office off the DVD. 
 
Use: 
sudo aptitude update
sudo aptitude upgrada
then 
sudo aptitude install oo (if oo is the name of the package  - I am on a windoze PC currently and cannot remember)
 
Tony

---

### Post by Blofeld on 2007-02-14
Thanks, Tony.
But ... when I do that (with Synaptic), and after I have added the DVD-ROM, it tries to download 50 MB just as if the DVD wasn't there.
In particular it tries to download OO.o Core 2.0.4, the same archive that GDebi tells me causes "irresolvable conflicts".
So in essence, I just can't get it to install off the DVD-ROM, GDebi refuses to do it, and Synaptic just happily turns to the internet.
The DVD isn't damaged, by the way.

---

### Post by Crooksey on 2007-02-14
Ok...

If you add the DVD-ROM as a repo, and temporarily disable all of your other repos, it will just install the OO of off the DVD.

---

### Post by Maestro23 on 2007-02-14
Try something like:

> sudo apt-cdrom add
sudo apt-get update
sudo apt-get install <program>

---

### Post by Blofeld on 2007-02-14
Okayyyeee ... I'll give it ONE LAST TRY.
Here's the deal:
* if it works I'll ask for your hand in marriage
* if it doesn't I will take to worshipping the lord of darkness and re-install Windows
So here goes ...

---

### Post by Blofeld on 2007-02-14
@Maestro:  apt-get starts off by tying to download 33 MB ...

---

### Post by Blofeld on 2007-02-14
@Crooksey:  ... looking good ...

---

### Post by Blofeld on 2007-02-14
@Crooksey:  :guitar: Success!! :popcorn:  Ohh ... :KS ... yes! :lolflag: Thank you!

---

