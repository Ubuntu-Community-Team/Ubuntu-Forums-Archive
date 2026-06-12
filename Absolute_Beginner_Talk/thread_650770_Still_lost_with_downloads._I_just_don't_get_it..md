---
title: "Still lost with downloads. I just don't get it."
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Joseph5000 on 2007-12-26
I extract a new program in a from me created folder on the desktop. Now i open this folder and I am confronted with more folders and files. Which ones do I have to open .(terminal and Jesus would I know which one) do get the stuff running. I got a hint of a webpage:
How to install ANYTHING in Ubuntu!, but that didn't help me at all. I am about to reinstall MS. Not because I think it is a great thing to have, but at least it seems consumer friendlier, plus,..it even seems to be faster then Ubuntu.

Argh, I am frustrated

---

### Post by Joseph5000 on 2007-12-26
THese are the folders I get

/home/joseph/Desktop/Programs/cire-0.14.0/autom4te.cache
/home/joseph/Desktop/Programs/cire-0.14.0/src
/home/joseph/Desktop/Programs/cire-0.14.0/aclocal.m4
/home/joseph/Desktop/Programs/cire-0.14.0/autogen.sh
/home/joseph/Desktop/Programs/cire-0.14.0/CHANGES
/home/joseph/Desktop/Programs/cire-0.14.0/config.log
/home/joseph/Desktop/Programs/cire-0.14.0/configure
/home/joseph/Desktop/Programs/cire-0.14.0/configure.ac
/home/joseph/Desktop/Programs/cire-0.14.0/COPYING
/home/joseph/Desktop/Programs/cire-0.14.0/CREDITS
/home/joseph/Desktop/Programs/cire-0.14.0/cvs2cl.pl
/home/joseph/Desktop/Programs/cire-0.14.0/depcomp
/home/joseph/Desktop/Programs/cire-0.14.0/HACKING
/home/joseph/Desktop/Programs/cire-0.14.0/INSTALL
/home/joseph/Desktop/Programs/cire-0.14.0/install-sh
/home/joseph/Desktop/Programs/cire-0.14.0/Makefile.am
/home/joseph/Desktop/Programs/cire-0.14.0/Makefile.in
/home/joseph/Desktop/Programs/cire-0.14.0/missing
/home/joseph/Desktop/Programs/cire-0.14.0/mkinstalldirs
/home/joseph/Desktop/Programs/cire-0.14.0/README
/home/joseph/Desktop/Programs/cire-0.14.0/TODO

---

### Post by taurus on 2007-12-26
Try

```
cd ~/Desktop/Programs/cire-0.14.0
```
Now see what INSTALL says.

```
cat INSTALL
```
You probably have to build it and then install it with

```
sudo apt-get update
sudo apt-get install build-essential
./configure
make
sudo make install
```

---

### Post by sub2007 on 2007-12-26
First of all, I'd check to see if the package is in Synaptic. That cuts out a lot of the hard work for you in 90% of the cases.

Next check the developers website, but look at whether there is a version in .deb format. Double-click that, enter your password and it will bring up the package installer. Then just hit "Install Package" and the installation will go through.

If, and only then I'd consider compiling it from source (that's unless I wanted something bleeding edge) and there may be a guide somewhere to compile it. BUT for most of the common software it will be in repositories or at least have a .deb version.

EDIT: sorry, didn't have the second post when I started replying and thought this was a generic how to install software.

Just to add though that after running ./configure you may well get error messages (mainly relating to dependencies). It will throw out something like "Package ... not found". If you get any error messages then the package won't make. You will need to search synaptic for any packages not found, and then install them. After that run ./configure again.  If it fails on the same package again then you may have to install the dev package (package-dev). Keep running ./configure until it finds no errors (and it prints a list of folders at the end). It may then instruct you to make (not always) and you can proceed to the next steps (make; sudo make install)

---

### Post by Joseph5000 on 2007-12-26
Thanks, I went in over the Terminal and did this. Something happened, but not a lot. i feel like a moron. It is nice of you to help me, but I just don't understand the whole spiel and I feel being at the mercy of somebody again. Like MS. How can I learn the whole thing. Truly from scratch. For real idiots, which I believe I am not.
How do I figure out in this Babylon of files which one will do the trick and all that.

---

