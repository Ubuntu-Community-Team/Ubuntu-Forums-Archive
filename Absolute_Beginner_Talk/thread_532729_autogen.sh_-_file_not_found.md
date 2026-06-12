---
title: "autogen.sh - file not found"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by FSten on 2007-08-23
I should start off by saying that I am new to linux and this is my first try on something like this.

I followed a step-by-step instruction on how to build gnucash ([http://wiki.gnucash.org/wiki/Building#Feisty]("http://wiki.gnucash.org/wiki/Building#Feisty")> Everything worked fine until I came to the command: ./autogen.sh when it says that "the file or folder does not exist" (translated from Swedish). I found an advice here on the forums to install libtools, which I did but no difference.

Any ideas on what I could do would be appreciated.

---

### Post by livestockPimp on 2007-08-23
have you tried seeing if the file exists?
type "updatedb" (this will take a while) and then "locate autogen.sh"
this will search for the file and tell you where it is located.
./someprogram.sh tells bash you are running the script "someprogram.sh" from the current directory.
if it is there, and it still wont work, try "ls -lah" and ensure the autogen.sh has the "x" attribute, if it does not then you can make it executable by typing "chmod +x autogen.sh"

---

### Post by FSten on 2007-08-23
Thanks. The file is not there. Strange, not sure what to do then. I thought it was supposed to have been included in the files I downloaded.

---

### Post by livestockPimp on 2007-08-23
well if you searched for it and its not there i would be trying to find out where it was meant to come from.

---

### Post by schorsch on 2007-08-23
Why don't you install it from the repos? You have to enable the "universe" repo to do this ...

---

### Post by FSten on 2007-08-23
I did at first, but I wanted to upgrade to version 2.2. The one I got installed is version 2.0.2

---

### Post by schorsch on 2007-08-23
Well, then you can skip the step regarding "./autogen.sh" and start with "./configure" step. You will have to install some additional development packages but the installation should work just fine.

---

### Post by FSten on 2007-08-23
Ok, thanks. So by running ./configure I will get a list of possibly missing packages? I ran it, but didn't understand much of the output. Do you mind giving me an indication on where to look? The output following the command is very long. 

If I run the next command, I get an error message saying that the package was not created, so I guess something is missing. Thanks for helping a newbie out. :)

---

### Post by schorsch on 2007-08-23
[COLOR="Red"]Please read until the end as I write this parallel to compiling![/COLOR]
Well, I just try to install gnucash in the version you wanted. I start by typing "./configure" in the directory with the sources. The output is indeed long but this is normal as the configure scripts checks everything that is needed to compile the application: Which compiler and which dependencies are available, which compiler flags can be used etc. When it complains that something is missing one would normally check if the "normal" packages are installed but most of the time the development packages are missing; their name ends with "-dev" under debian based systems like ubuntu (on SuSE the end with "-devel"....).
So I guess you have already run the following line as advised in the link you gave in your first post?
```
sudo apt-get install build-essential checkinstall guile-1.6-dev guile-1.6-slib libgoffice-0-dev libgtkhtml3.14-dev texinfo
```
Then I will now describe what I had to install in addition to that. It won't hurt if you try the following commands too as apt-get will say if an package is already installed, o.k.? If it says so just skip to the next command. Here we go:
```
sudo apt-get install guile-1.6-dev
sudo apt-get install guile-1.6-slib
sudo apt-get install libgnomeui-dev
sudo apt-get install libgoffice-0-dev
sudo apt-get install libgtkhtml3.14-dev
```
To search the available packages just type
```
apt-cache search <packagename>
```
where <packagename> is the packagename the error message from the output of the "./configure" command mentioned. For example: If it says "bla bla ... libgnomeui is missing" search for "libgnomeui" and you will get the proper name of the development package.
Take a look: Nearly all of the packages needed to install are mentioned in my first Code-Block except "libgnomeui-dev" whereas "texinfo" is not installed on my system and seems to be no longer required.

O.K. Step 2:
```
make
```
Tip: If you want to compile faster, type
```
make -j2
```
The value after "-j" controls how many make processes will be run paralell. So if you have a multi-core machine you could turn it up to reduce the compile time. When you get another error I would type
```
make clean
make
```
so you will start with a proper source code and start only one make process just to be on the safe side.

Next Step 3:
Normally you would now type:
```
sudo make install
```
This will install the application into you system BUT: You will not be able to remove as easy as with a package manager like synaptic! If you have the sources still availlable you can change into the sources directory and type:
```
make uninstall
```
This will work .... sometimes(!) as not every programmer includes this in the source code. Otherwise you will have to know which file is installed in which directory and manually delete it! In addition to that if you install the package from the repos in the future this can overwrite some needed files or something else and this can cause some trouble.
So I'd advise to install the package checkinstall:
```
sudo apt-get install checkinstall
```
This will build a .deb package that can be installed and (what is more important!) uninstalled at any time via the package manager with many applications that are compiled from the sources
So the last step now is:
```
sudo checkinstall --default --install=no --exclude=/bin,/usr/bin,/usr/lib
```
This will last for a few minutes. After it has finished you will have a file in the same directory called "gnucash_2.2.1-1_i386.deb" that can be installed via
```
dpkg -i gnucash_2.2.1-1_i386.deb
```
Regarding checkinstall again: if you set "install =yes" or leave this empty the created package will be installed automatically. The "--exclude" is helpful to exlude some directory from files that would be overwritten otherwise but you will get an error message from the dpkg-command. Right at the moment I am just running the "checkinstall" command, look where it throws an error message, exclude the path and run it again. Perhaps some one has a hint how this can be checked before?

I installed just a few minutes ago and it seems to work but as it does NOT create an icon in the applications menu you have to start it via terminal or create a link in the menu manually.

Phew, quite a long post for me but I hope it helps a little bit .....:)

---

### Post by FSten on 2007-08-24
Thank you very much for your long answer. I will have a look at it and try myself.

---

### Post by haxor999 on 2007-08-24
schorsch, thanks for the instructions. I originally followed the steps in the gnucash wiki at [http://wiki.gnucash.org/wiki/Building#Feisty]("http://wiki.gnucash.org/wiki/Building#Feisty") - skipped the [FONT="Courier New"]./autogen.sh[/FONT]  step and all was well.

However uninstalling that package later hosed my system (had to reinstall a bunch of DEBs) because it also insists on removing the things which the package originally overwrites into /usr/lib etc. This is where the **--exclude=/bin,/usr/bin,/usr/lib** parameter from your instructions comes in handy. Can't believe that the wiki advocates just using the [FONT="Courier New"]--force-overwrite[/FONT] option to dpkg when installing that DEB. :( Someone should change that

---

### Post by schorsch on 2007-08-25
Thats what I like about installing sources with checkinstall. If you install packages without checkinstall you can have problems to remove all files and even a "make uninstall" in the sources directory can harm your system.
When a fresh compiled package wants to overwrite some system files I am always observant as I do not want my system to be hosed. Right at the moment for me it is "Trial and Error" to find the right directories to exclude but it works. Perhaps someone has an advice how to find them before running checkinstall?

---

