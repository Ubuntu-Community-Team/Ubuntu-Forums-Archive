---
title: "qt4 installation"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by dunedust on 2007-03-27
ive been trying to install Qt/X11 Version 4.1.3.
ive done everything according to the install file 
however i have trouble understanding this last step 
my qt4 package is aldready installed but the program im tryiing to install (last.fm /interner radio/) fails to find qt4
so im assuming its something to do with this step
 

[I]4.  Environment variables

    In order to use Qt, some environment variables needs to be
    extended.

        PATH               - to locate qmake, moc and other Qt tools

    This is done like this:

    In .profile (if your shell is bash, ksh, zsh or sh), add the
    following lines:

        PATH=/usr/local/Trolltech/Qt-4.1.3/bin:$PATH
        export PATH

    In .login (in case your shell is csh or tcsh), add the following line:

        setenv PATH /usr/local/Trolltech/Qt-4.1.3/bin:$PATH

    If you use a different shell, please modify your environment
    variables accordingly.

    For compilers that do not support rpath you must also extended the
    LD_LIBRARY_PATH environment variable to include
    /usr/local/Trolltech/Qt-4.1.3/lib. On Linux with GCC this step
    is not needed.[/I]

thanks in advance
ps: i have qt3 installed

---

### Post by octoberdan on 2007-03-27
1. cd ~
2. gedit .bashrc
3. [add the line, "
    PATH=/usr/local/Trolltech/Qt-4.1.3/bin:$PATH 
    "to the end of the file]
4. source .bashrc

Does that work?

---

### Post by dunedust on 2007-03-28
hey thanks that really helped 
my qt4 version is now recognized
thanks again

---

