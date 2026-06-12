---
title: "Problem installing tcl/tk"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Aninha on 2007-06-17
I have no idea how stupid a question this may be, but I really don't know how Linux really works. I have worked with Windows all my life, so if you can give me an answer, please use small words :)

I wanted to install aMSN (an open source msn) on my computer. It went quite well, untill it said: "Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 7.04 (apt-get) to install a package with similar name to 'tcl'."

I tried in cli the command apt-get install tcl, but then it asked me all kinds of question I didn't know how to answer, really

So I went to the troubleshoot page of the program in question and was redirected to the download site for this tcl/tk. There it said that normally this is auto-installed and if this is not the case you download it here, and it was in some kind of .tar.gzip format. So I think it's some kind of zipped files-package. I download and save, and then unpack it. here's where it all stops making sense on my part: I thought it was going to be an executable file but instead I get a whole lot of files I don't know anything about and a read-me file I really can't make out, because it's telling me to type some type of command in some type of tcl/Unix directory, which I can't find anywhere (or at least don't know whta it is).

So if anyone has a solution, or even better, an easier way to get these things installed, I would be very grateful,

Aninha

---

### Post by mikeypc2006 on 2007-06-17
I'm having the same problem with TLS, the aMSN wizard can't download it and like the above poster, now that I've manually downloaded the files, I've no idea what I'm supposed to do with them!

---

### Post by Aninha on 2007-06-17
Owkay, I got a little further already, but am not quite there yet.

So, apparently, when you open de READ ME file in the bottom you can open a shell, where you have to type in these commands. All right.

So it asks me firt to typ "./configure", then "make" and then "make install". I do it all in the right order, but with the last command it says:
"Installing libtcl8.4.so to /usr/local/lib/
cp: cannot create regular file `/usr/local/lib/#inst.24592#': Permission denied
mv: cannot stat `/usr/local/lib/#inst.24592#': No such file or directory
chmod: cannot access `/usr/local/lib/libtcl8.4.so': No such file or directory
make: *** [install-binaries] Error 1"

So apparently I didn't make something and I think it's the problem is in step 2 cause normally the "make" command would  create a library archive called "libtcl<version>.a" or "libtcl<version>.so" and an interpreter application called "tclsh" that allows you to type Tcl commands interactively or execute script files. 

So how do I fix this?

A.

---

### Post by mikesignguy on 2007-06-17
before the commands did you type "sudo" ... super user do... and then the password?

---

### Post by Free Penguin on 2007-06-18
[www.freepenguin.it/tip8.html](www.freepenguin.it/tip8.html)   it's in italian but i think you can simply understand

---

### Post by TedGarvin on 2007-10-11
Same problem here.  The installer doesn't work at all, when I try ./configure while in the directory, I get a message "file not found".  The Italian page didn't help. It's ruining my self-esteem ( the real purpose of Linux ), so I'm installing Kmess and Kopete.  I hate to give up, but this time, the hunt is not worth the reward.

---

### Post by quinnten83 on 2007-10-11
I'm not at home, so I can't check.
But i think what you are trying to do no is compile from source.
The TCl/tk problem is something else.
In the TCl/tk file there is a reference somewhere that says 1.5 instead of  1.50.
once that is fixed aMSN usually works.
I don't remember exactly what to do, cause I have all that information @ home, and right now I am @work.
Will check later.

---

### Post by quinnten83 on 2007-10-11
Here we go:
> Q: I have installed TclTLS but it still complains about not finding it

A: Are you using Tcl/Tk8.5 ? See the instructions above about symlinking

Q: I have installed TclTLS but it still complains about the version

A: Please edit pkgIndex.tcl (in:/usr/lib/tls1.50/)so that this line

 package ifneeded tls 1.5

becomes like this

 package ifneeded tls 1.50

(just add the zero) 

from 
[http://www.amsn-project.net/wiki/TLS]("http://www.amsn-project.net/wiki/TLS")
try and see if thatworks

---

