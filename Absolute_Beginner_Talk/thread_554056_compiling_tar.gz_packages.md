---
title: "compiling tar.gz packages"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by armymedic42 on 2007-09-18
Much to my dismay, Mozilla is incompatible with my online chem homework.  I need to install Netscape, but it only seems to come in a tar.gz download.  How do I unpack and compile these sorts of packages?  Thanx

---

### Post by justin whitaker on 2007-09-18
> **armymedic42 said:**
> Much to my dismay, Mozilla is incompatible with my online chem homework.  I need to install Netscape, but it only seems to come in a tar.gz download.  How do I unpack and compile these sorts of packages?  Thanx

Here you go:

[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

Don't fear the command line on this one. It's actually very straight forward.

---

### Post by armymedic42 on 2007-09-18
I checked symantic and it says i do have build-essential, but everything i seem to try on that site that was recommended comes up with nothing.  Here's what I get:

mark@mark-laptop:~$ pwd
/home/mark
mark@mark-laptop:~$ ./configure
bash: ./configure: No such file or directory
mark@mark-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
mark@mark-laptop:~$ sudo checkinstall
sudo: checkinstall: command not found
mark@mark-laptop:~$

---

### Post by rsambuca on 2007-09-18
You have to start the configure process in the same directory as the files you just downloaded.

---

### Post by kellemes on 2007-09-18
I have the feeling you're not in the right directory when trying to install..
You should be inside the directory where you'll find the "configure"-file that came with the tar.
You can use "ls" to get a list of files in your current directory..

---

### Post by armymedic42 on 2007-09-18
I'm still pretty new to a lot of this stuff, so I think I just tried this in the right directory.  This is what I got:

mark@mark-laptop:~$ ls
BOINC       dvdrip-data             Lab2 Data analysis.odt  navigator
core.22319  Examples                Music                   russ
Desktop     gtk-gnutella-downloads  nautilus-debug-log.txt
mark@mark-laptop:~$ cd navigator
mark@mark-laptop:~/navigator$ ./configure
bash: ./configure: No such file or directory
mark@mark-laptop:~/navigator$ sudo make install
make: *** No rule to make target `install'.  Stop.
mark@mark-laptop:~/navigator$ sudo checkinstall
sudo: checkinstall: command not found
mark@mark-laptop:~/navigator$ 

I also tried doing all that under 'Desktop' and got all the same results.

---

### Post by RomeReactor on 2007-09-18
Hi. Did you download Netscape [from here]("http://browser.netscape.com/")? If so, there's no need to compile; [read here]("http://ubuntuforums.org/showthread.php?t=479975") for how to launch it (just note that the version I link to in that thread is **9.0b1**, which was the current version then--the [newest version]("http://browser.netscape.com/") is **9.0b3**; otherwise, the instructions *should* be the same; I haven't used it since).

---

### Post by armymedic42 on 2007-09-18
Thanx, I went ahead and installed IEs4Linux, and that should work.  Unfortunately, I still don't know how to install a tar.gz download.  Everything I tried according to to every tutorial I have seen just doesn't work.  I must be missing some vital piece of experiential knowledge.  Again, thanx for all the help.  PEACE

---

### Post by PCFascist on 2007-09-18
> **armymedic42 said:**
> Much to my dismay, Mozilla is incompatible with my online chem homework.

What plugin does your chem homework use?

---

### Post by rsambuca on 2007-09-18
No sweat armymedic.  I still think you just weren't in the correct directory prior to typing in the ./configure command.

---

### Post by philinux on 2007-09-18
Not all tar files come with a configure file. Well the one I just tried didn't have one.

---

### Post by stchman on 2007-09-18
> **armymedic42 said:**
> Much to my dismay, Mozilla is incompatible with my online chem homework.  I need to install Netscape, but it only seems to come in a tar.gz download.  How do I unpack and compile these sorts of packages?  Thanx

Firefox is built off Netscape.  It might be one of those rare "IE only sites".

---

