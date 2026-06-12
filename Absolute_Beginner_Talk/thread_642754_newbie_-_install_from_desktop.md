---
title: "newbie - install from desktop"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by prospero96 on 2007-12-17
I've downloaded OpenOffice 2.3.1.tar.gz  to the desktop and would like to know how to install it.
I can extract all the files to a large number of folders but can't work out how to proceed from there.
As a lifelong windows user I'm used to an .exe file setup but I'm now in the dark.

---

### Post by jken146 on 2007-12-17
Use Applications > Add/Remove to install things.

and read ubuntuguide.org

---

### Post by perlluver on 2007-12-17
Try extracting to one folder, the readme.  Usually you go into the terminal, type in ./configure, followed by make and then make install.

---

### Post by jualin on 2007-12-17
If you are not a newbie go to the readme of the tar file and you will probably have to use the terminal. However you could just go to synaptic package manager and download the openoffice package. Or like the guy above me said go to add and remove programs, and open office is under the Office tab. Hope it helps

---

### Post by discoade on 2007-12-17
What version of ubuntu are you using?

---

### Post by staticvoid on 2007-12-17
openoffice should already be install...

your tar.gz is something call *source code* to compile source code, generally you do something like this:

First you need build-essentials.. or maybe its without the "s", pop in your ubuntu cd and open a terminal and type
```
sudo apt-get install build-essentials
```

then you use commands to change directories.

to cheange to your Desktop folder:
```
cd ~/Desktop
```
to list the files on your desktop:

```
ls
```

then cd into your extracted tar.gz folder type cd, begin typing the nam of the folder (openof..) and press tab, it fills in the blank.

now you try something like this, or follow the readme:
```
./configure
```
but then for all compiling from source you do:
```
make
```
and then
```
sudo make install
```


there you have it! a tutorial to help you get accustome to using the terminal :)
It is a lot easier just instll from a .deb package (like an exe) or install from "Add/Remove..."


have fun! the terminal is scary at first, but is useful!  :D
sv

---

### Post by The Cog on 2007-12-17
Its a bit of a pain. Their tar.gz unpacks to lots of .rpm files. Perhaps best is to convert these to .deb files. I don't remember exactly how, but I think it goes something like this:
[B]sudo apt-get install alien
sudo alien *.rpm[/B]
and then you can install all the .deb.files. 

But this will likely interfere with the default Ubunti install of OOo. As I'm not sure how they will interact, I always install OOo in an even more long-winded way:

Extract the tar.gz, creating lots of .rpm files.
Extract each rpm file in turn, this created a _files directory for each rpm. Each ot these opt directories contains a part of the full program.
copy the openoffice directory from each _files/opt directory to /opt (needs root priviledge). By the time you have done this, all the program has been installed under /opt.

Create a file /usr/local/bin/ooo with these contents:
[B]#!/bin/sh
/opt/openoffice.org2.3/program/soffice "$*"[/B]
Make it executable with this command:
sudo chmod +x /usr/local/bin/ooo
Now you can open files with ooo and get the latest version of openoffice. I have to say I don't really recommend this approch because its so long-winded.

Maybe someone should tell OpenOffice to get their flaming finger out and to release .deb files.

EDIT
I notice that the OpenOffice.org download site now includes a .deb download option. This should be much easier to install than their RPMs. I'm downloading now.

---

### Post by hyper_ch on 2007-12-17
Come on, he's new to linux... why are you all confusing him with compiling from source, convertign .rpms to .debs...

First better point out to him add/remove (Synaptic)... only if he wants a newer package THEN come up with the other stuff...

As a windows  user he is not used to have centralized access to tons and tons of software through the repositories... normal windows habit: Google it up, go to the website, download it, double-click the .exe/.msi file... --> and that's what he did becasue he doesn't know better yet!

---

### Post by sandysandy on 2007-12-17
> **prospero96 said:**
> I've downloaded OpenOffice 2.3.1.tar.gz  to the desktop and would like to know how to install it.
I can extract all the files to a large number of folders but can't work out how to proceed from there.
As a lifelong windows user I'm used to an .exe file setup but I'm now in the dark.

as suggested above the synaptic package manager may be the easier way to install openoffice, if not already installed.( [COLOR="Blue"]System - administration - synaptic package manager[/COLOR])

or use [COLOR="Blue"]Applications - add remove[/COLOR]

to check whether open office is already there check under[COLOR="Blue"]  Applications - office[/COLOR]

regards

---

### Post by The Cog on 2007-12-17
> **hyper_ch said:**
> Come on, he's new to linux... why are you all confusing him with compiling from source, convertign .rpms to .debs...

First better point out to him add/remove (Synaptic)... only if he wants a newer package THEN come up with the other stuff...

As a windows  user he is not used to have centralized access to tons and tons of software through the repositories... normal windows habit: Google it up, go to the website, download it, double-click the .exe/.msi file... --> and that's what he did becasue he doesn't know better yet!

You are absolutely right, except that I assume he already has an earlier version of OpenOffice installed, because it is installed as part of the standard install. If he knows how to uninstall that, I guess he can also reinstall it. 

If the Original Poster is happy with the version of OpenOffice that gets installed with Ubuntu, then please, just use Add/Remove software from the menus (or Synaptic Package Manager also from the menus) - this should **always** be your first place to look when you want to install software on Ubuntu. Only go elsewhere when you have good reason not to be happy with what's in the standard Ubuntu repositories.

Assuming he is after a later version than the default install, then he needs to go to the OpenOffice.org download site. The tar.gz is not (as someone suggested) a source-code download, but a collection of rpm files (or .deb files as an option). 

For some strange reason, I find that double-clicking on the .deb file launches gdebi and gets me an error message saying that a later version is already installed (which is rubbish) and refusing to install it. So the I unpacked all the individual .deb files by right-clicking and Extract Here, then I opened a command prompt in the DEBS directory and executed this command:
```
find . -name 'data.tar.gz' | sed 's:\./:tar xzf :' | sh
```
which created an **opt/openoffice.org2.3** directory that I then copied (as root) to /opt.

---

