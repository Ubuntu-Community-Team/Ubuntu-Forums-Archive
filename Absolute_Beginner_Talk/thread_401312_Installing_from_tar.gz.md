---
title: "Installing from tar.gz?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Browzilla on 2007-04-04
Can someone explain to me how to install a tar.gz?  I'm terribly confused.

---

### Post by v8YKxgHe on 2007-04-04
What is it you're trying to install?

---

### Post by StifflerNewb on 2007-04-04
well the basics are this:

tar -xvzf <filename>.tar.gz [This extracts the files. Like winzip or winrar in windows]
cd <foldername> [This gets you into the folder you just extracted]
./configure or ./config
make
make install

basic way of doing it

---

### Post by Browzilla on 2007-04-04
A media player called Songbird.  
[http://www.songbirdnest.com/](http://www.songbirdnest.com/)

Says it works on Ubuntu.  I have Xubuntu though. It should still work though, shouldn't it?

---

### Post by r4ik on 2007-04-04
Try,

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

Good luck !

---

### Post by Browzilla on 2007-04-04
After I do the ./configure, it says "bash: ./configure: No such file or directory"

---

### Post by russell.h on 2007-04-04
You typically have to compile it. Don't worry though, its tyically not all that difficult.

Download the tar.gz someplace convenient, I like to use my desktop. Right click on it, go down to "Extract Here". This should create a folder on your desktop. If the program is called "program" then the folder might be called "program-1.3.0" or somesuch.

First you are going to need to install some things. Open a terminal window and type in
```
sudo aptitude install build-essential
```
That will install the compiler and some other useful programs for compiling. Now
```
cd Desktop/program-1.3.0
```(except obviously using the name of the folder that was created)
then
```
./configure
```
You will likely get something like "could not find package xyz". Open synaptic, and search for "xyz" (or whatever the name was). Packages tend to come in pairs, the one you want is "xyz-dev" or perhaps it will be called "xyz5-dev" or somesuch. You might have to fiddle with that a bit. Then run teh above command again, and if it gives you a different package, then install that too. Once you are getting no errors then type in
```
make
```
then if that succeeds
```
sudo checkinstall
```(you might have to install checkinstall (sudo aptitude install checkinstall), I can't remember. If checkinstall seems to be running then simply press enter at every prompt until it finishes. Your program should then be installed and ready to go.

---

### Post by aodhon on 2007-04-04
I believe you can install songbird using automatix as well

---

### Post by v8YKxgHe on 2007-04-04
Try this instead of compiling the program from source, which is not something a beginner should be doing!

[http://ubuntuforums.org/showthread.php?t=238328](http://ubuntuforums.org/showthread.php?t=238328)

it may be an older version, though

---

### Post by Bachstelze on 2007-04-04
It ssems this archive contains a precompiled binary, not source code...

---

### Post by Browzilla on 2007-04-04
[QUOTE=russell.h;2401918]
then
```
./configure
```
You will likely get something like "could not find package xyz". Open synaptic, and search for "xyz" (or whatever the name was). Packages tend to come in pairs, the one you want is "xyz-dev" or perhaps it will be called "xyz5-dev" or somesuch. You might have to fiddle with that a bit. Then run teh above command again, and if it gives you a different package, then install that too. Once you are getting no errors then type in


Exactly what I've done so far.  And it still gives me

```
browzilla@masashi:~/Desktop/Songbird$ ./configure
bash: ./configure: No such file or directory
```

---

### Post by Browzilla on 2007-04-04
> **HymnToLife said:**
> It ssems this archive contains a precompiled binary, not source code...

Hey, it does!  I guess I overlooked that.  Thanks!

I knew it wasn't this hard to install last time

---

### Post by sirhalos on 2007-04-04
What is the direct link to the download of this product I was unable to find it on their website to help you.

---

