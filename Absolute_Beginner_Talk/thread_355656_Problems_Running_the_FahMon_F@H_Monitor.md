---
title: "Problems Running the FahMon F@H Monitor"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by euphemism on 2007-02-07
Hi guys, I'm hoping someone here has used the FahMon utility before.

I installed it all the way through the "scons" command, everything working fine, but then when I get to the ./FahMon command to finally run the program, it tells me that no such file/directory exists.  

I went into the FahMon folder to try and figure out where the central utility might've installed to but I've had no luck.

I'm completely unfamiliar with the scons command and what that would've done, my FahMon folder looks more or less the same as when I first downloaded the source.

Any help is greatly appreciated. :)

---

### Post by jvc26 on 2007-02-08
Can you pass up a link as to the instructions you're following for it?
Il

---

### Post by NeilBlanchard on 2007-03-27
Hello,

I'll "graft" onto this thread, if that's alright?  The installation instructions for the Linux version of FahMon start with this:

> To compile FahMon on Linux, you will need:
 - g++ (either 3.x or 4.x)
 - wxGTK >= 2.6.3 (runtime and headers)
 - scons

How does one go about install these three items, in Edgy 6.10 64bit?  TIA

The entire instructions:

> 1) Requirements
---------------

To compile FahMon on Linux, you will need:
 - g++ (either 3.x or 4.x)
 - wxGTK >= 2.6.3 (runtime and headers)
 - scons

If wxGTK is correctly installed on your system, you should be able to execute the command wx-config from any directory:
athropos@ruby$ wx-config --list

Default config is gtk2-unicode-release-2.6
Default config will be used for output
Alternate matches:
  gtk2-unicode-debug-2.6



2) Compilation
--------------

If you have no problem with wx-config, you should be able to compile FahMon:
athropos@ruby$ cd src
athropos@ruby$ scons

If everything went OK, you can execute FahMon:
athropos@ruby$ ./fahmon



3) Choosing the browser to use
------------------------------

FahMon can open miscellaneous webpages for you, but you have to tell it which browser to use. To do that, you will need to define an environment variable named 'BROWSER' that will contain the command to use to launch the browser. For example with bash and firefox:

athropos@ruby$ BROWSER="firefox"



4) Launching FahMon
-------------------

FahMon searches for the images in the current directory. To be able to launch it from any location (e.g., with a shortcut from the gnome-panel), you should write a little script like this one:

--
#!/bin/sh

export BROWSER="firefox"

cd /path/to/fahmon/src
./fahmon
--


---

### Post by NeilBlanchard on 2007-04-06
Hello,

Any help getting these three things?

> To compile FahMon on Linux, you will need:
- g++ (either 3.x or 4.x)
- wxGTK >= 2.6.3 (runtime and headers)
- scons

TIA

---

