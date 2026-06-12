---
title: "source install"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by ckeylon on 2005-10-15
I need a link explain the code needed install .zip and .tar files

**User is one of my convertees , He wants to understand how to install from source , both on .tgz, tar.gz. and .zip's. Go easy guys. -- KB**

---

### Post by manicka on 2005-10-15
Okay first you need to extract the tar or zip file.

You can do this by just right clicking the file and choosing 'extract archive'

If it's a file that you want to compile a program for you should see a file called configure. If so this means you can compile the program.

Before starting we need to make sure you have the necessary packages installed to compile packages.

In a terminal type

```
sudo apt-get update
suso apt-get install build-essential
```

This will install the packages you need to compile source packages.

Now, in the terminal change to the directory that the archive created


then run

```
./configure
make
sudo make install
```

All going well that should do do it

to uninstall

type 'make uninstall' in the same directory

---

### Post by 11hjpphty76lkjj on 2005-10-15
**Duped Post. KB**

Below point is important though.

In theory it's always best to check synaptic first for software.  Make sure to turn on all of the respositories.  This is the easiest method..

System>Admin>Synaptic

Settings>Repos>Settings>check "Show disabled...">Close>check mark all of the repos>Okay>Click Reload.

Although I could be incorrect.

---

### Post by 11hjpphty76lkjj on 2005-10-15
Oops sorry manicka.  Good show sir!

---

### Post by seethru on 2005-10-15
optionally, instead of "make install" you can use "checkinstall"
```
sudo apt-get install checkinstall
```

And instead of using make install after make, just use

```
sudo checkinstall
```

This creates a .deb and inserts it into the Synaptic installed programs database, making for easy removal.

---

### Post by manicka on 2005-10-15
Good one, I always use checkinstall as well :)

---

