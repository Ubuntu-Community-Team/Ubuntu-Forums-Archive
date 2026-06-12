---
title: "Doesn't ubuntu come with Programming Utilities?"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by dearanna on 2006-02-18
Hey all,

Just wondering, doesn't ubuntu come with a bunch of programming utilities? I can't find them anywhere on the install cd. Do you have to download them, or are they on the CD somewhere, and also, please give detailed explanation on how to install them. I've installed Blender 2.41 already, but now I need a C++ IDE and compiler!! Also Python!!

---

### Post by knalle on 2006-02-18
drop to terminal and try "gcc --version" if gcc is installed you will have a full c/c++ compiler right there. to get a ide try this from the terminal "apt-get install kdevelop" to get the [http://www.kdevelop.org/](http://www.kdevelop.org/) package.

happy hacking!

---

### Post by Michael Steinberg on 2006-02-18
Easiest way to start is to type 

sudo apt-get install build-essential

This will load in many of the compilation tools that got omitted in Breezy.

---

### Post by knalle on 2006-02-18
nice tip!

---

### Post by Brunellus on 2006-02-18
I believe build-essential is on the install CD, but not installed by default.  Pop your CD into your drive, open a terminal, and 

sudo apt-get install build-essential

That ought to get you what you need, at least to start off with.  

Generally speaking, the default ubuntu install is not meant for developers.  From what I have seen/understood, Ubuntu is focused more on the desktop and the average desktop user by default.  Those people who need to develop and compile are presumed to know what to do to get their preferred development environment up.  

The decision streamlines desktop installs with "sane defaults," as the buzzword goes, and the non-inclusion of many packages in the install cd keeps the distro to a single CD, which makes for easier downloads and installations generally.

---

