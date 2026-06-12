---
title: "Making a windows progam in linux?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2007-12-14
Hi,

i came from windows using VB6 which is easy for me.

i switched totally over to linux..

So....
1. Do i install a virtual windows?
2. Languages like python... does python need to be installed for it to work in windows?
3. Make local web pages...

i really want to compile a simple .exe file created to turn this web page into a program..
[http://www.eslgold.com/vocabulary/food.html](http://www.eslgold.com/vocabulary/food.html)

simple.. click a picture and play the file built in without firing up windows media player...

what are your thoughts on making a .exe program,,?

many thanks...

---

### Post by siciliancasanova on 2007-12-14
Well if you're going to be making applications available for Windows users to download I wouldn't rely on any emulation.  Your besting testing asset would be an actual Windows machine.

Local web sites?  Not sure what you're asking here, developing local apps that run in your browser at [http://localhost?](http://localhost?)  Hosting web sites from your local machine on the web?  Developing websites on your machine to be put on a remote server?

---

### Post by CaptainInsaneO on 2007-12-14
If you're going to make a program in Python you need to have Python installed on any computer you want to run that program on.

C++ is a different story though... you should look into that if you want to make .exe's that anyone can run with no extra steps (like installing Python... even though Python is awesome :lolflag:)

---

### Post by hopelessone on 2007-12-14
What GUI type program for making .exe's using C++ in linux?

---

### Post by niteshifter on 2007-12-14
For true cross-platform work I use the MinGW kit: [http://www.mingw.org/]("http://www.mingw.org/").

However if what you're after is to make GUI apps just for Linux, you've got choices, lots of choices. The list below is not exhaustive, just what I use:

VM based: Java, Mono. (well I don't use Mono all that much, 1 VM is enough for me)

Scripted: Perl/Tk, Python/GTK, TCL/Tk .. and many more exist, these are my favorites. 

Binary: GCC (C, C++, Objective-C & more). 

Assembler: NASM

IDEs - there are lots of them also, Google language of chioce and IDE, read up on one, download it and try it. I use the Netbeans IDE myself for Java and C/C++ (supports MinGW). For Python I use SPE.

Also, you're in for a bit of culture shock coming from a Visual Basic background. Opinions on this vary - a lot - but I recommend getting started with Python. First some non-GUI practice, then move to GUI creation, learning to work with toolkit packages (like GTk).

---

### Post by LinuxIsInnovation on 2007-12-14
Ive seen netbeans in linux.. Isnt there some C++ compiler for linux which resembles the interface of Turbo C++ 4.5..??

---

### Post by siciliancasanova on 2007-12-14
> **sayakb said:**
> Ive seen netbeans in linux.. Isnt there some C++ compiler for linux which resembles the interface of Turbo C++ 4.5..??

Netbeans is pretty slick in Ubuntu.  Installs really easy.

---

