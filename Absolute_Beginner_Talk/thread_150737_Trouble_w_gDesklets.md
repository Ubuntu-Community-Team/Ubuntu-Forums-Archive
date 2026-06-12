---
title: "Trouble w/ gDesklets"
date: 2006-03-26
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-03-26
I'm having trouble with getting a xmms controller to work.  I'm really having trouble getting anything to woek with gdesklets (only a few desklets actually work.  I installed gdesklets through automatrix.  Here is a picture of the error message I get when i run the desklet.

---

### Post by arnieboy on 2006-03-26
[QUOTE=echo $USER]I'm having trouble with getting a xmms controller to work.  I'm really having trouble getting anything to woek with gdesklets (only a few desklets actually work.  I installed gdesklets through automatrix.  Here is a picture of the error message I get when i run the desklet.[/QUOTE]
are u trying to run the desklets which come preinstalled with automatix? if yes, I would suggest you uninstall them 
This is because most of these desklets (in the ubuntu repositories) which automatix installs from the ubuntu repositories are obsolete and dont function anymore.
Do the following:
```
sudo apt-get remove gdesklets-data 
```
and install desklets manually from here:
[http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)
To install the desklets, just download the gz files of your choice and from the gdesklets window, click File --> Install package and then choose the gz file.
Once the desklets get installed, u can safely delete the files themselves from your download directory.

---

### Post by echo $USER on 2006-03-26
I uninstalled gdesklets.  Downloaded the latest version and extracted the files to /home/****/gdesk.  Installed build-essential.  Now here is my problem, when I run ./configure this is the error I get (something about missing perl?): 

****@ubuntu:~/gdesk/gDesklets-0.34.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
****@ubuntu:~/gdesk/gDesklets-0.34.3$

---

### Post by arnieboy on 2006-03-26
u jumped a step ahead which you could have avoided. I had just told you to remove the gdesklets-data package.

as for the error, do the following:
```
sudo apt-get install libxml-parser-perl
```
and then run configure again and paste the next missing dep if any.

---

### Post by echo $USER on 2006-03-26
Sorry about that.  So i got gdesklets installed again.  Thsi is the only desklet I have instlled after the clean install fo the program.  Now when I open the ipod xmms controller this is the error message I get:

---

### Post by arnieboy on 2006-03-26
[QUOTE=echo $USER]Sorry about that.  So i got gdesklets installed again.  Thsi is the only desklet I have instlled after the clean install fo the program.  Now when I open the ipod xmms controller this is the error message I get:[/QUOTE]
u mean u have the latest compiled version of gdesklets installed or the package in the ubuntu repositories?
please give me the link of the desklet that you are trying to make work.

---

### Post by echo $USER on 2006-03-26
Yeah, I compiled the lates version 0.34.3.  Here is the link to the desklet I cant get to work:  [http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=237]("http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=237")

I'm using the version for xmms.  It installs with no trouble, just when I try to use it I get the error message in the picture in my above post.  Thanks a lot for all the help.

---

### Post by arnieboy on 2006-03-26
try the following:
```
sudo apt-get install python-xmms
```
now try running the desklet again.

---

### Post by echo $USER on 2006-03-26
[QUOTE=arnieboy]try the following:
```
sudo apt-get install python-xmms
```
now try running the desklet again.[/QUOTE]

Perfection!  Thanks a ton dude.  That did the trick.

Oh yeah, how did you know that was what i needed?

---

### Post by arnieboy on 2006-03-26
> Requirements/Dependencies: PyXMMS (XMMS only)

right on top of the page which houses your desklet.

---

### Post by echo $USER on 2006-03-26
[QUOTE=arnieboy]right on top of the page which houses your desklet.[/QUOTE]
lol. Thanks again man.

---

