---
title: "How to install tar.bz2-files"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by ArnsteinK on 2008-01-14
I'm trying to install Rubryipper, but it wont work. I have followed a few guides, but all I get is this: make: *** No rule to make target `install'. Stop.


What to do?

---

### Post by Nepherte on 2008-01-14
You have to unpack the tar.bz2 file:
```
tar xvfj <tarfilename>
```

---

### Post by ChrisHannam on 2008-01-14
Typically:

tar xvjf filename.tar.bz2
cd filename
./configure
make
sudo make install

This will compile and install your package.

The eror message you are seeing is from "make" as its missing a Makefile.

---

### Post by MONODA on 2008-01-14
try installing Build-essential
```
sudo apt-get install build-essential
```
I have been working on a script to automatically install tarballs, but it is not perfect yet. Visit:
[http://ubuntuforums.org/showthread.php?t=656464&goto=newpost](http://ubuntuforums.org/showthread.php?t=656464&goto=newpost)

---

### Post by ArnsteinK on 2008-01-14
I did that. I tried to do it through the terminal, and then I got this message: arnstein@arnstein-laptop:~/Applications$ tar xvfj rubyripper-0.4.4.tar.bz2
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors


It does say that it's a bzip2 file.

---

### Post by ArnsteinK on 2008-01-14
> **MONODA said:**
> try installing Build-essential
```
sudo apt-get install build-essential
```
I have been working on a script to automatically install tarballs, but it is not perfect yet. Visit:
[http://ubuntuforums.org/showthread.php?t=656464&goto=newpost](http://ubuntuforums.org/showthread.php?t=656464&goto=newpost)

how do I use it?

---

### Post by ArnsteinK on 2008-01-14
I downloaded a new package and started from scratch. Here's the log:

arnstein@arnstein-laptop:~/Applications$ tar xvfj rubyripper-0.4.4.tar.bz2
rubyripper-0.4.4/
rubyripper-0.4.4/rubyripper_22.png
rubyripper-0.4.4/GPL-3.txt
rubyripper-0.4.4/locale/
rubyripper-0.4.4/locale/po/
rubyripper-0.4.4/locale/po/rr_gtk2.pot
rubyripper-0.4.4/locale/po/hu/
rubyripper-0.4.4/locale/po/hu/rr_cli.po
rubyripper-0.4.4/locale/po/hu/rr_lib.po
rubyripper-0.4.4/locale/po/hu/rr_gtk2.po
rubyripper-0.4.4/locale/po/rr_lib.pot
rubyripper-0.4.4/locale/po/de/
rubyripper-0.4.4/locale/po/de/rr_cli.po
rubyripper-0.4.4/locale/po/de/rr_lib.po
rubyripper-0.4.4/locale/po/de/rr_gtk2.po
rubyripper-0.4.4/locale/po/ru/
rubyripper-0.4.4/locale/po/ru/rr_cli.po
rubyripper-0.4.4/locale/po/ru/rr_lib.po
rubyripper-0.4.4/locale/po/ru/rr_gtk2.po
rubyripper-0.4.4/locale/po/nl/
rubyripper-0.4.4/locale/po/nl/rr_cli.po
rubyripper-0.4.4/locale/po/nl/rr_lib.po
rubyripper-0.4.4/locale/po/nl/rr_gtk2.po
rubyripper-0.4.4/locale/po/rr_cli.pot
rubyripper-0.4.4/README
rubyripper-0.4.4/rr_lib.rb
rubyripper-0.4.4/rubyripper_cli.rb
rubyripper-0.4.4/configure
rubyripper-0.4.4/rubyripper_gtk2.rb
rubyripper-0.4.4/rubyripper.desktop
arnstein@arnstein-laptop:~/Applications$ cd rubyripper-0.4.4
arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$ ./configure
/usr/bin/env: ruby: No such file or directory
arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$ make
make: *** No targets specified and no makefile found. Stop.
arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$ sudo make install
make: *** No rule to make target `install'. Stop.
arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$

---

### Post by asmiller-ke6seh on 2008-01-14
> **ArnsteinK said:**
> rubyripper-0.4.4/configure  <---**here's the configure file**
rubyripper-0.4.4/rubyripper_gtk2.rb
rubyripper-0.4.4/rubyripper.desktop
arnstein@arnstein-laptop:~/Applications$ cd rubyripper-0.4.4
arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$ ./configure
/usr/bin/env: ruby: No such file or directory **<--- This is where the error occurs, so **make **and **make install **fail**
arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$ make
make: *** No targets specified and no makefile found. Stop.
arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$ sudo make install
make: *** No rule to make target `install'. Stop.
arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$

Did you install the **build-essential**?

---

### Post by MONODA on 2008-01-14
It is still in development and does not work for tar.bz2 files yet but will soon. Keep an eye on it though. ;)

---

### Post by aeiah on 2008-01-14
as with most things that dont install easily, read the README file. it has the section:

3. HOW TO INSTALL

Dependencies:
* cdparanoia
* ruby-gettext (for translations)

Suggested:
* ruby-gtk2 (for gtk2 gui)
* cd-discid or discid (for proper freedb support)
* eject or diskutil for MacOS (for eject support)
* flac, oggenc, lame (if the codec is wanted)

Run from directory:
(1) ./rubyripper_gtk2.rb or
(1) ./rubyripper_cli.rb

To install:
(1) ./configure --enable-lang-all --enable-gtk2 --enable-cli --prefix=/usr or
(1) ./configure --enable-lang=de,hu --enable-gtk2 --enable-cli --prefix=/usr
(2) make install
The executables will be named `rrip_cli` and `rrip_gui`

To uninstall: (1) `make uninstall`
To cleanup: (1) `make clean`






so, make sure you have the dependencies listed and probably the suggested ones, and then run ./configure with the flags it suggests. ie ./configure --enable-lang-all --enable-gtk2 --enable-cli --prefix=/usr

before doing make / sudo make install

or you can run it straight from your home directory with ./rubyripper_gtk2.rb for a gui version or ./rubyripper_cli.rb for the command line version

---

### Post by asmiller-ke6seh on 2008-01-14
> **ArnsteinK said:**
> how do I use it?

BUILD-ESSENTIAL is the C-compiler stuff, needed to compile your source code. Without it **./configure** makes no sense, and you will be unable to use **make**.

---

### Post by ArnsteinK on 2008-01-14
YEs, I have build-essential.

---

### Post by ArnsteinK on 2008-01-14
Do I have to restart after installing build-essential?

---

### Post by logos34 on 2008-01-14
> **ArnsteinK said:**
> Do I have to restart after installing build-essential?

no.

But read the README, like aeiah posted.

Try running it first directly from the folder:

arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$ **./rubyripper_gtk2.rb**

Anything?  If so, does it recognize the cd?

The critical dependencies for me were 
[B] libgettext-ruby1.8  
libgtk2-ruby[/B]

---

### Post by ArnsteinK on 2008-01-14
arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$ ./rubyripper_gtk2.rb
/usr/bin/env: ruby: No such file or directory

I tried the readme first. And I have the needed packages. Cant I just add some repositories?

---

### Post by logos34 on 2008-01-14
what, is the folder empty or something?

arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$ **ls**

---

### Post by ArnsteinK on 2008-01-14
No:

arnstein@arnstein-laptop:~/Applications/rubyripper-0.4.4$ ls
configure  locale  rr_lib.rb          rubyripper_cli.rb   rubyripper_gtk2.rb
GPL-3.txt  README  rubyripper_22.png  rubyripper.desktop

---

### Post by logos34 on 2008-01-14
odd.  it's all there but won't run configure or the gui.

I'm having my own minor problem with rubyripper.  It installed fine (converted to .deb), but for some reason it refuses to recognize any audio cd I put in--yet it can detect the drive and open/close the tray!  Go figure...

I gave up on it and run EAC on Wine (or Grip with cdparanoia)

---

### Post by ArnsteinK on 2008-01-14
How did you convert it to deb? Can you send that file to me?

---

### Post by wolfen69 on 2008-01-14
1 click install of rubyripper [http://www.getdeb.net/search.php?keywords=rubyripper](http://www.getdeb.net/search.php?keywords=rubyripper)

---

