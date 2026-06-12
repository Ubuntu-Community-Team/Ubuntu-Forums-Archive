---
title: "dvd data disc, can anyone help me?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by h-town on 2007-11-10
HI

I just want to say that I've had ubuntu on my laptop for 2 days and I'm SHOCKED at how much better it is than windows. I should have converted years ago to linux, but I always thought that it would be boring to use, arcane, and not intuitive whatsoever. I got to admit- Ubuntu totally [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

However I have one problem (probably the first of many) I've backed up all my personal files and mp3s and whathaveyou to a dvd data disc through windows, but I can't seem to be able to load any of the files into my laptop anymore. A dialog window pops open that tell me it couldn't mount the udf volume. Can anyone direct me towards solving this problem so I can fully enjoy a beautiful operating system that (seems to) rarely crash like my putrid vista did 20-30 times a day?? 

I also want to stress that I'm very new to ubuntu and I'm not familiar with the command line feature of the OS, maybe you also know of a great tutorial on using this so I can teach myself how to solve problems in the future? 

BTW- I say that in a few years Linux is going to take over the world, i hope at least.

---

### Post by matthewcraig on 2007-11-10
Have you checked that the disk is valid and not corrupted?  A lot of times they get burned wrong.  I do not think Ubuntu has a problem mounting UDF volumes generally.

This link might help you, otherwise:
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233)

---

### Post by niteshifter on 2007-11-10
You may need to install the package "udftools". Use the Synaptic Package Manager (System -> Administration -> Synaptic Package Manager) and it's search function: If there is no text in the Installed Version Column, it's not installed.

If that doesn't work you could use a Windows machine w/ DVD drive and a USB thumb drive and move your data via the thumb drive.

---

### Post by h-town on 2007-11-10
good call on udftools. there was no text in the installed version column so i guess you found the problem, so-  i looked it up and found a download for it 

[http://sourceforge.net/project/showfiles.php?group_id=295](http://sourceforge.net/project/showfiles.php?group_id=295)

i hope it works! I don't know what to do next, but i'm reading the documentation for ubuntu and i figure i'll eventually get to the part that tells me how to handle a file like this. I really appreciate the help. I'll reply to this thread if all goes well. thanks again!

---

### Post by niteshifter on 2007-11-10
No need to download it from sourceforge. While in Synapic Package Manager:

Find udftools (click the search button in Synaptics' toolar, enter the text "udftools")
Click on the box to the left.- a dialog should pop up.
Click "Mark for Installation" in that dialog.
Click the Apply button in Synaptics' toolbar.

Your machine should trundle along, download what you need and install it, all "automagically".

---

### Post by h-town on 2007-11-10
after I clicked apply and it attempted to install udftoools i got an error message:

E: /var/cache/apt/archives/udftools_1.0.0b3-12_i386.deb: unable to open files list file for package `rsync'

It says that udftools is now installed but it still doesn't work. I did it a second time and the same results occurred. 

I've also tried putting a blank dvd in the drive and a  dvd dialog window popped up. so the drive works fine- it just can't read a windows formated dvd data disc.. I"ll google the error message and look around for a solution.

Do you think I need to download that file now?

---

