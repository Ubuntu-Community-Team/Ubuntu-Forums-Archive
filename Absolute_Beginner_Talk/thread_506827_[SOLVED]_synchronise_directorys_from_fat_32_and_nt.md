---
title: "[SOLVED] synchronise directorys from fat 32 and ntfs"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-07-22
i have 2 hard drives both on a local machine and there is a few directory's i would like to keep in sync with each other.

one hdd is a fat32 the other is ntfs

i tried the program "unison" but it would not let me select the fat 32 or the ntfs drive. 

i have found this program that looks like it might do the job

[http://directorysync.sourceforge.net/doc.html](http://directorysync.sourceforge.net/doc.html)

but it also says this
=====================================================================
1.2.1 Ubuntu/Kubuntu 5.10

You might get the following Error:

 Exception in thread "main" java.lang.NoClassDefFoundError: dirsync/DirSync
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
 Caused by: java.lang.ClassNotFoundException: dirsync/DirSync
    at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
    at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
 
This is due to Ubuntu/Kubuntu installing a free (i.e. not SUN) Java that seems to be not 100% compatible yet. 
You have to install the SUN Java. Afterwards you have to select it:

 sudo update-alternatives --config java
=====================================================================

i noticed in automatics2 under codecs there is a Java 1.6 if i install this version of java can i get the directory sync program to run?

ok i installed the java with automatix2 and d/l the zip file from source forge... looks promising, i opened the dirsync.jar file with java and i have a groovy GUI infront of me...

looks promising.
dont have time to investigate now, but will let you know how i go

*sigh* i had to try it... again another brillint looking program but it will not allow me to select my fat32 or ntfs drive.

the search continues

---

### Post by jfinkels on 2007-07-22
> **stinger30au said:**
> i have 2 hard drives both on a local machine and there is a few directory's i would like to keep in sync with each other.

one hdd is a fat32 the other is ntfs

i tried the program "unison" but it would not let me select the fat 32 or the ntfs drive. 

i have found this program that looks like it might do the job

[http://directorysync.sourceforge.net/doc.html](http://directorysync.sourceforge.net/doc.html)

but it also says this
=====================================================================
1.2.1 Ubuntu/Kubuntu 5.10

You might get the following Error:

 Exception in thread "main" java.lang.NoClassDefFoundError: dirsync/DirSync
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
 Caused by: java.lang.ClassNotFoundException: dirsync/DirSync
    at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
    at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
 
This is due to Ubuntu/Kubuntu installing a free (i.e. not SUN) Java that seems to be not 100% compatible yet. 
You have to install the SUN Java. Afterwards you have to select it:

 sudo update-alternatives --config java
=====================================================================

i noticed in automatics2 under codecs there is a Java 1.6 if i install this version of java can i get the directory sync program to run?

ok i installed the java with automatix2 and d/l the zip file from source forge... looks promising, i opened the dirsync.jar file with java and i have a groovy GUI infront of me...

looks promising.
dont have time to investigate now, but will let you know how i go

*sigh* i had to try it... again another brillint looking program but it will not allow me to select my fat32 or ntfs drive.

the search continues

You could write a shell script that uses the program 'rsync' to download files from one location to another; iin brief it is used like this:```
rsync /path/to/source /path/to/destination
``` To read more about it, type this:```
man rsync
```

After writing the script, you might schedule it to be run as a cron job (i.e. at a scheduled time every day or otherwise regularly). To read more about cron, type the following in the terminal:```
man cron
```

---

### Post by trak87 on 2007-07-22
Yeah, I was going to suggest rsync as well. Very powerful command line program. Perhaps there's a GUI interface for it as well?

---

### Post by stinger30au on 2007-07-22
cool, thanks for the ffedback i will investigate

---

### Post by stinger30au on 2007-07-22
its cool . under xp pro i used to use the[ freeware version of syncback]("http://www.2brightsparks.com/downloads.html#freeware") and told wine in the setup what drives to use and presto!!! works like charm!

---

### Post by stinger30au on 2007-09-01
i have changed my OS to Ubuntu Ultimate 1.4 and tried to install syncback and it  now refuses to sync directorys...

so i went a hunting. go to applications and go to add/remove and in the search file type in "grsync"
install it. only 500k long.

homepage here

[http://www.opbyte.it/grsync/](http://www.opbyte.it/grsync/)

---

