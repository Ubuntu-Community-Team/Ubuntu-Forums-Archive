---
title: "install and running a tarball"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Trindol on 2008-01-25
OK, I have installed tarballs before but this one is different and since I'm very new to linux I'm confused. I extracted the contents to the desktop and tried the normal ./configure command but it did nothing. There is no source folder in the extracted files.

I'm talking about the emulator pSX. Even though I downloaded the "linux version 1.13", the package contains only an executable and some text files. When I navigate to the extracted folder in the terminal and run "./pSX" the program runs fine. However if I remove the folder from the desktop it no longer works (not too surprising)

I think I read that it is possible to run programs without installing them. Is this what I'm doing? I'm not really sure. I would like to have it so I can just type "pSX" in the terminal to run it, not navigate to a folder to first. Where should I move the pSX folder to, or how should I install it properly?

---

### Post by gvartser on 2008-01-25
Install it using synaptic instead.

Search for "psx"

Best regz,

*err got to learn to read the post better before answering them*

/g

---

### Post by Trindol on 2008-01-25
Thanks but I'm pretty certain it is not in Synaptic.

---

### Post by gvartser on 2008-01-25
Sry, didn't read your post accurate.

No you do not have to install anything (Its already pre-compiled), just extract it to a folder of your choice and then add that folder into your path.

Then you can start the psx from anywhere, (IOW, you do not need to start it from the specific folder where it is placed)

```
#) pSX /usr/psxgames/mygame.bin
```

Just make sure you have the following requiered packages installed:
Under Linux pSX requires the following shared libraries/packages :

	OpenGL
	ALSA
	GTK
	GTKGLEXT
	libxml2

/g

---

### Post by Trindol on 2008-01-26
Ok, I think I understand what you're saying but I'm not sure how to do it exactly. By adding it to my path, do you mean modifying the file ~/.profile?

Right now it says this:

> # ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

---

### Post by gvartser on 2008-01-26
Yes you could add it to your .profile.

Add the following entry at the bottom of you .profile:

```
export PATH="${PATH}:<path/to/the/pSX/folder>"
```

When you are done editing, log out & in again from your shell or just start a new terminal and test to run the program.

What i generally do on my machines or places where i have a shell is to create an additional profile file, call it what you want, I call it ".<login_name>_addons"
And in that file I add all my customizations that i want in my shell, like aliases, functions etc.

[U]Here is an little example:
[/U]
1) Create the .<login_name>_addons file in the home dir.

1.1) Add all customizations you would like to have:
```
Example:
PATH="${PATH}:<path/to/the/pSX/folder>
alias sl=ls
```

2) Edit your .profile to include the file created in step 1, to be loaded by default when starting a new shell.
Add the following at the bottom of the file:

```
# Load my shell config addons:
if [ -f ~/.< login_name>_addons ]
then
     . ~/.< login_name>_addons
fi
```

3) Then use this file to save all your tweaks, the nice thing is then that you have created a file that is easy to export to other linux systems where you have access.

/G

---

