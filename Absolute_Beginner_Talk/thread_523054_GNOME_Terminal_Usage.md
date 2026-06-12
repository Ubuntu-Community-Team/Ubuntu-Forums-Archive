---
title: "GNOME Terminal Usage"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by rubab on 2007-08-11
I have a file named "ttf-arphic-ukai_0.1.20060108.orig.tar.gz" & "crossover.linux.pro-6.1.tar.bz2" 

These files are on my NTFS partition . I am willing to try crossover but i am not sure where to copy these files and how to use them .
I installed Ubuntu for the first time a few hours ago.
Any solutions please.

---

### Post by SOULRiDER on 2007-08-11
tar.gz and tar.bz2 files are compressed files, just like zip or rar.

Could you give us more information on those files and what it is youre trying to install?
I believe its important that you read this:
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

and this guide for mounting NTFS partitions:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Linux can be a bit scary at first simply because its different, but after a week when you start to understand things better you will see how much better it is and will start to figure out things by yourself.

---

### Post by BobCFC on 2007-08-11
tar.gz files are the old equivalent of zip files on unix.  

tar.bz2 files are similar but newer and slightly smaller like "zip2"


EDIT: I forgot to say that in Ubuntu you can just double click on a compressed file to open a program like winzip and then choose extract.



to extract from a tar.gz file to the current directory use:

```

tar zxfv somefile.tar.gz

```

The options stand for Zip, eXtract, File and Verbose (print results to screen)


or to put it in another place add the destination directory at the end:


```

tar zxfv somefile.tar.gz /to/some/other/place

```


To extract from the bz2 file it is almost identical except drop the z form the options:

```

tar xfv somefile.tar.gz

```

NOTE:  you can use the TAB key to autocomplete the filename; you do not have to type the whole thing.

You will have to read the instructions to install Crossover.. it may have a README file or look on the website.  If there isn't a simple .deb file on the website that you can double click on to install you may have to compile it the old fashioned way.

To do this change into the directory made after the extracting zip file:

cd crossover.linux.pro-6.1

Then:
```

./configure
```

To begin the install process.  If no errors type
```

make
sudo make install
```


If you have never complied a program before you may need to install the C compiler first

sudo apt-get install build-essentials

I would look for a .deb file of crossover first, they are precompiled and much easier to install

---

