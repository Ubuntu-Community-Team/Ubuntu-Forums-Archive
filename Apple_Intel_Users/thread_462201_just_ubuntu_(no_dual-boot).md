---
title: "just ubuntu (no dual-boot)?"
date: 2007-06-02
forum: Apple Intel Users
---

### Post by kzm. on 2007-06-02
hey mactels

i want to install ubuntu (64bit) on my macbook (2.16mhz core2coreduo) this weekend. i use ubuntu now for a year on my 4 years old medion machine, so i would consider myself a novice. 

i found some how-to's for edgy and dual-boot. which- besides the heat and networkcard- leaves me with two questions:
a) are there more recent how to's (for dummies like me)?
b) why should i have dual-boot / boot-camp? is it only for firmware updates? is there no other way (from osx life cd or something). i also read, that someone discussed dual-boot for win/linux makes sense when using virtualization. is this true (for osx, too)?

any opinions.. resources?

thanx a lot.

---

### Post by alloydwhitlock on 2007-06-02
A good head start on running Ubuntu by itself can be found here:

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)


It's fairly easy to follow, though make sure you are near an ethernet cord so you can do the wireless driver install.  




As for Bootcamp, it's not necessary since your system came with the newest version of the MacOS.  The terminal has the built-in commands on creating the necessary partitions you will need for Ubuntu.  This thread covers formatting using the terminal as well as installation:

[http://ubuntuforums.org/showthread.php?t=452262](http://ubuntuforums.org/showthread.php?t=452262)


If you are not comfortable using the terminal, Bootcamp is the easiest way to format the partition.  Just select all of the free space and format it for Windows.  When you start the Ubuntu installer, use the manual partitioner and knock out that space you made in Bootcamp with a small swap partition and your ext3 partition.

Hopefully someone running Ubuntu by itself can add more info...

---

### Post by kzm. on 2007-06-02
thanx.

the "community/MacBook" i knew, i guess thats the first to find.
the other one is new to me and very nice.. i followed the diskutil instruction on the osx terminal, but know i realize, i have to press the option key whenever i start my laptop to get linux.
hmm.. linux is my prime system so is it an option to install refit now afterwards to have some more control of the booting and set some other system than osx to default? 
does anybody know?

---

### Post by ivesjd on 2007-06-02
hrm, im not sure if you could install refit or not. You said you have to hold option to boot? If you deleted the OS X partition you shouldnt have to. Though I may be wrong. 
[http://ubuntuforums.org/showthread.php?t=435153](http://ubuntuforums.org/showthread.php?t=435153)
i think that is what your looking for.

---

### Post by alloydwhitlock on 2007-06-02
Directions on installing on the EFI partition:

[http://felipe-alfaro.org/blog/2006/09/19/installing-refit-on-the-hidden-efi-system-partition/](http://felipe-alfaro.org/blog/2006/09/19/installing-refit-on-the-hidden-efi-system-partition/)

This will allow you to run Ubuntu w/o OS X installed.  Since it's running in the EFI partition, the loader will automatically start.  If you are not comfortable doing this, don't do it.

---

