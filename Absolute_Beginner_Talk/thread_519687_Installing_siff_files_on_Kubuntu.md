---
title: "Installing siff files on Kubuntu"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by FireStorm102389 on 2007-08-07
Ok, well, I guess I can't really get to know linux if I don't ask important and useful questions about specifics on where I am having problems...so here goes...

Kubuntu 7.04 is the version I installed on my computer.  I recently had lots of trouble trying to install things, untill I stated looking at things from a slightly different angle, because I was under the impression that U had to manually do everything in a terminal and there was no install...but im over that now...now the question is how do I get different files other than .deb files to show up for installation?...Kubuntu has no problem recognizing and installing . deb files, but when it comes to the other files there is no install option and it doesn't show up into any of the lists in adept manager.

.gz, .bz2, .rpm

and im sure there is another cuz it feels like im missing one, but either way...it doesn't give me an installl option and I was wondering how I would go about installing them if they don't show up in the adept manager or add/remove programs?...unless there is something im oing wrong or forgetting to do to make them shw up...PLZ some HELP me

I just want to know how to install them, and I really wanna know how to install a game called [Boson]("http://www.kde-apps.org/content/show.php/Boson?content=28633")

---

### Post by Pragmatist on 2007-08-07
Check this out:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/install-file.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/install-file.html)

Under "tarballs", the name for the type of packages your describing, it says:
> 
Files with the *.tar.gz* or *.tar.bz2* suffix are package files known as *tarballs* which are widely used in Linux and Unix.
         If there is no native Ubuntu package available in any of the Ubuntu repositories, **you can use the command line to install or uninstall the Tarball file by following the instructions that come with the package.**
         Tarballs often contain the source code of the program, and need to be *compiled* in order to be used. To do this, extra software will generally be needed (see [the section called “Basic Compilers”]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/build-essential.html")).


This is not too explicit.  Here is some more detail:
1.) Download the tarball:  You will then have a file of the form filename.tar.gz or filename.tar.bz (or filename.tar.bz2 which is treated the same as the .bz)

2.) The file is compressed, "zipped", which is why you see the ".gz or .bz or .bz2".  After you unzip it, it will just have .tar at the end.  A tar file is an "archived" file.  It is a way of grouping several related files together.  You will then need to "unarchive" or "untar" the .tar file.  We are going to accomplish both of these steps (unzip and untar) in one step:
**tar xvzf filename.tar.gz**
If the extension is .bz or .bz2, then you type:
[B]tar xvjf filename.bz

[/B]3.) The previous step will create a new directory with files.  The directory name will be similar to the name of the .tar.gz file (i.e. "filename" as used above).  You switch into that directory and you should find a README file and sometimes a INSTALL file.  Read them both.  They should describe the installation process.

4.)  The installation process depends on whether or not you need to compile code.  If you do not need to compile code, the executable should be in the directory you unzipped/untared.  If you do need to compile code, it will be explained in the README/INSTALL files and usually has three steps:
(a) configure your system for the compile:  **./configure**
(b) compile: **make**
(c) install the compiled program and files on your computer: s**udo make install** This last command often needs "sudo" since root (administrator) privileges are needed to copy files to certain directories on your system.

---

