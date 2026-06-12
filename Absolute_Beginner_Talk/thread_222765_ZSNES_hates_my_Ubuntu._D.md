---
title: "ZSNES hates my Ubuntu. D:"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Sarteck on 2006-07-25
After a fresh install of Ubuntu, I tried using the ZSNES I got through the Synaptic Package Manager, and it kind of worked...  Except that it borked one of my games (SimCity) as soon as I pressed the "Start" button.  XD  I was figuring that it might have been because it was an older version...

So I compiled the newest ZSNES from source (an adventure and a half that taught this newbie a little about compiling, at least).  Great!  I finally get past the Autogen, Make, and Make Install bit with no errors!  Go Sarteck!  Now let's run this puppy...

BZZZZZT!  When I ran it normally, I had some error about not being able to change the resolution to 640 by 480.  When I run it **sudo**ed, my monitor totally blanks and then (after a second or two) totally turns off.  The only key combination that can do anything when this happens is "Ctrl + Alt + Backspace" which logs me out.  D:

I've actually spent a few days looking for the answer to this problem before I decided to post something aobut it...  I'm sure it can't be unique, after all.  But the problem is that I don't even know just what to search for.  XD  Any help would be appreciated.

---

### Post by Metacarpal on 2006-07-25
Odd.  I use ZSNES exclusively (don't like the interface on SNES9X) and never had any problems.  I'll try it tonight with SimCity and I'll let you know what happens.

---

### Post by Metacarpal on 2006-07-26
Just tested my copy of SimCity and it worked without any problems.  I think you may have a corrupted ROM.

---

### Post by gigaferz on 2006-07-26
where do you get zsenes for linux??? will my roms work? (i use those roms on windows..)

---

### Post by Metacarpal on 2006-07-26
Hi gigaferz,

Have you enabled the Multiverse repository for Add/Remove Programs & Synaptic?  If you've enabled Multiverse, then you'll be able to select it in the Add/Remove Programs > Games menu.  It'll be at the bottom.

For help getting the extra repositories set up on your system, [see this post]("http://www.ubuntuforums.org/showthread.php?t=185758")

---

### Post by generalleoff on 2006-07-27
sudo apt-get install build-essential nasm autoconf automake libsdl1.2-dev zlib1g-dev libpng-dev subversion

svn co [https://svn.bountysource.com/zsnes/trunk/](https://svn.bountysource.com/zsnes/trunk/) zsnes

cd zsnes/src

./autogen.sh

make

sudo make install

this will build zsnes from the latest source with all features enabled. I would say if this dose not fix the problem then either yer rom is damaged or something not directly related to zsnes is broken.

---

### Post by cborga1985 on 2006-08-15
I made a package from cvs if anybody wants it.
Filename: [zsnes_cvs20060815-1_i386.deb]("http://www.megaupload.com/?d=8QYHGIZT")
Filesize: 542.09 KB

---

### Post by mcduck on 2006-08-15
..you could also try snes9x. Works great and it's also in the repositories :)

---

### Post by generalleoff on 2006-08-17
the newest version of snes9x that's in the repos (1.42 or 1.43 depending on the package) is 1 year 8 months out of date and is inferior to the version of zsnes (1.42 and 1 year 3 months out of date) that's in the same repo.

you could always grab snes9x 1.5 elsewhere though and it's a real improvement over 1.43. i don't think it is supported by any of the front ends yet though so it's console only.

zsnes svn is definitely the better option right now.

---

### Post by cborga1985 on 2006-08-19
> **cborga1985 said:**
> I made a package from cvs if anybody wants it.
Filename: [zsnes_cvs20060815-1_i386.deb]("http://www.megaupload.com/?d=8QYHGIZT")
Filesize: 542.09 KB

i named the package wrong but this is from svn and it works no problem.

---

