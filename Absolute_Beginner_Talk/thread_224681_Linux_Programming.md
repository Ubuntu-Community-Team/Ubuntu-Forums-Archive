---
title: "Linux Programming"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by drpepper on 2006-07-28
Hey everyone

I've been programming in windows for a while now, VB, Delphi, C++ etc. I'm at a total loss as how to create programs in linux. Is it the same coding, but different compiler for each os platform? 

Thanks :)

drpepper

---

### Post by s_h_a_d_o_w_s on 2006-07-28
for c++:

get g++, the c++ compiler in the terminal
[COLOR=Lime]
sudo apt-get install g++[/COLOR]

then write your code in gedit or whatever and save it a .cpp .

then :
[COLOR=Lime]
g++ /path/to/source.cpp[/COLOR]

to execute

[COLOR=DarkOrchid] ./a.out[/COLOR]

---

### Post by Kurt` on 2006-07-28
Well, you're not going to compile Visual Basic on Linux. :p 

For C++, you can use the compiler g++. You will have to:

# sudo apt-get install build-essential

to install all the necessary items.

Then to compile a C++ program, you simply run this:

# g++ file1.cpp file2.cpp -o filename

Then you can run it via:

# ./filename

As for Delphi I have no clue, but...

There is also a programming-related section on the forums where you can ask any questions you have. [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by jdbartlett on 2006-07-28
I also recommend learning a scripting language. They're handy for metaprogramming, prototyping, web dev, as well as for doing all those repetitive every-day jobs for you! Popular scripting languages are Perl, Python, and Ruby. Perl is an older scripting language and pretty much ubiquitous. Python and Ruby are newer (Ruby is just over a decade old now) but are friendlier (especially Ruby) and come pre-installed on many Linux distros.

---

### Post by Lord Illidan on 2006-07-28
As for delphi, I know of the freepascal project. There is also lazarus.

---

