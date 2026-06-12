---
title: "[SOLVED] &amp;quot;Couldn't find package....&amp;quot;"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Flyvapnet on 2007-08-24
What could be simpler than installing a package, when the Wiki insists all one need do is type "sudo apt-get install [package name]" into the terminal?  Well, for starters, I keep getting a "Couldn't find package...." response.

All right, then, where is the package supposed to be located so that Ubuntu 7.04 Feisty Fox *can* "find the package"?  I've moved the package from my Dowloads folder to my Home folder (the File System refuses the package because I apparently don't have permission to "write" there) and back again, I've put it on the Desktop, I've opened the file via the Archive Manager (which doesn't do a damned thing in the way of installing anything) and none of these processes seem to be good enough for this operating system.

By the way, this package which is apparently invisible to Ubuntu 7.04 Feisty Fox is "pidgin-extprefs-0.7.tar.gz" in its original form and "pidgin-extprefs-0.7" in the folder form which the Archive Manager produces.  I've tried both names in all those locations mentioned above, moving both the package and the folder here and there in a futile attempt at getting this operating system to "find" it.

Can somebody please tell me, exactly, how such a package is *really* installed as opposed to the Wiki's incorrect instructions?  Thank you very much!

:confused:

=^..^=

---

### Post by bobplano on 2007-08-24
the wiki is refering to how you can usually install packages which are on the internet like sudo apt-get install firefox. tar.gz is different. you need to compile it. make sure you have the build-essential package install (sudo apt-get install build-essential) and then navigate to where the pidgin directory is, the one you are trying to install. run
```
./configure
make 
sudo make install
```

that should install it and you're good to go

---

### Post by annda on 2007-08-24
to avoid confusion and generally learn more about installing software, you can start with reading this (rather general):
[https://help.ubuntu.com/community/SoftwarePackagingFormats](https://help.ubuntu.com/community/SoftwarePackagingFormats)

and this is an overview of related articles on [ubuntu user documentation page]("https://help.ubuntu.com/community/"):
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by Flyvapnet on 2007-08-24
Thank you very much, **bobplano** and **annda**, for your very helpful suggestions!  I think, due to your help, I've got this figured out now.

:KS

=^..^=

---

