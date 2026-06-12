---
title: "install special file format"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Franswa_CS on 2007-04-22
how to install tar.gz , tar.bz2 , tgz files on ubuntu?

---

### Post by viciouslime on 2007-04-22
I am guessing you have downloaded the source code for something?

The usual steps are to extract it somewhere, change to that directory in the terminal then run:
./configure
make
sudo make install

You might however, have to install some dependencies first. There should be a readme inside the tar.gz file. If you tell us which program you're trying to install we can probably offer more help.

---

### Post by Franswa_CS on 2007-04-26
i am trying to install vlc player but using deb package is waste of time as it requires a lot of dependency files (this is what me make hate deb package) so if u can help me please help.

if u know any site that could list all dependency files for deb package (instead of logging to the internet each time i found that i need a dependency package) please tell me.

thanks for your help

---

### Post by KaeseEs on 2007-04-26
Unfortunately, installing from source (that's what's in the tarball) won't help you much with this particular problem - VLC has the same dependencies no matter how you install it, but if you do it yourself instead of with a .deb, you won't get a warning if you try to install without them, but rather the program will crash.

Luckily, if you go to packages.ubuntu.com, it will show you all the dependencies for any package you look up.  Alternatively, you can use the command```
aptitude show *packagename*
```, which will display a lot of information about the package, including its dependencies.

Now, a better way to do this is to automate the process of fetching dependencies.  Thankfully, Ubuntu will gladly do this for you as well.  Try the command ```
sudo aptitude install *packagename*
```which will install a program for you, including all its dependencies.  Note that, for VLC, you'll need to enable the 'universe' software collection to do this, but that's not too hard, either:```
sudo gedit /etc/apt/sources.list
```
When the file opens, there will be a section that says, 'uncomment the following to enable universe' or something to that effect; delete the '#' symbols in front of the lines below that which start with 'deb', and save the file.  Next, run:```
sudo aptitude update && sudo aptitude install vlc
``` which will install VLC for you.

Finally, if you absolutely need to install from a tarball (.tar.gz, .tar.bz2, .tgz), it's done in a few steps.  For a .tar.gz or .tgz file:```
tar -xvzf *file*
./configure
make
sudo make install
```

For a .tar.bz2 file:```
tar -xvjf *file*
./configure
make
sudo make install
```

Best of luck!

---

### Post by Sef on 2007-04-26
Read [How to install anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

