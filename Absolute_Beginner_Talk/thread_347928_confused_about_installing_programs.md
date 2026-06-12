---
title: "confused about installing programs"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by jim-in-utah on 2007-01-28
I am completely new to Linux; I have been using Ubuntu (Dapper Drake) for about a month, and for most of that time I have been trying to get one small program to install and run.
I recieved a Sony e-book reader (PRS-500) for Christmas, and found that it would only run on Windows XP, a downgrade I didn't want to make (from Windows 2000). I found on the net that there was a program to use it in Linux, called prs500, so I installed Ubuntu and tried to install prs500.

 I downloaded the program (a"python egg"), but couldn't figure out how to install it. The  site I got it from said to use easy_install, so I downloaded that and couldn't install it either. Then I noticed that it required Python2.5, and I only had 2.3 or 2.4, so I downloaded that and couldn't install it. Then I stopped and read a book on Ubuntu and found out I needed to install build-essentials before I could install anything else. I found that on Synaptic Package Manager and installed it, and then I managed to install Python2.5, and then I installed easy_install. That wouldn't download prs500 because the site wasn't a "standard url"-- it started with https instead of http -- but I managed to get it to use the copy I had already downloaded, and managed to install prs500 and get it to connect to my PRS-500. I thought I had finally succeeded after a month of frustration.

 But not so -- it turned out that the gui needed something called PyQt version 4 something, which needed Qt version 4 something. I downloaded Qt4.22 and thought I had that installed -- at least the make command ran for almost 4 hours, and make install seemed to work also. I downloaded PyQt 4.1.1, and tried to install that. At first, configure said it needed SIP, so I downloaded that and installed it. Then PyQt said it couldn't find qmake ("Error: Failed to create ./qtdirs Make sure you have a working Qt v.4 qmake in your PATH or use -q to explicitly specify the location of a working v.4 qmake") . I assume that is part of the Qt I installed. I ran whereis and it said qmake was in usr/bin/qmake and in usr/X11/bin/qmake. I tried using -q with each of those but got the same error. 

