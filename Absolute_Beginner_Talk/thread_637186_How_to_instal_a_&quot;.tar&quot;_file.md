---
title: "How to instal a &quot;.tar&quot; file"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by GSands on 2007-12-10
Well I am as green as they come and my memory has failed me with my DOS commands, I had hoped they would be similar to Linux commands.  I need to know how to install a ".tar" file after I have extracted it please.  I gotta get my movies back:popcorn: ty

---

### Post by njparton on 2007-12-10
A tar file is just a way of grouping files together into one filename which can be compressed or uncompressed.

Right click on the file in Nautilus and it should give you the option to extract.

Otherwise in a terminal type ```
man tar
``` and search for the extract switch.

```
tar -cvf filename
``` is to create a tar file, can't remember what the switch for extract is...

---

### Post by wormser on 2007-12-10
What are you trying to install?  Most software should be install via the repositories with Synaptic or apt-get.  First open up the univers and multiverse repositories.  System> Administration> Software Sources> Ubuntu Sofware tab> Check universe and multiverse.  Next look for the software package in Synaptic.  System> Administration> Synaptic Package Manager.  Now search for the software you want.  If the program you are looking for is not in the repositories then look for a .deb or .tar file online.

---

### Post by spiderbatdad on 2007-12-10
```
cd /Desktop
``` if the file is on your desktop...notice Desktop is case sensitive.
 then:
```
tar -zxvf name.of.file
``` just begin to type the name and hit the Tab key to auto complete the name of the file.

then:
```
cd new.file.created
``` where "new.file.created" is the  new directory created on your desktop of the same name as the original tar file. Again begin the name and use the Tab key.
then:

```
./configure
make
sudo make install
``` where each line of code is entered separately. Also open the directory and look for a readme file or install file to get instruction particular to this package.

---

### Post by Sef on 2007-12-10
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by bodhi.zazen on 2007-12-10
A "tar" is an archive and can contain source code or binary packages. It is best to read the README or look for instructions where you obtained it from.

If you need assistance, please specify what you are trying to install and where you got it from.

---

