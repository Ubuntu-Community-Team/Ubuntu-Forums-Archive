---
title: "installing tar.bz2"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Roen hayden on 2007-05-29
ok so lets say u do not want to use the Add and remove of installing and uninstalling applications.. And u download the tar.bz2 file from the internet how would you go about installing the software you download from the net?

---

### Post by yabbadabbadont on 2007-05-29
By reading and following the detailed instructions provided by the person who created the tar.bz2 file.  What, they didn't include detailed instructions?  Go bug them.  ;)

Unless you have a very good reason, and know what you are doing (you don't since you had to ask), use the version of the application that is available in the repositories.  :D

---

### Post by Roen hayden on 2007-05-29
Ok yes i the the repositories are easyer but what if they were to go down or crash how would i install it then? by the way the software is NVU

---

### Post by yabbadabbadont on 2007-05-29
> **Roen hayden said:**
> Ok yes i the the repositories are easyer but what if they were to go down or crash how would i install it then? by the way the software is NVU

[LIST=1]
[*]Search the net for a deb package that someone else has already created.
[*]Politely ask someone here who knows what they are doing to create such a deb package.
[*]Go bug the author(s) of the software you wish to install to provide a deb package.
[*]Go bug the author(s) of the software you wish to install to provide a complete list of the build dependencies and, hopefully, some decent instructions on how to configure and build the software.
[/LIST]
:D

Edit: #4 is important as the person in #2 will need that information too.

---

### Post by Ek0nomik on 2007-05-29
If you want to install software, you can use the repositories as you know.  If they go down, you can change your sources to another location.  Example, I live in the U.S., and the U.S. repository has gone down for a few minutes before, so I switched to U.K. repos and was able to download.

If you want to compile, you **have** to first run this command.  (Once, and only once by the way)

```
sudo aptitude install build-essential
```

This will install necessary library files and software so you can compile packages.

Generally each tarball (tar.gz) will contain a README file telling you what to do.  Extract the tarball, then navigate into the directory and look for a README file and... well, you know, read it.  ;)

The commands generally go like this:

```
./configure
sudo make
sudo make install
```

but, again, check the README for exact instructions and/or other necessary library files.

---

### Post by ellisdee on 2007-05-29
.tar.bz2 files are just compressed similar to .zip in Winblows

Once you unzip these files there's usually a readme file you can open in your favourite text editor that will give you directions on how to install the software you downloaded.

Most steps are simply decompress, ./configure, make, make install

Here's an example of how I would install a new application -

I just downloaded newapplication.tar.bz2
Open up Terminal
Navigate to the appropriate directory (eg cd /home/user/Desktop/)
tar xvfj newapplication.tar.bz2 (This will extract the files)
Navigate to the newly created directory (eg cd /home/user/Desktop/newapplication/)
./configure
make
sudo make install
My new application is now installed and ready to be used ;)

---

### Post by yabbadabbadont on 2007-05-29
If you are really interested in creating a proper deb package, there is a rather long and complicated wiki article about it.

[https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch](https://wiki.ubuntu.com/HowToBuildDebianPackagesFromScratch)

Edit: By the way, the "./configure" step will probably fail several times until you have all of the build dependencies installed.  When installing dependencies in Ubuntu, be aware that libraries come in two packages.  The normal one that is used at run time and a development version that is used at build time.  (they end in *-dev usually)  You will need both versions installed when trying to satisfy the dependencies of your program.

---

### Post by ellisdee on 2007-05-29
damnit beaten to the crunch ;P

---

### Post by MakLeod on 2007-05-29
NVU has an update call Kompozer and you can get it at [www.getdeb.net](www.getdeb.net) in a precompiled .deb that you can just click and install.

---

### Post by Limitlesschannels on 2007-05-29
> **Ek0nomik said:**
> If you want to install software, you can use the repositories as you know.  If they go down, you can change your sources to another location.  Example, I live in the U.S., and the U.S. repository has gone down for a few minutes before, so I switched to U.K. repos and was able to download.


how do i switch to the UK repos?  Is that an entire sources.list substitution?

---

### Post by Roen hayden on 2007-05-29
> **ellisdee said:**
> .tar.bz2 files are just compressed similar to .zip in Winblows

Once you unzip these files there's usually a readme file you can open in your favourite text editor that will give you directions on how to install the software you downloaded.

Most steps are simply decompress, ./configure, make, make install

Here's an example of how I would install a new application -

I just downloaded newapplication.tar.bz2
Open up Terminal
Navigate to the appropriate directory (eg cd /home/user/Desktop/)
tar xvfj newapplication.tar.bz2 (This will extract the files)
Navigate to the newly created directory (eg cd /home/user/Desktop/newapplication/)
./configure
make
sudo make install
My new application is now installed and ready to be used ;)

