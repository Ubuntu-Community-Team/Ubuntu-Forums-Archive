---
title: "[SOLVED] Installing Gparted"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Mwelsh on 2008-02-27
I'd like to put Gparted onto my Ubuntu (Xubuntu I think actually) machine, but I have no compiler. I also have **NO** internet access on that computer, so sudo apt-get does not work.

Any help would be greatly appreciated. I already checked for a partition editor, and no default one is installed (to my knowledge).

Thanks!

---

### Post by wormser on 2008-02-27
Do you still have the install CD?  I believe there is a version on there.

---

### Post by ajeetraj on 2008-02-27
if you have a live cd then you can use that. Usually for the partitioning if you want gparted then any live CD should do the trick!

---

### Post by jan quark on 2008-02-27
the live cd is one option
the other is to create a[ gparted live cd]("http://gparted-livecd.tuxfamily.org/")

---

### Post by Mwelsh on 2008-02-27
I have the Live CD, but I don't want to have to run the program off the CD.... I don't want to have to boot off the CD... 

Can I install with the Live CD? and if so, how?

Thanks for the suggestions

---

### Post by jan quark on 2008-02-27
you can install gparted by dowloading it from this site

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754) or

[http://packages.debian.org/etch/gparted](http://packages.debian.org/etch/gparted)

from a pc with inet connection and transferring the tar to your pc via an usb stick.

---

### Post by Mwelsh on 2008-02-27
Will this work if I don't have a compiler? I got a gparted tar.gz earlier, and when I tried to install it, I had issues regarding a missing C(++?) compiler. I then tried to install a compiler, but it also had issues...

Thanks!

---

### Post by ajeetraj on 2008-02-27
Did you try to use a .deb file for the installation of gparted?

if not then you can get the .deb file for feisty here: [http://ubuntuforums.org/showthread.php?t=465262#post2787589]("http://ubuntuforums.org/showthread.php?t=465262#post2787589")

---

### Post by stchman on 2008-02-27
> **Mwelsh said:**
> I'd like to put Gparted onto my Ubuntu (Xubuntu I think actually) machine, but I have no compiler. I also have **NO** internet access on that computer, so sudo apt-get does not work.

Any help would be greatly appreciated. I already checked for a partition editor, and no default one is installed (to my knowledge).

Thanks!

Problem is you can get the source code for gparted and try to compile it, but you might run into dependency issues.

[http://packages.ubuntu.com/gutsy/gparted](http://packages.ubuntu.com/gutsy/gparted)

You can download the .deb package and try.  If you have all the dependencies already installed then you are golden.  If not then you will have to install the dependencies before-hand.

---

### Post by Mwelsh on 2008-02-27
If I don't have all the dependancies, where can I get those?

Thanks again! The .deb files you all pointed me to seem to work, but I lack dependencies

---

### Post by Duck2006 on 2008-02-27
I beleave you can get what you want here.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by ajeetraj on 2008-02-27
well, I am glad it is working. Here is some info might help you: 

To see the dependencies: [link]("http://www.gnomefiles.org/app.php/GParted")

For other info on gparted: [here]("http://gparted.sourceforge.net/download.php")

And, for the libparted package and other related packages you can easily google for the required packages or just search in the terminal with "sudo aptitude search <package name>"

Hope this helps!

---

### Post by Mwelsh on 2008-02-28
It's all working, just some conflicts with packages being newer than others already installed and prequisites... Will have to look into what removing certain packages will do....

---

