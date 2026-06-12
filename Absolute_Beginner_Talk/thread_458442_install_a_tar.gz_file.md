---
title: "install a tar.gz file"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by ammmom on 2007-05-29
I have FF installed, but I don't have my CD with me.  I do have a copy of DD, if it helps.  I want to install "across lite" a program for the NY Times crossword.  I have two choices and I have downloaded both: acllinux.smotif.tar.gz or acllinux.dmotif.tar.gz I have motif installed.  

I'm new to Ubuntu and just can't figure this one out.  TIA.

---

### Post by Ek0nomik on 2007-05-29
A tar.gz file is merely an archive file.  It's like a zip or rar, it just holds and compresses other files into 1 file.  You extract the tar.gz, and then go into the folder and read the README file.

It will have instructions on how to compile.

To compile, you need to have build-essential installed

```
sudo aptitude install build-essential
```

Now, the commands generally go like this:

```
./configure
sudo make
sudo make install
```

---

### Post by GrueTamer on 2007-05-29
You install tar.gz files by extracting them with an archiving tool.  Inside, there are most likely source files: look for a makefile.  If there are, cd to the directory of the extracted files, and type in the terminal

```
./configure
``` (if there is a file named configure)
```
sudo make && make install
```

If it works, then the binary files should be made.  If not, post back the output of the command, and if there was a makefile inside the tar.gz file.

Also, look for instructions where you downloaded the files.  Those might help.

You'll need the build-essential package to do this, get it from apt or synaptic before compiling the file.

---

### Post by coxy on 2007-05-29
You need to extract the files from within the archive.

```

tar -xzvf acllinux.dmotif.tar.gz
tar -xzvf acllinux.smotif.tar.gz

```

The above command will extract the files into the current working directory. Tar is an archive tool used for the same kind of things as Winzip in a Windows environment. The switches are as follows:

x - extract
z - pass through gzip (because it is a .tar.gz)
v - verbose (prints what is happening on the screen)
f - file (the file name)

You can then cd into the directory and there should be some text files that will explain how to install the software. They normally reside in a text file called INSTALL.txt. There may also be a README.txt.

Different software use different methods of install so I can't be much more help than that.

---

### Post by ammmom on 2007-05-29
Thanks everyone.  I'm still very confused.  I used the " sudo aptitude install build-essential" command. Terminal spat out a bunch of stuff.  I said yes to the following "0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 7906kB of archives. After unpacking 33.0MB will be used.
Do you want to continue? [Y/n/?]"

Would you tell me which one I should install?

 # acllinux.smotif.tar.gz: Statically linked to Motif
OR
# acllinux.dmotif.tar.gz: Dynamically linked (you must have Motif library installed)

Then I'll get the readme file?????????

I'm really a beginner at all of this, so sorry.  TIA.

---

### Post by DJ Wings on 2007-05-29
Use the static one.

---

### Post by ammmom on 2007-05-29
I have the static files extracted and I printed out the readme file: In terminal, I typed > ldd acrossl
but terminal responded with > ldd: ./acrossl: No such file or directory"

I think that I need "dynamic libraries"  and I don't know anything about "dynamic libraries."  Here's the readme part:

> [I]
2.1 Dynamic libraries

	The program is dynamically linked to the following libraries which
must exist in a path searched by the loader in order to run the program:

	libXt.so.6		(X11R6 tested with 6.0 libraries)
	libXext.so.6
	libX11.so.6
	libc.so.5		(tested with 5.2.18)
	libSM.so.6
	libICE.so.6

	libXpm.so.4		(tested with 4.7)
	libg++.so.27		(tested with 27.1.0 which is actually 2.7.1.0)
	libstdc++.so.27			"
	libm.so.5		(tested with 5.0.5)

in the statically linked to Motif version and additionally to

	libXm.so.2.0

in the dynamically linked version. Due to the way, the Motif library was created
by our vendor, the loader will not look in /usr/X11R6/lib for the Motif
library where it is usually installed. The library (or a symbolic link to it)
must be present in /usr/lib.

All the above libraries except for libXm.so.2.0 are part of standard Linux
installations. The executable is in ELF format and will only run on ELF
linux distributions with appropriate ELF shared libraries.

The paths to all directories in which the above libraries are placed must be
searchable by the loader either as a default or through a specification of
the path in the LD_LIBRARY_PATH environment variable. Please consult a
Linux FAQ or guide and/or your shell documentation for details.

To check that all libraries are installed and accessible, type

	ldd acrossl

There should not be a (not found) entry in the list of dynamically linked
entries.

If the libraries can be found, then you are ready to run Across Lite except
for on-line help.[/I]

TIA again

---

### Post by DJ Wings on 2007-05-29
Try this:
```
sudo apt-get install libmotif3 lesstif2
```

---

### Post by ammmom on 2007-05-29
It didn't seem to work......

> -desktop:~$ sudo apt-get install libmotif3 lesstif2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmotif3 is already the newest version.
libmotif3 set to manual installed.
The following NEW packages will be installed:
  lesstif2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 584kB of archives.
After unpacking 1393kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe lesstif2 1:0.94.4-2 [584kB]
Fetched 584kB in 1s (470kB/s)    
Selecting previously deselected package lesstif2.
(Reading database ... 122431 files and directories currently installed.)
Unpacking lesstif2 (from .../lesstif2_1%3a0.94.4-2_i386.deb) ...
Setting up lesstif2 (0.94.4-2) ...

-desktop:~$ ldd acrossl
ldd: ./acrossl: No such file or directory


---

### Post by DJ Wings on 2007-05-29
Recompile it, then do it. Recompile it every time you do something you think might help.

---

### Post by ammmom on 2007-05-29
Bump.  Can anyone help me??????????:confused::confused::confused:

---

### Post by Ek0nomik on 2007-05-29
> **ammmom said:**
> It didn't seem to work......

Are you sure you are in the directory of the files?

For an example, say I have Example.tar.gz on my Desktop.  I extract the files to a folder called Example.

Now when I open my terminal I type:

```
cd Desktop/Example
ldd acrossl
```

You need to be sure you are in the directory where all the files reside.

---

### Post by ammmom on 2007-05-29
> **Ek0nomik said:**
> Are you sure you are in the directory of the files?

For an example, say I have Example.tar.gz on my Desktop.  I extract the files to a folder called Example.

Now when I open my terminal I type:

```
cd Desktop/Example
ldd acrossl
```

You need to be sure you are in the directory where all the files reside.

I wasn't in the file directory, as you know.  Thank you.  But it looks like I have a new problem:confused:
> -desktop:~/Desktop/acllinux.smotif.tar.gz_FILES$ ldd acrossl
/usr/bin/ldd: line 117: ./acrossl: No such file or directory
[email]desktop:~/Desktop/acllinux.smotif.tar.gz[/email]_FILES$ 


---

### Post by ammmom on 2007-05-29
Bump.  Hopefully, I'm almost finished.  Anyone?

---

### Post by ammmom on 2007-05-30
can any morning people help me? TIA.........

---

