---
title: "Compiling and Links"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by davebridges on 2008-01-06
Hi everyone,

I am relatively new to Ubuntu.  One of the programs I need for work (ImageJ) required me to download a tarball, extract it then compile (?) it using ./run.  It works fine, but i would like to understand better what I did, and also find a way to do this via a launcher (rather than having to move to that directory and do ./run whenever I want to run the program.  I have a few other programs that are similar, and I am unfamiliar with the make/configure syntax.  Anyone care to explain it to me :)

---

### Post by PeterJS on 2008-01-06
In building most things there are 3 tools, automake, make, and gcc. The first step, which most people don't ever see because the programmers run it and then make any changes needed for the configuration to be correct. Automake looks at the program and what libraries and system components it uses and then generates the configure script that the user will use when they unpack the tar ball. The reason this is uesful is that not all systems are the same, something programed on Red Hat will work on ubuntu, but won't necessarily know where to look for things. So the configure scripts iron out those differences. One of the things done by the configure script is generating the Makefile used by make to determine how to build the project.

The next step make, reads the Makefile which tells it where all the program source components are and how gcc should assemble them. The last step make install, again invokes make but tells it to look for the install instructions in make file, which usually consist of copying files to their final location and any other miscellaneous configuration set up needed.

---

### Post by davebridges on 2008-01-06
great... thanks for the info.  but once i have done it once, all the files are in their final location right.  so is there an easy way to make a permanent link so that i dont need to do ./run each time?

---

### Post by PeterJS on 2008-01-07
Some packages will do this automatically, and some don't, looks like your found one of the ones that doesn't. You've got a couple of options:

1) Copy the whole mess in to /opt/ and symlink the program itself in to /usr/local/bin

1.5) Leave it where it is and symlink it in to /usr/local/bin, this is workable but generally considered poor taste and not a sound idea

2) Leave it where it is, and create a shortcut on one of the panels or the desktop that refers to it by it's entire path.

---

### Post by hyper_ch on 2008-01-07
What program is it actually? Are you sure it's not in the repos?

Basically compiling would be as following:

(1) Get compiler and stuff
```

sudo apt-get install build-essential

```

(2) Extract the compressed program and check if there is an install guide or readme with additional information.

(3) Run the following three commands in the extracted folder of the application:
```

./configure
make
sudo make install

```

Depending on what they are requiring you there will be errors and you'll have to install more libraries. Also if a library is installed and it says it's still missing, you are like to be required to install the  -dev  version of that library also.

---

### Post by PeterJS on 2008-01-07
My only comment on the above, is that make install certainly works, but checkinstall is better. What checkinstall does is that is sets up a fake environment for make install to run in, and then builds a deb package from that. This allows you to uninstall things cleanly with apt. The tools are there why not use them.

---

