---
title: "Help:installing Audio Drivers"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by HgBoy on 2007-02-16
I am trying to install the driver for my realtek alc888 HD audio. I have downloaded the driver and unzipped the tar file, but dont know what to do next. I have tried using the readme file, but I have little to no idea how to compile the source code. When i tried on my own i got pages of error messages. please help!!!

---

### Post by true_friend on 2007-02-16
first of all u have to install build-essantial
sudo apt-get install build-essential 
give ur password and let it to install.
after it u may be right for building/compiling the driver. Go to unzipped folder throudh Terminal or open up a terminal there.
first of all when compiling "./configure" command is given without any sudo etc.
it will configure its dependencies may u get some errors of not available packages u may provide that error there for further help.
if every thing is successful next command would be "make" and after make "make install" is last command which installs some package compiled. driver should be installed by this process if there is not a specific way for installing it.
Regards
True_Friend

---

### Post by HgBoy on 2007-02-16
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

is what I get with the ./configure. I have gcc installed, so I'm not sure what is missing.  the readme also explains "Turn on sound support (soundcore module, default turn on)" I dont know how to complete that step either.

---

### Post by HgBoy on 2007-02-17
I have gotten everything to compile, but when i run i run ./configure for the utilities , i get an error message saying a curses library is needed. where could I locate this library?

---

### Post by true_friend on 2007-02-19
Provide out put again of this command may it be helpful.

---

### Post by dvarsam on 2007-02-19
[QUOTE=HgBoy]I have gotten everything to compile, but when i run i run ./configure for the utilities , i get an error message saying a curses library is needed. where could I locate this library?[/QUOTE]

You need to install this package:
[color=blue]libncurses5-dev[/color]

It is available from Synaptic.
Good Luck!

P.S.> Don't forget that you need to redo everything from scratch!!!
Start by re-extracting the folders from the downloaded "[color=blue].tar.gz[/color]" packages.

---

### Post by maryjanua on 2007-09-19
did you ever get this fixed i have that card and i got it solved check this thread out
[http://ubuntuforums.org/showthread.php?t=550753](http://ubuntuforums.org/showthread.php?t=550753)
around page 11 it started getting fixed

---

