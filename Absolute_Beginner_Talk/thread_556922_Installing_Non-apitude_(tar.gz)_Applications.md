---
title: "Installing Non-apitude (tar.gz) Applications"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by Patriot1776 on 2007-09-21
Hello guys, I'm a one-week old Ubuntu user and already I LOVE the command-line.  Been reading for sometime around on linuxcommand.org.  So much so I'm now wanting to use 'pure' command line programs.  I've downloaded mp3blaster in tar.gz form and just looking for general advice and maybe a tutorial on installing it since it's not an apitude-registered applicaton not available in the Add/Remove menu.  

If I can get it working, I'm then going to find me a WMA-to-MP3 converter like SoundConverter is (which I currently use), but also preferably in 'pure' command-line form.

EDIT - I guess the main things are that since I have to do stuff myself, I'm mainly looking for advice about where to put everything when I unpack the tar.gz that mp3blaster came in.

---

### Post by Maestro23 on 2007-09-21
> **Patriot1776 said:**
> Hello guys, I'm a one-week old Ubuntu user and already I LOVE the command-line.  Been reading for sometime around on linuxcommand.org.  So much so I'm now wanting to use 'pure' command line programs.  I've downloaded mp3blaster in tar.gz form and just looking for general advice and maybe a tutorial on installing it since it's not an apitude-registered applicaton not available in the Add/Remove menu.  

If I can get it working, I'm then going to find me a WMA-to-MP3 converter like SoundConverter is (which I currently use), but also preferably in 'pure' command-line form.

EDIT - I guess the main things are that since I have to do stuff myself, I'm mainly looking for advice about where to put everything when I unpack the tar.gz that mp3blaster came in.


You need to extract if first either thru GUI (Right-click and extract) or command line:

> tar xvzf filename.tar.gz

Should then be a README/INSTALL.txt file in the extracted folder with instructions and programs (if any) it requires.  If you run into dependency issues, you will have to resolve them first.

From it's README.doc

> 3.  Installation
-------------------------

    If you're eager to start, this will do:
        ./configure
        make
        make install


When compiling from source, make sure you have "build-essential" installed.

> sudo apt-get build-essential

Some useful links: 

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Post back when you hit a wall. :smile:

---

### Post by Patriot1776 on 2007-09-22
Ran "./configure" and it says that there are no (n) curses in the system.  Saw a few other no's as well.  I'm guessing that when I run "./configure", I want zero "no's" right?  If that's so, it also said that apparently the soundcard isn't available.

---

### Post by Patriot1776 on 2007-09-22
Okay now, I need ncurses.  Maybe just use wget to get it?

---

