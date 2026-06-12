---
title: "Create Install/Apt-Get script to run after install"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by kleptos on 2006-01-09
After i install Ubuntu, there are a few packages i like to install with the help of apt-get. This is so easy and so wonderful that ubuntu might become my main os now. Is there a way to write and run a script to install all the packages i like to install? Using the apt-get command can get quite long and one typo can leave a headache. I want to install the main ubunto os then run some sort of a script that runs all the installs i want using apt-get. Is this possible? Is it easy? 
Thanks!

---

### Post by Arktis on 2006-01-09
Open up gedit.  Make sure the first line in your script is:

#!/bin/sh

On the next line, type out

sudo apt-get install name1 name2 name3 name4, etc, etc.

Make sure you spell everything correctly!  You can enter the names of however many packages you need, just make sure that no matter how many package names you enter, that they are all on the same line: line 2.  Once you are finished, save the file to your home directory as something like aptscript.sh, chmod it to be executable and you're done.  Save it to some form of external media like a thumbdrive, floppy, or backup cd.  Before you do that, you may want to test it out with the command ***sh aptscript.sh*** just to see if you spelled anything wrong.  apt-get should tell you if you did by claiming it couldn't find nameX.

---

