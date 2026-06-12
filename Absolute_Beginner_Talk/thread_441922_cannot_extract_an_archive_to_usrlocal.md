---
title: "cannot extract an archive to /usr/local"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by j_evenstar on 2007-05-13
it says: you do not have right permissions to extract archives in the folder "/usr/local"

i have to transfer it there since this is the installation instructions: 

> 
You may need to be root, depending on the permissions of the directories
where you choose to install Qt.

1.  Unpack the archive if you have not done so already:

	cd /usr/local
	gunzip qt-x11-2.3.0.tar.gz	# uncompress the archive
	tar xf qt-x11-2.3.0.tar	# unpack it

    This creates the directory /usr/local/qt-2.3.0 containing the
    files from the main archive.

    Rename qt-2.3.0 to qt (or make a symlink):

	mv qt-2.3.0 qt

    The rest of this file assumes that Qt is installed in /usr/local/qt.

---

### Post by jfinkels on 2007-05-13
If you want to do these commands in the /usr/local directory, you need to do so with root permissions. Preface your commands with 'sudo', like this:
```

*sudo* gunzip qt-x11-2.3.0.tar.gz # uncompress the archive
*sudo* tar xf qt-x11-2.3.0.tar # unpack it

```

Read more about root and sudo here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by j_evenstar on 2007-05-13
okay i know that but my problem is qt-x11-2.3.0.tar.gz is located on the Desktop and i can't copy it to the /usr/local directory. and when i tried downloading the file again and try to save it in /usr/local, the downloading doesn't continue,

---

### Post by jfinkels on 2007-05-13
> **j_evenstar said:**
> okay i know that but my problem is qt-x11-2.3.0.tar.gz is located on the Desktop and i can't copy it to the /usr/local directory. and when i tried downloading the file again and try to save it in /url/local, the downloading doesn't continue,
Try this if you want to copy that file from your Desktop to the /usr/local directory:
```
sudo cp /home/*yourusername*/Desktop/qt-x11-2.3.0.tar.gz /usr/local
```
Does this work (it should)? What kind of error message do you get, if any?

---

### Post by zvacet on 2007-05-13
```
cd Desktop
```
```
usename@localhost:~/Desktop$sudo cp  qt-x11-2.3.0.tar.gz /usr/local
```
```
cd /usr/local
```
```
tar zxvf qt-x11-2.3.0.tar.gz 
```

---

### Post by j_evenstar on 2007-05-13
> **jfinkels said:**
> Try this if you want to copy that file from your Desktop to the /usr/local directory:
```
sudo cp /home/*yourusername*/Desktop/qt-x11-2.3.0.tar.gz /usr/local
```
Does this work (it should)? What kind of error message do you get, if any?
thank you, it worked. i think i missed the sudo when i copied before.

> **zvacet said:**
> ```
cd Desktop
```
```
usename@localhost:~/Desktop$sudo cp  qt-x11-2.3.0.tar.gz /usr/local
```
```
cd /usr/local
```
```
tar zxvf qt-x11-2.3.0.tar.gz 
```
thank you. it worked too.

now, i have another question. 

> 1.  Unpack the archive if you have not done so already:

	cd /usr/local
	gunzip qt-x11-2.3.0.tar.gz	# uncompress the archive
	tar xf qt-x11-2.3.0.tar	# unpack it

    This creates the directory /usr/local/qt-2.3.0 containing the
    files from the main archive.

    Rename qt-2.3.0 to qt (or make a symlink):

	mv qt-2.3.0 qt

    The rest of this file assumes that Qt is installed in /usr/local/qt.


2.  Set some environment variables in the file .profile (or .login,
    depending on your shell) in your home directory. (Create the
    file if it is not there already.)

	QTDIR		   - wherever you installed Qt
	PATH		   - to locate the moc program and other Qt tools
	MANPATH 	   - to access the Qt man pages
	LD_LIBRARY_PATH	   - for the shared Qt library

    This is done like this:

    In .profile (if your shell is bash, ksh, zsh or sh), add the
    following lines:

	QTDIR=/usr/local/qt
	PATH=$QTDIR/bin:$PATH
	MANPATH=$QTDIR/doc/man:$MANPATH
	LD_LIBRARY_PATH=$QTDIR/lib:$LD_LIBRARY_PATH

	export QTDIR PATH MANPATH LD_LIBRARY_PATH

    In .login (in case your shell is csh or tcsh), add the following lines:

	setenv QTDIR /usr/local/qt
	setenv PATH $QTDIR/bin:$PATH
	setenv MANPATH $QTDIR/doc/man:$MANPATH
	setenv LD_LIBRARY_PATH $QTDIR/lib:$LD_LIBRARY_PATH

    After you have done this, you will need to login again, or
    re-source the profile before continuing, so that at least $QTDIR
    is set.  The installation will give an error message and not
    proceed otherwise.

i have done number 1, but number 2 is confusing. i don't know if i am .profile or .login...
any help again? thanks.

---

### Post by jfinkels on 2007-05-13
These are pretty complicated directions for a beginner...what are you installing, and have you checked to see if it's in the repositories (i.e. Synaptic)?

