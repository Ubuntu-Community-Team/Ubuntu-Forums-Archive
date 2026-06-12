---
title: "[SOLVED] How do I install Eclipse?"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by perito on 2008-03-17
I got the file from
[http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/europa/winter/eclipse-java-europa-winter-linux-gtk.tar.gz](http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/europa/winter/eclipse-java-europa-winter-linux-gtk.tar.gz)
trying to install eclipse
eclipse-java-europa-winter-linux-gtk.tar.gz

yes i know i can sudo apt-get install eclipse, but that would download more than 100mb which will take forever and I already have the file (.tar.gz)....

so how can I install eclipse from this file?
thx

---

### Post by Duck2006 on 2008-03-17
This may help with installing *.tar.gz files.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by StOoZ on 2008-03-17
the 'tar' command can extract this zipped file and right after that also the tar.
use the man page for 'tar' for explanation and good  examples.
in the terminal,type:
man tar

---

### Post by upbeat.linux on 2008-03-17
I would recommend going the sudo apt-get install eclipse route if you are new to *nix/Ubuntu.

Otherwise, make sure to read the README and INSTALL files in the base directory that you untar.

---

### Post by Nythain on 2008-03-17
if you can get it from the repos, you should... yeah you already have the source, but do you have all of its dependencies... i mean, you could theoretically end up needing to download near 100mb of dependencies anyways... so you might as well take teh easier route

but if you must, then as already mentioned, untar that badboy, and look for a README or INSTALL and follow the instructions... some source packages are as simple as
./configure
make
make install

others are as simple as
python setup.py
or
sh install.sh

and others can be a real pain in the bum

---

### Post by bodhi.zazen on 2008-03-17
In general you should install from the repos if at all possible.

	[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

	========================
	
```
sudo aptitude update
sudo aptitude install build-essential checkinstall
```

	download the source code, unpackage.

	Open a terminal, cd into the package directory.

	Now, 

	[list=number][*]Read the README and/or INSTALL file.```
gedit README
```
	[*]List the options: ```
./configure --help | less
```You may scroll through the output with up and down arrows, page up, page down ... 
	Type q to exit less.


	[*]./configure --prefix=/usr
	[*]make
	[*]sudo checkinstall -D[/list]

---

### Post by Nepherte on 2008-03-17
In the case of eclipse, you don't have to do any of the above (which actually is the way to install .tar.gz files by the way). Just unpack the file and run the "eclipse" file. This will start up eclipse.

---

### Post by aysiu on 2008-03-17
Isn't Eclipse in the repositories?

This might help you:
[Installing and setting up Eclipse with Sun's Java](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by Nepherte on 2008-03-17
He said he already had the .tar.gz file and didn't want to dowload the whole package in synaptic again :)

---

### Post by perito on 2008-03-18
> **Nepherte said:**
> In the case of eclipse, you don't have to do any of the above (which actually is the way to install .tar.gz files by the way). Just unpack the file and run the "eclipse" file. This will start up eclipse.


exactly :)
thanks everybody, no installation needed

---

