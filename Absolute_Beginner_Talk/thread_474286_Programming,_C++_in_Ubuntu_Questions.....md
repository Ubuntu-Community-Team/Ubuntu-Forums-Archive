---
title: "Programming, C++ in Ubuntu Questions...."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by OhioYJ on 2007-06-14
Ok I used to do a fair amount of C++ programming, I'm trying to get back into it some. 

I've installed Anjuta, and Eclipse, and I get basically the same error message in both programs, with even a simple "Hello World" program.

> The target executable does not exist for this Project.

I'm sure I'm overlooking something simple?

---

### Post by freebird54 on 2007-06-14
Sounds like a command line error to me - but I haven't worked with this setup yet either :).  Or you using make, or compiling and linking separately?

---

### Post by OhioYJ on 2007-06-14
So far I've just been using the Build, Make, and Compile options in the Build menu of Anjuta. 

Then using the "Execute" option in that same menu.

---

### Post by hyper_ch on 2007-06-15
is the files being chmodded as executable?

---

### Post by ecs_pf5 on 2007-06-15
I am a definite newbie so I'm not going to be that much help.

However, I pretty much randomly ran down the list of options in the build menu, and saw that the only option I could not get to report success was 'Build Distribution'.

After randomly monkey-bashing all the other build menu options, I got the following output in a terminal after pressing the 'execute' option:

```

EXECUTING:
/home/user/Projects/hotdog/src/hotdog 
----------------------------------------------
Hello world

----------------------------------------------
Program exited successfully with errcode (0)
Press the Enter key to close this terminal ... 

```I had selected a Gnome 2.0 project, and had called it hotdog.

Hope it gives you some kind of hope, anyway :-?

[http://sourceforge.net/forum/forum.php?forum_id=44932](http://sourceforge.net/forum/forum.php?forum_id=44932) might have some help

---

### Post by OhioYJ on 2007-06-15
Thanks for the help so far.

This helped get rid of the errors with the Compile with Make option.

> sudo apt-get install build-essential

So now in my src directory I have an main.o and a main.cc files?

However I still get:

> The target executable does not exist for this Project

I open to suggestions, even if its another program that would work for creating simple programs?

---

### Post by OhioYJ on 2007-06-15
Ok I can Compile, and Compile with Make, but I can NOT do the Build option. I get this

> make: *** NO targets specified and no makefile found. Stop.

Completed... unsuccessful.

---

### Post by bvanpelt on 2007-06-15
main.cc is your source file. main.o is the compiler output created by compiling main.cc. main.o is an intermediate file and is not itself executable. It has to be linked (possibly with other .o's and libraries) to create the linker output file. This file is (when no other name is specified) named a.out.

From what you've described so far I don't think you are providing make enough info so that it can link your .o's and libraries together. The fact that make sees nothing to do is a clue.

Brooks

---

### Post by OhioYJ on 2007-06-15
> From what you've described so far I don't think you are providing make enough info so that it can link your .o's and libraries together. The fact that make sees nothing to do is a clue.

What would I do to fix this? Even when I "make" the main.cc file in the terminal window, I get main.o is up to date. But it won't build or execute?

---

### Post by bvanpelt on 2007-06-15
I haven;t used make in about 10 years, so this will be brute-force. Post your make file so we can see it. You should have a file called main.mak (or ??? .mak) somewhere; post it. Clearly your .mak file has no target for a link - it only seems to have a target for .cc files...

---

### Post by ecs_pf5 on 2007-06-15
> 
I open to suggestions, even if its another program that would work for creating simple programs?


Are you bothered about using a particular language, and do you specifically want to create GUI apps?

I found plain gcc really straightforward for just producing simple C programs for terminal / console use. Had some success using it to compile C code that called GTK directly to produce a small GUI app, unfortunately I'd be completely unable to retrace my steps

There are a couple of BASICs that look quite handy.. unfortunately they seem a bit harder to use on 64-bit so I've kinda gotten a little bogged down with them. Gambas, REALbasic? 

Gambas - never tried it as it won't run on my 64bit machine :(

Carl Gundel over at LibertyBASIC keeps promising to release LIbertyBASIC 5 for Linux but I'm not sure how far along he is with that at the moment - but the Windows version was incredibly easy to use

REALbasic looks excellent but the super duper version is not free-beer. It will spit out 3 different executables on the one compile run, one for Linux, one for Mac, one for Windows..... so it says on the tin..

Python/IDLE/wxPython and monodevelop (for dot net) look quite good.. although I haven't really done more than scratch the surface of either (they both seem to require runtimes / virtual machines on the target platform though, I might be mistaken there)

Not a great deal of help I know but maybe there's something you can pick up on

---

### Post by kott on 2007-06-15
and what happened?

---

### Post by OhioYJ on 2007-06-15
Ok I have two make files in that folder. My program called Test7868,

This one is in the src folder of that project, with the source code:

> ## Process this file with automake to produce Makefile.in

## Created by Anjuta - will be overwritten
## If you don't want it to overwrite it,
## 	Please disable it in the Anjuta project configuration

INCLUDES = \
	$(PACKAGE_CFLAGS)

AM_CXXFLAGS =\
	 -Wall\
	 -g

bin_PROGRAMS = test7868

test7868_SOURCES = \
	main.cc

test7868_LDFLAGS = 

test7868_LDADD =  \
	$(PACKAGE_LIBS)

The other one is in the main folder of Test7868

> ## Process this file with automake to produce Makefile.in
## Created by Anjuta - will be overwritten
## If you don't want it to overwrite it,
## 	Please disable it in the Anjuta project configuration

SUBDIRS = po src

test7868docdir = ${prefix}/doc/test7868
test7868doc_DATA = \
	README\
	COPYING\
	AUTHORS\
	ChangeLog\
	INSTALL\
	NEWS\
	TODO

EXTRA_DIST = $(test7868doc_DATA)

gnomemenudir = $(prefix)/@NO_PREFIX_PACKAGE_MENU_DIR@/Applications
gnomemenu_DATA = test7868.desktop

# Copy all the spec files. Of cource, only one is actually used.
dist-hook:
	for specfile in *.spec; do \
		if test -f $$specfile; then \
			cp -p $$specfile $(distdir); \
		fi \
	done

---

### Post by OhioYJ on 2007-06-15
Ok got it figured out, I had also posted this on the Anjuta forum as well. Here is what fixed it for me, for anyone following along, or having the same problem. Thanks for the help as always!

> Thank you very much, got it working!

The option is actually "Auto Generate" in the build menu. Then I got a bunch of errors, but all those errors where a list of libraries and dependencies that I needed. So I just started typing in the files it wanted into the Synaptic Package Manager, installed them, and its all up and working!

Now time to start doing some reviewing, its been a couple years since I last wrote some code.

---