I don't know what to try next. It seems this is a lot of work to run one little program, I'm almost desperate enough to buy XP :(  Can anyone help me to get this working?

---

### Post by taurus on 2007-01-28
Do you intend to install Ubuntu on that machine?

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by jim-in-utah on 2007-01-28
No. Actually, I understand the e-Book itself uses Linux internally. But what I'm talking about is the program I need on my computer, to add and remove e-books from the reader.

---

### Post by Titi on 2007-01-28
hey, i had the same kind of frustrations when i started with ubuntu. i guess in the beginning, you have to install a lot of stuff before being able to install the programs you really want. but after a while when you run another configure file: "checking for blahblah", you'll say: yes, got that! those are the glorious moments :)
i guess this is not much a help for this particular problem, but believe me, things will get easier in the future...

---

### Post by atihimself on 2007-01-28
most of the time installing goes like this...
sudo apt-get install blah-blah
OR...
./configure
make 
make install/checkinstall
but I think you know it allready

another good command vhat I discovered lately is ...
sudo apt-cache search blah-blah
finds everything you need and you don't have to google the whole net

---

### Post by enixon on 2007-01-28
Is it possible to install programs on ubuntu without using sudo commands in a terminal? Why don't programs come with their own installing app? Is this a technical issue or lack of effort on the developers hands? I'm new to Linux and these are a lot of the problems I've ran in to thus far in my endeavors.

---

### Post by aysiu on 2007-01-28
> **enixon said:**
> Is it possible to install programs on ubuntu without using sudo commands in a terminal? Yes. Read this:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by jim-in-utah on 2007-01-29
I'm still confused -- Maybe I was too wordy and didn't make my question specific enough. What I'm confused about is not installing packages with apt-get, or even running ./configure, make and make install as such, I think I've finally figured that much out. What I don't get now is why after I install one program the next program's configure file can't find it. I checked both with whereis and by looking in nautilus and the qmake is there in /usr/bin and /usr/bin/X11. There is a link called qmake and a file called qmake-qt4 in both. Isn't /usr/bin on my PATH? If I type qmake -v in Terminal, from the same directory, it tells me I have qmake version 200a, using Qt 4.1.2 in usr/lib. So why can't the configure.py for PyQt find it, if the Terminal can? I have tried the following commands: 
sudo python2.5 configure.py -q /usr/bin/qmake
sudo python2.5 configure.py -q /usr/bin/qmake-qt4
sudo python2.5 configure.py -q /usr/bin/X11/qmake
sudo python2.5 configure.py -q /usr/bin/X11/qmake-qt4
and a few other variations, and it still tells me it can't create ./qtdirs and I need to have a working Qt v.4 qmake on my PATH or use -q to specify where it is. What am I missing? Do I have to do something to configure the PATH to include /usr/bin? Is it called something else in other versions of Linux that I need to change to so the software can find it? Has anyone else on the forum ever installed PyQt who knows what to do? Can anyone explain what these programs even are? It looks to me like Qt is a whole huge program for writing software, and qmake is the compiler part of it -- is this right? And is PyQt an add-on for compiling Python programs? Isn't this what Python2.5 is? This is what I find so confusing, that I need to practically be a programmer just to install a little piece of software to add and remove e-books from an e-book reader. I installed the XP version on my sister's computer in under a minute, and the linux version has taken me over a month so far and still doesn't work.

---

### Post by jlambeth1 on 2007-01-29
Thanks aysiu for the link.  I just dove into linux two days ago and was confused on how to install any programs.  The link you posted was very informative for a long time Windows user who wants something new and better.  I have yet to try Ubuntu as it downloaded last night, but after all that I have read, I am eagerly waiting for work to end so that I can go home and try it out.

---

### Post by rowinggolfer on 2008-01-11
Hi Jim,

I run several Ubuntu machines, and have installed libprs500 on all of them. I am a python hacker, and interested in the source code, so on my laptop I installed from source (ie from the developers secure  site 'https://etc'). Only on that machine did I come accross a few issues similar to yours.

Firstly, I think you are trying to download the developers version of the software. This is a bigger package, and has greater dependencies (like the QT development environment).

I would suggest you try the following.
if you have a libprs500 folder in your home folder... delete it.

if you have the egg file in /usr/lib/python2.5/site-packages/   delete this also (I suspect you may have a bad egg!)

then let's sort out your dependencies. Open a terminal and type:

$sudo apt-get install python-setuptools python-imaging  libqt4-core libqt4-gui python-qt4 fonttools unrtf python-mechanize imagemagick xdg-utils python-dbus  python-lxml python-elementtree

(yep... that's a lot of dependencies, but you should most already)

if all goes well type
$sudo easy_install -U TTFQuery libprs500

then 
$sudo libprs500_postinstall

My guess is you WILL get a message about QT being 4.3.... but ignore this.
I think there may be a bug in the versioning reported by python. 4.3.2 is reported as 4.3. If you got qt4 via apt-get (as above) you will have 4.3.2 from the ubuntu repositories.

BTW - I also get a message about some obscure desktop integration suite I have no intention of using. Start the program via a terminal simply type 
$libprs500

good luck.

Neil.

---

### Post by Amstell on 2008-01-11
they have instructions on their website for getting it to work

[https://libprs500.kovidgoyal.net/download_ubuntu](https://libprs500.kovidgoyal.net/download_ubuntu)

```

sudo apt-get install  python-setuptools python-imaging  libqt4-core libqt4-gui \
                      python-qt4 fonttools unrtf python-mechanize \
                      imagemagick xdg-utils python-dbus  python-lxml \
                      python-elementtree
sudo easy_install -U TTFQuery libprs500 
sudo libprs500_postinstall
```

just run those commands and it should throw a menu up  in your applications menu.

Good luck

P.S. Remember, google is the **** for answers.

---

