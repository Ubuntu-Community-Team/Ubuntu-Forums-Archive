---
title: "Comand line help"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Kedster on 2007-09-30
ok iv used ubuntu for like 1.5 mounths but still have the problem of not understanding the codes that i g3et told to use like i installed beryl but the commands were 1 liners or so and i dont understand when there is like 6 lines of code do i copy paste them all and wait or just the first one and the rest r outputs or do them one at a time by coping one pasting one and running one and coping another pasting unother and another runing. please help me

---

### Post by aJayRoo on 2007-09-30
Usually when people on these forums post code it is intended to be executed one line at a time. Code that is meant to be typed in can be differentiated from output by the prompt (usually the dollar sign '$') at the beginning of the line. In other words you usually copy each line and run it in turn. Is there something specific you would like help understanding? It is definitely worth getting to grips with the Linux command line as it is a very powerful tool. Try [this link](http://www.linuxcommand.org/learning_the_shell.php) for some tips on using and getting to know the Linux shell, I know I found it useful as a beginner.

---

### Post by Kedster on 2007-09-30
what would i do for this

Get source:
Code:

```
mkdir kiba-dock
cd kiba-dock
svn co http://svn.kiba-dock.org/akamaru/ akamaru
svn co http://svn.kiba-dock.org/kibadock/ kibadock
svn co http://svn.kiba-dock.org/kibaplugins/ kibaplugins
svn co http://svn.kiba-dock.org/gsetkiba/ gsetkiba
```
 
or this

Code:
```
cd akamaru/
./autogen.sh
make
sudo checkinstall
cd ../kibadock/
./autogen.sh
make
sudo checkinstall
cd ../kibaplugins/
./autogen.sh
make
sudo checkinstall
cd ../gsetkiba/
./autogen.sh
make
sudo checkinstall
```

btw just use "kiba-dock" to run.

---

### Post by fdrake on 2007-09-30
you'll have to copy each line and paste it on the terminal and press enter. for each line. when you 're done you can run the prog u installed by simply writing "kiba-dock".

---

### Post by aJayRoo on 2007-09-30
Okay I just thought about it for a second and realised when people post code the prompt is of course not there! Sorry for any confusion that caused, I was thinking of screenshots of a terminal!

Ok for your example there, each line is a command that needs to be typed in. Do them one at a time. The first set of code does this:
line 1 - creates a directory named 'kiba-dock'
line 2 - change to the newly created kiba-dock directory
lines 3-6 - get the source code for akamaru, kiba-dock, kibaplugins and gsetkiba from the svn repository.

The next set of code has to do with compiling the source code that was downloaded, This is done by moving into the source code directory, configuring the makefile, compiling the package and then building a deb file (debian package) that the package is then installed from.

Each line should be typed in turn after the previous command has finished (assuming the previous command was successful).

---