Step one, to add environment variables to your .profile file, type the following:
```
gedit ~/.profile
```
Then, add these lines:
```

QTDIR=/usr/local/qt
PATH=$QTDIR/bin:$PATH
MANPATH=$QTDIR/doc/man:$MANPATH
LD_LIBRARY_PATH=$QTDIR/lib:$LD_LIBRARY_PATH

export QTDIR PATH MANPATH LD_LIBRARY_PATH

```
Then type:```
source ~/.profile
```
And you should be all set to continue. Let me know if you would like further explanation.

I think there's probably a package just waiting for you to download it in the repos, so you don't have to go through all this trouble...

---

### Post by j_evenstar on 2007-05-13
i'm trying to install DevC++ for linux (that's what we use in school, although in Windows OS). and the install instruction says this:
> * First you need to make sure you have a installed all the C/C++ development packages when installing your distribution (those packages contains gcc, g++, make, standard include files and libraries). You should be able to obtain them on you distribution CD/web site.

* You then need Qt libraries installed. If you don't you can download the Qt package at : [ftp://ftp.trolltech.com/qt/source/qt-x11-2.3.0.tar.gz](ftp://ftp.trolltech.com/qt/source/qt-x11-2.3.0.tar.gz)
Follow the Qt INSTALL file after unpacking it and you should be able to installit quite easily.

* Now that your system is ready to run Dev-C++, type (as root) :

$> sh install.sh
or :
$> ./install.sh

This will launch the installation script. Follow the instructions and after the installation finish, change to your dev-c++ directory ($HOME/dev-c++ by default) and type :

$> ./devcpp 

Dev-C++ is now being launched, enjoy :)

i guessed that the c/c++ dev't packages is the build-essential package. so i installed it thru command line ```
sudo apt-get install build-essential
```
and now i'm installing the Qt libraries.

but..
```
QTDIR=/usr/local/qt
PATH=$QTDIR/bin:$PATH
MANPATH=$QTDIR/doc/man:$MANPATH
LD_LIBRARY_PATH=$QTDIR/lib:$LD_LIBRARY_PATH

export QTDIR PATH MANPATH LD_LIBRARY_PATH
```
where will i type this? in the .profile in getedit or in the terminal? and also where do i type this?
```
source ~/.profile
```
again, thanks for your help.

---

### Post by Vixis on 2007-05-13
Code:
> 
QTDIR=/usr/local/qt
PATH=$QTDIR/bin:$PATH
MANPATH=$QTDIR/doc/man:$MANPATH
LD_LIBRARY_PATH=$QTDIR/lib:$LD_LIBRARY_PATH

export QTDIR PATH MANPATH LD_LIBRARY_PATH

Must be written in gedit


> 
source ~/.profile

In the terminal.

---

### Post by j_evenstar on 2007-05-13
thanks, i've saved it in my home directory. so can someone help me with this? 
> After you have done this, you will need to login again, or
    re-source the profile before continuing, so that at least $QTDIR
    is set.  The installation will give an error message and not
    proceed otherwise.

3.  Install your license file as $HOME/.qt-license.
    For the free edition, you do not need a license file.  For Professional
    and Enterprise editions, install your license file as described in your
    distribution.

log in again -- meaning reboot the computer? and how about number 3? thanks again...

---

### Post by Vixis on 2007-05-13
You already have made resource by this command:
source ~/.profile

3.For the free edition, you do not need a license file. But if it is Professional
and Enterprise editions, you need to make new directory and copy license file there:
mkdir $HOME/.qt-license
cp path_to_the_license_file ~/.qt-license/

---

### Post by j_evenstar on 2007-05-13
okay. thanks.
however, upon running devc++,
```
jillian@jillian-desktop:~$ cd /home/jillian/dev-c++
jillian@jillian-desktop:~/dev-c++$ ./devcpp
./devcpp: error while loading shared libraries: libqt.so.2: cannot open shared object file: No such file or directory
jillian@jillian-desktop:~/dev-c++$ sudo ./devcpp
./devcpp: error while loading shared libraries: libqt.so.2: cannot open shared object file: No such file or directory
jillian@jillian-desktop:~/dev-c++$
```
i don't know if you're familiar with this. but just in case, i'm asking it. and what is libqt.so.2?
thanks again.

---

### Post by jfinkels on 2007-05-13
> **j_evenstar said:**
> okay. thanks.
however, upon running devc++,
```
jillian@jillian-desktop:~$ cd /home/jillian/dev-c++
jillian@jillian-desktop:~/dev-c++$ ./devcpp
./devcpp: error while loading shared libraries: libqt.so.2: cannot open shared object file: No such file or directory
jillian@jillian-desktop:~/dev-c++$ sudo ./devcpp
./devcpp: error while loading shared libraries: libqt.so.2: cannot open shared object file: No such file or directory
jillian@jillian-desktop:~/dev-c++$
```
i don't know if you're familiar with this. but just in case, i'm asking it. and what is libqt.so.2?
thanks again.

libqt.so.2 is a shared library file. 

First let's find out if your environment variables were exported correctly. Type the following in the terminal:
```

echo $LD_LIBRARY_PATH

```
tell us the output.

To find out if ilibqt.so.2 is actually where it's supposed to be, type the following in the terminal:
```

ls -l /usr/local/qt/lib | grep libqt

```

This will list the contents of the qt library directory and filter the results by only outputting lines containing the string 'libqt'.

---