### Post by oldos2er on 2007-12-26
Starting off compiling programs when you're brand new to Linux is frustrating, I know. I second the suggestion to use Synaptic Package Manager if possible. Maybe this will help: [https://help.ubuntu.com/7.10/add-applications/C/index.html](https://help.ubuntu.com/7.10/add-applications/C/index.html)

---

### Post by oldos2er on 2007-12-26
i checked out "cire" and it's not in Ubuntu's repositories.

 So you've got the source in /home/joseph/Desktop/Programs/cire-0.14.0 . There's info in the README file, and INSTALL too.

 In Ubuntu, before you can compile source code, you need to install the build-essential package. Either search for it in Synaptic, or type "sudo aptitude install build-essential' in a terminal.

---

### Post by GGLucas on 2007-12-26
Unlike in windows, where each program comes with an installer, with most Linux programs, you only download the source code, and you will need to use this code and turn it into a program (this is called compiling), a lot of software also has a file with the .deb extension which you can use to install it directly, somebody else will already have compiled the source code and turned it into a "package" (kind of like an installer), but with some software, such as this one, nobody has, and you will need to compile it yourself.

The standard method for compiling a program is to use the following command:
```
./configure && make && sudo make install
``` 
This will work with 99% of the software, most programs will have a file called INSTALL with it which says what you need to do to compile it, you can open it in any text editor.


It seems that for this program, you should do the following.

Change the directory to the one the files are in first:
```
cd ~/Desktop/Programs/cire-0.14.0
```

First, run the configure script, this is used so that when you start compiling, it will know what to do.
```
./configure
```

Secondly, you need to actually compile all the source code you got into an executable program file.
```
make
```

After this, you do:
```
sudo make install
```
This will put all the files in the right directories for it to run.

Now, you can run the program by typing
```
cire
```

in a terminal, or pressing Alt+F2 and typing "cire" (you can create a menu item/launcher by creating a new one with the command "cire" too)

---

### Post by Joseph5000 on 2007-12-26
I moved the download to trash and deleted it. Downloaded it again. Again to the Destination folder on my desktop. I opened Synaptic and searched for the package. And then the package sits on the left screen side and shows me the middle finger. Sorry guys. MS worked for me, even if Gates sucks. THanks, but I got work to do

---

### Post by Casual Fan on 2007-12-26
I feel his pain, but Linux is not Windows. You can't learn French, and then try to speak German with the same grammar rules as French. It sounds like the o.p. didn't read any tutorials or anything. Like I said, I sympathize, but you have to make an effort to learn.

---

### Post by jas0 on 2007-12-26
Use synaptic to search and install the following package:

> build-essential

if you are unable to find it, do the following:

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

After this, go back to the beginning of this post and try again.

After you do all of this, follow cire's own build instructioins:

> 
Installing Cire: 

1: Configure: 

	To Configure, type './configure <options>'. The Options are as follows:

		--with-gtk-ui=<yes/no>
			Controls Whether the GTK UI Is Built. Default: Yes

		--with-ncurses-ui=<yes/no> 
			Controls Whether the Ncurses UI Is Built. Default: Yes

		--with-text-ui=<yes/no>
			Controls Whether the Text UI Is Built. Default: No

2: Make:
	
	To Make, simply type 'make'

That's It. It will generate an Executable called cire, which you can do
whatever you want with.

IMPORTANT: If you want us to be able to better help you, copy and paste any confusing output you see in your terminal window as you're following the instructions.

Good luck!

---

### Post by rgb1701 on 2007-12-27
Assuming you meant

[http://cire.sourceforge.net/screen.php](http://cire.sourceforge.net/screen.php)

all I did was download the tar.gz file just like the millions of .zips I've dl'd for 20+ years on DOS/WIn, unzipped like the the millions of others, read the INSTALL text file:


Installing Cire: 

	Use the ./build.pl Perl Script, if it doesn't work make sure it is chmod'd
	executable.	For more information, type "./build.pl help".


and double clicked the build.pl file and the executable was created in the same directory- no different than double clicking an "installcire.exe" on Windows.

This was in Linux Mint (Ubuntu variant) and its default file manager, Thunar (i.e. File Explorer in Win)

I would only fault the developer for not putting the instructions in the README and/or naming the build script "install.pl" for people used to "install.exe" on WIndows, but it's really no more clicks or logical steps to install vs any WIndows .zip download.

---

