---
title: "Why no java runtime in Firefox 3.0"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2008-02-27
I have installed the java runtime enviornment in Firefox and Firefox 2.0 works ok.  How can I get it to work in Firefox 3.0?

---

### Post by libertas on 2008-02-27
you need to install the plugin "Java"

---

### Post by libertas on 2008-02-27
by that i mean that you need to do this:
Tools>Add ons>Get Extensions
this will bring up a tab in your browser

click on plugins, and find java

follow the instructions then install java

---

### Post by johnfarrow on 2008-02-27
when I do I get this.....error: Failed dependencies:
        /bin/basename is needed by jre-1.6.0_03-fcs.i586
        /bin/cat is needed by jre-1.6.0_03-fcs.i586
        /bin/cp is needed by jre-1.6.0_03-fcs.i586
        /bin/gawk is needed by jre-1.6.0_03-fcs.i586
        /bin/grep is needed by jre-1.6.0_03-fcs.i586
        /bin/ln is needed by jre-1.6.0_03-fcs.i586
        /bin/ls is needed by jre-1.6.0_03-fcs.i586
        /bin/mkdir is needed by jre-1.6.0_03-fcs.i586
        /bin/mv is needed by jre-1.6.0_03-fcs.i586
        /bin/pwd is needed by jre-1.6.0_03-fcs.i586
        /bin/rm is needed by jre-1.6.0_03-fcs.i586
        /bin/sed is needed by jre-1.6.0_03-fcs.i586
        /bin/sort is needed by jre-1.6.0_03-fcs.i586
        /bin/touch is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/cut is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/dirname is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/expr is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/find is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/tail is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/tr is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/wc is needed by jre-1.6.0_03-fcs.i586
        /bin/sh is needed by jre-1.6.0_03-fcs.i586
 
Done.

---

### Post by libertas on 2008-03-12
> **johnfarrow said:**
> when I do I get this.....error: Failed dependencies:
        /bin/basename is needed by jre-1.6.0_03-fcs.i586
        /bin/cat is needed by jre-1.6.0_03-fcs.i586
        /bin/cp is needed by jre-1.6.0_03-fcs.i586
        /bin/gawk is needed by jre-1.6.0_03-fcs.i586
        /bin/grep is needed by jre-1.6.0_03-fcs.i586
        /bin/ln is needed by jre-1.6.0_03-fcs.i586
        /bin/ls is needed by jre-1.6.0_03-fcs.i586
        /bin/mkdir is needed by jre-1.6.0_03-fcs.i586
        /bin/mv is needed by jre-1.6.0_03-fcs.i586
        /bin/pwd is needed by jre-1.6.0_03-fcs.i586
        /bin/rm is needed by jre-1.6.0_03-fcs.i586
        /bin/sed is needed by jre-1.6.0_03-fcs.i586
        /bin/sort is needed by jre-1.6.0_03-fcs.i586
        /bin/touch is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/cut is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/dirname is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/expr is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/find is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/tail is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/tr is needed by jre-1.6.0_03-fcs.i586
        /usr/bin/wc is needed by jre-1.6.0_03-fcs.i586
        /bin/sh is needed by jre-1.6.0_03-fcs.i586
 
Done. if you look at it (hard i know it makes my eyes go haywire) you will see jre-1.6.0_03-fcs.i586 which is the java trying to install on your computer (it is the java file) it then says that it does not have all of the directories and folders that are needed for it to install. My question is have you deleted anything that wasn't supposed to be deleted? are you administrator on the computer (that makes all the difference) if you don't know if you are admin then i ask you, are you able to download things via synaptics manager (if you are then you are admin.)

It is obvious that it is missing directories that it needs and they are all either in the bin directory or the usr/bin directory. do you have a bin directory? (was it deleted by mistake?) i am not entirely sure as to what answer is but i can tell you that your system is missing directories that java needs to install (which is what failed dependencies means) as well all of the things that  jre-1.6.0_03-fcs.i586 is said to be needing are either not there or not accessible by java. 

i suggest that you check to see if you still have those directories (see if you can find them) if you do than that is half the battle you then have to figure out what is stopping it from accessing the directories if you don't we now know that you are missing a rather large chunk of your bin directories in which case i suggest that you back up the systems files and fresh install ubuntu and put everything back on it (it will work then)

---

### Post by wolfen69 on 2008-03-12
first off, Firefox 3 is still beta. i found a few bugs that are already known. it is NOT ready for prime time yet. give it more time. it will save you some headaches.

---

