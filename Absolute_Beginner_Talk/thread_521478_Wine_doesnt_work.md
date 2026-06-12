---
title: "Wine doesnt work"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-08-09
a very basic question. How does one use wine?
I have say Acroread on say sda1(Win version)
I cd to the directory and run the following:

wine acroread.
and nothing happens.
Can someone tell me how to use it? Do I have to download windows programmes in Linux and then use wine?
Thnx

---

### Post by splintercellguy on 2007-08-09
You have to give it the full name of the file.

---

### Post by thefoolisme on 2007-08-09
Have you installed wine and the programs you wish to run on it?

You might need to read some information regarding Wine.<www.winehq.org>

 There are other programs that read pdfs.  Perhaps you should just use one of those.

---

### Post by wpshooter on 2007-08-09
> **gupta_sumesh63 said:**
> a very basic question. How does one use wine?
I have say Acroread on say sda1(Win version)
I cd to the directory and run the following:

wine acroread.
and nothing happens.
Can someone tell me how to use it? Do I have to download windows programmes in Linux and then use wine?
Thnx

There is an Adobe Acrobat Reader program for Linux.

Why don't you just use that ?

---

### Post by Hospadar on 2007-08-09
Well in general, the usage of wine is ```
wine <filename of executable>
```

With wine, you don't do
wine <command>
you do more like
wine <file>

so for example
wine installer.exe

So if you want to run some program, you have to cd to where the actual executable file is located and run wine on that file, alternatively, you could give wine the fully qualified name of the executable, for example
```
wine "/home/luke/.wine/drive_c/Program Files/your_program/your_program.exe"
```
or wherever the executable happens to be.

Also a little background on wine, when you install things it puts them in the "drive_c" folder in the ".wine" folder in your home directory (which is hidden, go to view->show hidden folders to show it, or just use the command line.  So if you are looking for executables for programs installed with wine, look there.

GL

---

