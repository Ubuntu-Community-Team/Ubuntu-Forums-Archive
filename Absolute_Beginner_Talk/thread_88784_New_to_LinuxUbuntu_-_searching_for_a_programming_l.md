---
title: "New to Linux/Ubuntu - searching for a programming language ....."
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by Rykhaard Damian on 2005-11-11
I do hope that I haven't missed any answers that ARE on the site, here, that would help me in my quest.  :o
I've been searching through here for about the past 90 minutes, for a any link to some place from which I could download the Python programming language, that I could program with under Ubuntu 5.04 (soon to be 5.10).
A couple of hours ago, I decided to start searching here for a version fo the Basic Language to program in, in Linux, but almost immediately saw references / praise in regards to the Python language.  Seeing some examples of it's code, and more praise, I'd very much like to take a whack at working with it! :)

Other info:  I've programmed in many variations of Basic, since 1982, on many different computer types.  I've never come anywhere near to being professional at it, but I've usually gotten to where I wished to get, with my software. ;)

Part of my reason for coming to Linux, this week - were for the Terminal aspect; simplicity; quickness in things.  Attached to that - my desire to start programming music software (to use with my modular synthesizer that I'm building), in a non-GUI text only format.  (As well as a desire to conver Numerology software (functionality wise) that I wrote in Visual Basic .Net, to pure text format.

So NOW - my desire, is to find a source of Python, that I can happily work with in Ubuntu. :)  (Teaching myself how to work with Python, as well. ;) )

Would anyone know, where I could grab, from?  I've searched for "Python +Linux" through Google as well, as at Soundforge.  Perhaps I missed links, due to almost falling asleep - the final reason being why I'm typing this.  I've probably missed something somewhere but ......

Any help would be grandlee appreciated. :)

Ryk

---

### Post by kont.raen on 2005-11-11
[QUOTE=Rykhaard Damian]I do hope that I haven't missed any answers that ARE on the site, here, that would help me in my quest.  :o
I've been searching through here for about the past 90 minutes, for a any link to some place from which I could download the Python programming language, that I could program with under Ubuntu 5.04 (soon to be 5.10).
A couple of hours ago, I decided to start searching here for a version fo the Basic Language to program in, in Linux, but almost immediately saw references / praise in regards to the Python language.  Seeing some examples of it's code, and more praise, I'd very much like to take a whack at working with it! :)

Other info:  I've programmed in many variations of Basic, since 1982, on many different computer types.  I've never come anywhere near to being professional at it, but I've usually gotten to where I wished to get, with my software. ;)

Part of my reason for coming to Linux, this week - were for the Terminal aspect; simplicity; quickness in things.  Attached to that - my desire to start programming music software (to use with my modular synthesizer that I'm building), in a non-GUI text only format.  (As well as a desire to conver Numerology software (functionality wise) that I wrote in Visual Basic .Net, to pure text format.

So NOW - my desire, is to find a source of Python, that I can happily work with in Ubuntu. :)  (Teaching myself how to work with Python, as well. ;) )

Would anyone know, where I could grab, from?  I've searched for "Python +Linux" through Google as well, as at Soundforge.  Perhaps I missed links, due to almost falling asleep - the final reason being why I'm typing this.  I've probably missed something somewhere but ......

Any help would be grandlee appreciated. :)

Ryk[/QUOTE]


Hi Ryk,

to be honest I don't know what you are exactly after, i.e.  what your definition of "source" is, but if you are in need of an introduction into python or something the like, you could try [www.python.org]("http://www.python.org").

If you are looking for the python interpreter and the related packages, you should try searching for pyhton in synaptics (see also : how to install additional software in ubuntu) and install the desired packages out of the query result.

I hope I could help you with that :)

---

### Post by pitr on 2005-11-11
Python is already installed and ready for use on a normal Ubuntu installation. 

If you are familier to programming then I suggest you download dive into python and read it for some good references on how python works. You can find this book using synaptic (think the package is called diveintopython but I'm not sure). 

If you are looking for source for python application then go to sourceforge.net and search projects that uses python as a language.

---

### Post by michael_salcher on 2005-11-11
just type "python" in terminal the interactive python interpreter starts. otherwise write your python code in a file, give it a the following "she bang" line (first line in the file:

#!/usr/bin/env python

save the file. make it executable ("chmod a+x foo.py", where foo.py is your python source code file) and run it with "./foo.py" (mind the "./")

---

### Post by Rykhaard Damian on 2005-11-11
Hey all. :)

Many thankyous for the help / suggestions from all of you! :D

FIrstly - I'm sorry, Kont.raen for typing somewhat unclearly.  :( I was quite tired, and should have gone to bed, instead, but - the excitement of a new language (to me) to program in, and finding an interpreter of it, kept ..... 1/2 awake, instead of falling asleep.  LOL

What I WAS looking for, and thanks to input from you chaps, was a Python interpreter (that I NOW know, is built INTO the Ubuntu and Mandrake 8.1 releases of Linux).
That - takes care of searching for it, as there's no need.   It's right here. :D  Yay!

I'm looking to write / convert couple of programs, using Python under the Linux OS:

1 - a basic MIDI sequencer (Musical Instrument Digital Interface) that would allow me to play electronnic musical instruments, from my computer.

2 - conversion of code that I'd written in Visual Basic .Net, for doing Numerology, into Python code. (Numerology translates names/etc. into a numerical value, with interpretations for each # / by translating, I don't mean direct translation from Basic to Python, but only the 'functionality'. With the seeming similarities between Basic and Python, I should be able to do a fair bit of 'cut and paste' it looks like. :) )

In searching online just now for any potential MIDI source code in Python, I DID find mention from one person, that Python may not be 'fast enough' to handle working with MIDI instruments in realtime. (They communicate at just over 30,000 baud). Mmmm. Minor concern there, but I'll hopefully figure it out. 
I'm hoping that I wont have any troubles here, as I don't intend to deal with any GUI contraptions for the software. Just pure, text. That should cut down any system's overhead or anything, required. 
At the very least - if I'm able to get my PC to spit out at least 2 individual sources of 'timing pulses' from SOME port in the PC (Parallel port could work fine), for controlling external gear - I'll be doing alright. 

Pitr / Michael - thank you grandlee for just pointing out, that I can type 'Python' in the terminal! I was happy as heck to find that it's BUILT IN! :D 
I went and downloaded 'Dive Into Python' and unzipped it into it's own directory.
And with all of the source code available all over the place on the net - I shouldn't have any troubles teaching myself how to work with Python. 

K.  Sorry for typing an encyclopedia at y'all. :o

Someday - I hope to be able help others here, as well.  Much-o to learn. :)

Ryk

---

### Post by crazedgremlin on 2006-11-30
[http://en.wikibooks.org/wiki/Non-Programmer's_Tutorial_for_Python/Contents]("http://en.wikibooks.org/wiki/Non-Programmer's_Tutorial_for_Python/Contents")

here's a good introduction to python

---

