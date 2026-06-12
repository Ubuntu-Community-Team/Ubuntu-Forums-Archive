---
title: "OPera"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by SOG420 on 2006-03-09
First of all I hope that this is the appropriate location for this post. If not I sincerely apologize. Second I am blown away with the level of support and help you guys give spending one day with Ubuntu has rivaled a decade of WIndows. Ok the point now
 I am trying to install OPera using the instructions found @    	Ubuntu Forums > Ubuntu Breezy Badger 5.10  > Customization Tips & Tricks
Reload this Page General - HOWTO: Nice looking Opera
>>>> 

This is the commands and the result
>>>
wm@ubuntu:~$ sudo dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb
dpkg: error processing opera_8.50-20050916.6-shared-qt_en_etch_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera_8.50-20050916.6-shared-qt_en_etch_i386.deb

---

### Post by Sutekh on 2006-03-09
[QUOTE=SOG420]
wm@ubuntu:~$ sudo dpkg -i opera_8.50-20050916.6-shared-qt_en_etch_i386.deb
dpkg: error processing opera_8.50-20050916.6-shared-qt_en_etch_i386.deb (--install):
 **cannot access archive: No such file or directory**
Errors were encountered while processing:
 opera_8.50-20050916.6-shared-qt_en_etch_i386.deb[/QUOTE]
Are you in the correct folder?  Where did you put the opera.deb?

Also check for typos in the command.  

There is an easy way to type crazy long filenames using the auto-completion ability of the TAB button.

Start typing the filename then press TAB, if there is a unique file/folder starting with those letters then TAB will finish it for you ---> no typos.



So first check that the opera.deb is in the directory you are working from.   
```
pwd
```Will tell you the working directory

And
```
ls
``` to list the files in the working directory.

Then use TAB to ensure you use the correct command.  Try
```
sudo dpkg -i opera_
```Then press TAB to finish it off.

---

