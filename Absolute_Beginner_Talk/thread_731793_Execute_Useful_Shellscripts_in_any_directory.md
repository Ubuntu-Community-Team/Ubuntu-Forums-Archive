---
title: "Execute Useful Shellscripts in any directory"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by spangeman on 2008-03-22
Hi All

Very new to Linux, which is why I am here :-)

I'm starting to build a list of useful commands in some shell scripts and I'd like to be able to execute them from anywhere in the file system using the terminal. At the moment I have to copy the script to the directory I want to run it in and then run it.

The scripts do things like 
+ unrar and then move all *.avi files to another disk
+ join files and then move them to a specified folder
+ mount and unmount network shares

So basically useful commands that I want to rexecute quickly in the terminal.

I had a quick play with the $PATH variable but that didn't seem to work. Could someone run me through what I need to do to achieve this?

Thanks
Spangeman

---

### Post by timbounceback on 2008-03-22
Either move it to a directory that is already in path, or put it in the path - make the it look like this:
$PATH=$PATH:/home/whatever/scripts

---

### Post by munkyeetr on 2008-03-22
copy it into **/usr/bin** directory, and make sure the executable bit is set, then you can run it form the terminal as you like. You can even remove any extension you had (.sh, .ksh, .pl, etc) so you don't have to type an extension with the name.

---

### Post by noynac on 2008-03-22
> **spangeman said:**
> Hi All
...I'm starting to build a list of useful commands in some shell scripts and I'd like to be able to execute them from anywhere in the file system using the terminal. At the moment I have to copy the script to the directory I want to run it in and then run it....Could someone run me through what I need to do to achieve this?...

Your home directory contains a hidden file with the name .bashrc. The last line in this file contains a path statement. Just add the directory that contains your scripts to this file. For example:

PATH="${PATH}:/home/username/myscripts: other/directories/in/path"

---

### Post by lloyd_b on 2008-03-22
A standard install puts a directory ("~/bin") at the beginning of your path.  This is intended as a place for "personal" executables.  So all you need to do is "mkdir bin" in your home directory, and then move those scripts into it.

Lloyd B.

---

### Post by spangeman on 2008-03-22
Thanks for the replies.

I have put the scripts in /usr/local/bin as this directory seems to be empty and that works fine.

However I like the idea of lloyd_b solution a lot better but I'm not fully sure which directory is the actual "home directory". Could you tell me exactly which directory I should be creating the new bin directory inside? Is it this one? (my username is spangeman):-

/home/spangeman/

That directory already has a bin directory but if I put scripts in there that does not seem to work.

The contents of my $PATH variable are:-

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by lloyd_b on 2008-03-22
> **spangeman said:**
> Thanks for the replies.

I have put the scripts in /usr/local/bin as this directory seems to be empty and that works fine.

However I like the idea of lloyd_b solution a lot better but I'm not fully sure which directory is the actual "home directory". Could you tell me exactly which directory I should be creating the new bin directory inside? Is it this one? (my username is spangeman):-

/home/spangeman/

That directory already has a bin directory but if I put scripts in there that does not seem to work.

The contents of my $PATH variable are:-

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

To verify which is your home directory:
```
echo $HOME
```
in a terminal window.

There's a block of code normally found in the file "~/.bash_profile" which *should* add "~/bin" (a.k.a. "/home/spangeman/bin", if "/home/spangeman" is your home directory) to the beginning of the PATH.  Note that this only occurs if the "~/bin" directory exists.

Take a look at the file "~/.bash_profile", and see if the following appears in it:
```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

If you don't see that block, add it, either there or in "~/.bashrc" (The difference is that ".bashrc" is read every time you open a terminal window, while ".bash_profile" is only read when you log in).

Lloyd B.

---

### Post by spangeman on 2008-03-29
Thanks Lloyd

Worked like a charm.

Regards
Spange

---

