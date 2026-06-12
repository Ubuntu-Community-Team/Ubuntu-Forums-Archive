---
title: "Is there any good programming IDE for Linux ?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Alex N on 2007-04-26
I'm sorry, but I am migrating from Windows. I want to set up some useable environment.
Including programming IDE of course. Things that I need from IDE : stability, GUI design,
syntax highlight and good help. On Win I have such IDEs for C++ and PHP - for free.

After installing Ubuntu I tried several proposed IDEs. The result is :

Anjuta IDE - crushes
Monodevelop - weird GUI designer, crushes
etc.

Also I'd like to have the same IDE and interface library for Win and Linux. (GTK?)
It would be nice to be able to add comments in my language (Russian)

---

### Post by ubuntu27 on 2007-04-26
Here is the Programming Forum: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

You may want to read ["What's your Favorite IDE?"]("http://ubuntuforums.org/showthread.php?t=6762") thread

Anything related to programming should be posted into the [Programming Forum]("http://ubuntuforums.org/forumdisplay.php?f=39"). :) 


Good luck!

---

### Post by igknighted on 2007-04-26
Anjuta is a good program, I would bet you're install is broken.  Also check out Kdevelop, its KDE but the best there is.  Also Eclipse is nice.  Most linux users use Emacs/Vim or another editor (kate/scite/gedit) and the CLI to debug/compile.  These editors have advanced features like code folding, syntax highlighting and (i believe) even code completion.  Try them out.

I recommend KDevelop.  It is the most complete package available and integrates well with Quanta+ if you do web development too.  I would recommend using qt4 for your library, as there are windows versions of it as well, and it is incredibly versatile.  GTK is also a nice option.

---

### Post by dubrict on 2007-04-26
I can't seem to find an IDE that will tell you what arguments a function your typing can take.

For example, if I were typing  list.fill(  It would be nice if it would pop up with a little information, like ( iterator start, iterator stop, T element ).

I've seen it in all sorts of IDE's just not any of these ones.

---

### Post by Kenji Mapes on 2007-04-26
> **ubuntu27 said:**
> Here is the Programming Forum: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

You may want to read ["What's your Favorite IDE?"]("http://ubuntuforums.org/showthread.php?t=6762") thread

Anything related to programming should be posted there. :) 


Good luck!

I was interested in this as well.  Thanks for the links 27!:)

---

### Post by spamalot on 2007-06-19
tried anjuta, kdev and eclipse. 

the last one worked best for me and seems to have wide support e.g. [http://www.research.ibm.com/eclipse/](http://www.research.ibm.com/eclipse/)

---

### Post by psusi on 2007-06-19
The best IDE ever is emacs.  It has every feature including the kitchen sink.  It integrates with the compiler and debugger to view the source where the error is/is currently executing.  It can use tags tables to quickly warp you to the definition of a function with a single keystroke, or jump across every instance where that function is called.  It can browse the classes and their members in another frame.  It can do on the fly compression/decompression to access compressed files.  It can even let you directly edit files within a .tar.gz.  It also has a very powerful regular expression searc/replace function, and generalized scripting in lisp, and much, much more.

As an example, the other day I had a header file with about 100 #defines in it that defined macros referencing elements of an array.  Over time I had stopped using and commented out several of them, so I wanted to get rid of the obsolete #define and renumber the rest to save space in the array.  Doing this by hand would have been very tedious, but with emacs I whipped up a 5 line script in about two minutes that scanned for all of the #defines, removed the ones with leading //, and renumbered all of the indecies.

Later I had a C file with several definitions for arrays of strings that a coworker wanted broken out into several excel spreadsheets, one for each array.  It took me one mouse click, and two keystrokes to select one of the arrays, a few more characters of regular expression to match on the quoted text, and another regular expression to replace with, and I had a series of lines of text on the clipboard to paste into excel without the ""s and ,s and leading tabs.  Revering the transformation after my coworker modified the spreadsheet and asked me to update the code to match was just as easy.  Took me all of 15 seconds to update the C with some dozen or two changes he had made to the spreadsheet.  

It is fully self documenting, but because it can do so much, it takes a good deal of time to study the full manual and learn how to use it, but once you do, emacs is incredibly powerful.

---

### Post by vinceZZZZ on 2007-06-19
Hello forum people,

i don't know if you are interested...but there is a CODELESS programming tool for making windows software.

This tool will work on Linux through WINE......because WINE allows the .NET framework of Msoft to be installed.

THis tool is called LIMNOR...

it is totally CODELESS.....and takes about 10 minutes to learn to completely windows program.

a child could learnt to use it in about 10 minutes....you can make all manor of software using Limnor....and even plug in special .NET tools that you require.

SHould you require any teaching of Limnor....i will teach yo for FREE in a few emails.....

just email me.....with your questions.....after you ahve read the first TUTORIAL inside limnor....

teh only thing to really learn is where to put VARIABLES in your designs....

just ask anything....and i can teach you everything in about 2 emails...

[email]b1enjamin_turnbull@yahoo.com[/email]

it is a great programming tool....it is very powerfull and SIMPLE to use...there is NO LANGUAGE involved...just shapes and performers and actions....

a genius tool....really...

Vince

---

