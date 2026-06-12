---
title: "Tar"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-03-13
I wonder if anyone can tell me what to do with a file that I have downloaded 
that is a tar.gz file
I have been trying to get this program installed for about a week and cant figure out how to do it with an .exe file so I got a Linux compatible version and when I downloaded it the file aboue is what i got

---

### Post by tchoklat on 2007-03-13
Double click the tarball and open it with the archive manager, extract it to a folder inside your home folder (don't do it straight into the home folder or you might get stuff all over the place, make a folder for source stuff, for instance "src" is short for source). After you extract it, go to that folder where you extracted it (extract is like unzip on a .zip file). Read the readme.txt. It'll tell you how to install. *Most* programs you can use the command line (that's the only way to compile from source) and go to that folder, for instance
cd ~/src/game

then you have to
./configure
sudo make
sudo make-install

---

### Post by arochester on 2007-03-13
See "How to install ANYTHING in Ubuntu!" at [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by Tyr Norian on 2007-03-13
(EDIT: tchoklat already answered much better than I did.)

---

### Post by jrandolph on 2007-03-13
Well I extracted it and got this "Install sh" file and I tried to run it but it does not work I would assume it should do something but it does nothing

---

### Post by jrandolph on 2007-03-13
The software is a telnet emulator called TN5250

---

### Post by ardchoille42 on 2007-03-13
> **jrandolph said:**
> I wonder if anyone can tell me what to do with a file that I have downloaded 
that is a tar.gz file
I have been trying to get this program installed for about a week and cant figure out how to do it with an .exe file so I got a Linux compatible version and when I downloaded it the file aboue is what i got

Go into the directory that has that .tar.gz file and do:

```

tar xzvf filename.tar.gz

```

Where filename is the name of the file. That will unpack the file.

To run an install.sh file as root, do:

```

sudo sh install.sh

```

---

### Post by Tyr Norian on 2007-03-13
If that still doesn't work, the homepage for the project says there's a Debian package available.

[URL="http://sourceforge.net/project/downloading.php?group_id=27533&use_mirror=optusnet&filename=tn5250_0.16.5-5woody1_i386.deb&44798851"]http://sourceforge.net/project/downloading.php?group_id=27533&use_mirror=optusnet&filename=tn5250_0.16.5-5woody1_i386.deb&44798851
[/URL]
Get that, move to the directory you saved it in, and type:

```
sudo dpkg -i tn5250_0.16.5-5woody1_i386.deb
```

The same package is also available in the "universe" repository for Ubuntu.

Out of pure curiosity, what do you intend to use this for? It looks fascinating.

---

### Post by jrandolph on 2007-03-13
Thank you all very much -- I got it to work -- now I have no need to ever use MS windows again

---

### Post by Aurora Borealis on 2007-04-02
What a great thread. There are lots of us who've been struggling with this. Thanks from me, too.

---

