---
title: "What are these files, and where did they come from??"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-07-07
;)I installed from the 6.10 LiveCD earlier this week, and last night I let it do the upgrade online to 7.04.  When that finished, I did a "ls -al" so I could see all the files, including hidden, on my desktop.  I've got some files there I don't understand.  Can someone tell me what these are, where they came from, and if it is OK for me to delete them?

dave@dave-ubuntu:~$ cd Desktop
dave@dave-ubuntu:~/Desktop$ ls -al
total 1088
drwxr-xr-x  3 dave dave   8192 2007-07-07 04:28 .
drwxr-xr-x 33 dave dave   4096 2007-07-07 04:28 ..
-rw-r--r--  1 dave dave   4577 2006-10-10 08:47 bar-00bd7f8e4a.desktop
-rw-r--r--  1 dave dave 699421 2007-07-06 07:03 desktopguide.pdf
-rw-r--r--  1 dave dave    285 2007-07-05 17:16 eek-005420fecf.desktop
-rw-r--r--  1 dave dave   6631 2006-10-07 08:47 eek-0069eb9826.desktop
-rw-r--r--  1 dave dave   6883 2006-12-06 23:47 eek-006a2fe0d9.desktop
-rw-r--r--  1 dave dave   7327 2006-12-06 23:47 foo-00973e1bcf.desktop
-rw-r--r--  1 dave dave   3961 2006-12-06 23:47 frobate-00184f859b.desktop
-rw-r--r--  1 dave dave   4877 2006-12-06 23:47 gegl-00d2c9b074.desktop
-rw-r--r--  1 dave dave   4849 2006-10-02 19:48 larry-00fc43db45.desktop
drwxr-xr-x  2 dave dave   4096 2007-07-06 07:26 .libs
-rw-r--r--  1 dave dave 328695 2007-07-07 04:24 vmware-any-any-update110.tar.gz
dave@dave-ubuntu:~/Desktop$

Thanks!!

---

### Post by jmfa59 on 2007-07-07
I think It is related to file permission I hope someone can explain more.

---

### Post by steve.horsley on 2007-07-07
They're not there on a standard Feisty desktop. 

Do you see them when you look in your Desktop folder with nautilus? What do they look like?

Try (from the command line) 
cat eek-005420fecf.desktop
and see what the contents are - that should give a clue. .desktop files are program launcher files (like windows shortcut files) and are text based.

---

### Post by anewguy on 2007-07-07
They don't show in nautilus, even if I have the "show hidden files" option on.  They don't show on a regular "ls" from the command line.  They do show when I do a "ls -al".  I've looked at the files, and while they are text, some appears to be a different language, and what the files actually do I can't tell.  They do seem to match in number those items that are in the "applications" menu that I asked to be on the desktop (8 of them).  The PDF I downloaded about linux.  What's a little weird also is nothing shows for the VMware Server starter that is on my desktop.  

Perhaps the 8 weird files are actually the random names generated for those things I requested by placed on the desktop?;)

---