ok it will now allow me to Navigate to the appropriate directory if says bash: cd: /home/user/Desktop/: No such file or directory and yes i replaced user with my name.

---

### Post by ellisdee on 2007-05-29
You should be able to auto-complete your command by pressing tab twice so that you are navigating to the correct directory

This is what it looks like on my pc -

shan@schlappy:~$ cd /home/                     (pressing tab twice after the /)
user/   user2/
shan@schlappy:~$ cd /home/user/D          (pressing tab twice should auto-complete Desktop and so on)

The path has to absolutely accurate if you are trying to navigate there that includes case

If the file is on your desktop it should be something like -
username:~$cd /home/username/Desktop/

Remembering the ls command lists the contents of the directory if you would prefer to navigate level by level to view contents

I hope this post isn't confusing ;P

---

### Post by Roen hayden on 2007-05-29
> **ellisdee said:**
> .tar.bz2 files are just compressed similar to .zip in Winblows

Once you unzip these files there's usually a readme file you can open in your favourite text editor that will give you directions on how to install the software you downloaded.

Most steps are simply decompress, ./configure, make, make install

Here's an example of how I would install a new application -

I just downloaded newapplication.tar.bz2
Open up Terminal
Navigate to the appropriate directory (eg cd /home/user/Desktop/)
tar xvfj newapplication.tar.bz2 (This will extract the files)
Navigate to the newly created directory (eg cd /home/user/Desktop/newapplication/)
./configure
make
sudo make install
My new application is now installed and ready to be used ;)

ok i nav to to the right directory and when i get there i typed ./configure and this came up "bash: ./configure: No such file or directory" i'm so close..

thanks 
~roen

---

### Post by Roen hayden on 2007-05-29
ok i got the ./configure working but once i get into the options i do not know what to do from there?..

thanks 
~roen


this is what it says when i open ./nvu-configure

Usage: ./nvu-config [OPTIONS] [LIBRARIES]
Options:
        [--prefix[=DIR]]
        [--exec-prefix[=DIR]]
        [--version]
        [--defines]
        [--libs] [libraries]
        [--cflags] [components]
        [--idlflags]
Components:
    *
Libraries:
    xpcom
    nspr
    js
    jsj
    gfx

---

### Post by Roen hayden on 2007-05-29
> **Roen hayden said:**
> ok i got the ./configure working but once i get into the options i do not know what to do from there?..

thanks 
~roen


this is what it says when i open ./nvu-configure

Usage: ./nvu-config [OPTIONS] [LIBRARIES]
Options:
        [--prefix[=DIR]]
        [--exec-prefix[=DIR]]
        [--version]
        [--defines]
        [--libs] [libraries]
        [--cflags] [components]
        [--idlflags]
Components:
    *
Libraries:
    xpcom
    nspr
    js
    jsj
    gfx

SO how do i execute one of those options?

---

### Post by Ek0nomik on 2007-05-29
> **Limitlesschannels said:**
> how do i switch to the UK repos?  Is that an entire sources.list substitution?

In your sources.list file you should be able to switch us to uk.

---

### Post by Roen hayden on 2007-05-29
[QUOTE=Ek0nomik;2745963]In your sources.list file you should be able to switch us to uk.[/QUO

nothing its wrong with the repositories i just wanna know how to install software you download from the net.

---

### Post by Ek0nomik on 2007-05-29
> **Roen hayden said:**
> 
nothing its wrong with the repositories i just wanna know how to install software you download from the net.

I was talking to someone else.  ;)

Can you post the README file for me?

---

### Post by Roen hayden on 2007-05-29
there isn't a readme file.. the software is NVU ..?

---

### Post by Ek0nomik on 2007-05-29
Ok, so you had a tarball (tar.gz) correct?  Where did you extract the files?  On your Desktop?  Let's pretend the directory is "Nvu".  Did you navigate inside the directory?

Open a fresh brand spanking new Terminal and type:

```
cd Desktop/Nvu
```

