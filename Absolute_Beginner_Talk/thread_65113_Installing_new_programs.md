---
title: "Installing new programs"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by wgrytt on 2005-09-13
Got Ubuntu up and running. Yeah. Then downloaded some typing programs for my students. They are sitting right on my desktop and I can't find any info within Ubuntu to explain how to open and install programs that aren't on the Synaptic Manager's package list. Someone tell me I'm missing something incredibly simple that doesn't involve entering codes etc. and that plays to my strengths -- clicking on buttons. Looking forward to installing Emacspeak for low Special ed kids.

---

### Post by Perfect Storm on 2005-09-13
I guess you're are looking for is .deb files (these are packages that ubuntu are using), but you can't just point'n'click these packages.
To install a .deb file you have to open the terminal and:

cd /where/you/saved/the/package
sudo dpkg -i XXXXXX.deb

or

sudo dpkg -i /where/the/package/is/XXXX.deb
the last option that are shown here, you can just type sudo dpkg -i and drag the .deb package into the terminal.

If it's a Shell script installing files (.sh file), you have to:
sudo sh /where/the/package/is/XXXX.sh

If they aren't as .deb or .sh there's a possiblity that you have to compiile itself.



.:=The AI Dude=:.

---

### Post by aysiu on 2005-09-13
Looks as if emacspeak is in universe:

[http://mirrors.xmission.com/ubuntu/pool/universe/e/](http://mirrors.xmission.com/ubuntu/pool/universe/e/)

Have you enabled extra repositories?

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by tonysathre on 2005-09-13
if the file is a tar.gz or tar.bz2 u have to compile it form source:

to do this, make a new folder for the file, move the file into that folder, then open a terminal cd to the new directory that u made, type in the terminal tar zxvf filename.tar.gz or tar jxvf filename.tar.bz2(depends what kind of archive file it is), it should spit out a bunch of stuff, then type ls in the terminal to see what the new folder it created was called, then cd to the new directory, type ./configure, then when that is done type make, then sudo make install, then when that is done type make clean and your all done.  hope this helps

---

### Post by aysiu on 2005-09-14
[QUOTE=aysiu]Looks as if emacspeak is in universe:

[http://mirrors.xmission.com/ubuntu/pool/universe/e/](http://mirrors.xmission.com/ubuntu/pool/universe/e/)

Have you enabled extra repositories?

[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)[/QUOTE] It is in the universe repositories. Take a look at this screenshot of my Synaptic. You can just apt-get install emacspeak.

[http://i22.photobucket.com/albums/b337/psychocats/888aaa8d.png](http://i22.photobucket.com/albums/b337/psychocats/888aaa8d.png)

---