(replace Nvu with whatever folder the files are inside of)

Then, please type and **post me ALL your terminal output (yes, from the very beginning so we can clear up some abstractions)**:

```
ls
```

Post your output and let's see where you're exactly working out of and we can move on a bit quicker.

---

### Post by yabbadabbadont on 2007-05-29
Both of you might find this interesting (and relevant): [http://forum.nvudev.org/viewtopic.php?t=6890](http://forum.nvudev.org/viewtopic.php?t=6890)

Plus they provide binaries that they claim to have tested on Ubuntu (among others).

---

### Post by Roen hayden on 2007-05-29
paul@paul-desktop:~/Desktop/nvu-1.0$ ls
bloaturls.txt      libmozjs.so      libxpcom_compat.so      regchrome
chrome             libnspr4.so      libxpcom.so             regxpcom
components         libnss3.so       libxpistub.so           res
defaults           libnssckbi.so    LICENSE                 run-mozilla.sh
elf-dynstr-gc      libplc4.so       mangle                  shlibsign
extensions         libplds4.so      mozilla-xremote-client  xpcshell
greprefs           libsmime3.so     nsinstall               xpicleanup
icons              libsoftokn3.chk  nvu                     xpidl
libgkgfx.so        libsoftokn3.so   nvu-bin                 xpt_dump
libgtkembedmoz.so  libssl3.so       nvu-config              xpt_link
libgtkxtbin.so     libxlibrgb.so    plugins
paul@paul-desktop:~/Desktop/nvu-1.0$

---

### Post by Ek0nomik on 2007-05-29
I think he wants to know how to compile the program.  He knows he can download it online, but I think he wants to try it this way.  (Correct me if I am wrong)

P.S. **yabbadabbadont**:  I hope we have some good posting madness again tonight.  ;)

> **Roen hayden said:**
> paul@paul-desktop:~/Desktop/nvu-1.0$ ls
bloaturls.txt      libmozjs.so      libxpcom_compat.so      regchrome
chrome             libnspr4.so      libxpcom.so             regxpcom
components         libnss3.so       libxpistub.so           res
defaults           libnssckbi.so    LICENSE                 run-mozilla.sh
elf-dynstr-gc      libplc4.so       mangle                  shlibsign
extensions         libplds4.so      mozilla-xremote-client  xpcshell
greprefs           libsmime3.so     nsinstall               xpicleanup
icons              libsoftokn3.chk  nvu                     xpidl
libgkgfx.so        libsoftokn3.so   nvu-bin                 xpt_dump
libgtkembedmoz.so  libssl3.so       nvu-config              xpt_link
libgtkxtbin.so     libxlibrgb.so    plugins
paul@paul-desktop:~/Desktop/nvu-1.0$

Weird, who doesn't provide a README file?!?/!/  What kind of world are we living in?!

Anyways, type

```
./configure
```

inside the nvu-1.0 directory, and again, **post me your output**.

You did *excellent* on posting the output before by the way.  :)

---

### Post by Roen hayden on 2007-05-29
paul@paul-desktop:~/Desktop/nvu-1.0$ ./configure
bash: ./configure: No such file or directory
paul@paul-desktop:~/Desktop/nvu-1.0$

---

### Post by Roen hayden on 2007-05-29
hang on i did manage to get this 

ok i got the ./configure working but once i get into the options i do not know what to do from there?..


this is what it says when i open ./nvu-configure

Usage: ./nvu-config [OPTIONS] [LIBRARIES]
Options:
[--prefix[=DIR]]
[--exec-prefix[=DIR]]
[--version]
[--defines]
[--libs] [libraries]
[--cflags] [components]
[--idlflags]
Components:
*
Libraries:
xpcom
nspr
js
jsj
gfx
______

---

### Post by yabbadabbadont on 2007-05-29
Look at his ls output.  That directory contains a binary installation of nvu....  try running ./nvu in that directory.

---

### Post by Roen hayden on 2007-05-29
> **yabbadabbadont said:**
> Look at his ls output.  That directory contains a binary installation of nvu....  try running ./nvu in that directory.

i know i can run it that way but i want to install it so it is under applications

---

### Post by kva on 2008-07-19
> **Ek0nomik said:**
> In your sources.list file you should be able to switch us to uk.

Where is the sources.list file is it in /etc directory ?

---

### Post by aomlives on 2008-07-19
It's in the /etc/apt directory.

---

