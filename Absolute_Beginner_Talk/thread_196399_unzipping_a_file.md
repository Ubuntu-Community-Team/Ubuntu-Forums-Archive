---
title: "unzipping a file"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-06-14
Im trying to install libpng and have downloaded it ok but when i try to tar it im getting the following error . What am i doing wrong?



[COLOR="Red"]100%[=======================================================================================================================>] 726           --.--K/s
09:35:33 (49.45 MB/s) - `libpng-1.2.8-config.tar.gz' saved [726/726]

root@ubuntu:/tmp/rrdbuild# tar zxvf libpng-1.2.10.tar.gz
tar: libpng-1.2.10.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@ubuntu:/tmp/rrdbuild# tar zxvf libpng-1.2.8.tar.gz
tar: libpng-1.2.8.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@ubuntu:/tmp/rrdbuild# tar zxvf libpng-1.2.8-config.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
root@ubuntu:/tmp/rrdbuild# tar libpng-1.2.8-config.tar.gz
tar: Old option `b' requires an argument.
Try `tar --help' or `tar --usage' for more information.
root@ubuntu:/tmp/rrdbuild#[/COLOR]

---

### Post by catlett on 2006-06-14
Try using nautilus . Get to lbpng by Places<Home. When you get to the file right-click on it. You will get the option to "extract here" or "create archive". Tar is what will be invoked to accomplish the actions.
If you right click and choose "extract" or "create" and you still have an issue there is something deeper to the problem. But for now try tarring graphically with nautilus and see what happens.

---

### Post by andrecasteliano on 2006-06-14
Remember that you should install ZIP support first:

sudo apt-get install zip unzip

And, ir you´re only trying to install libpng, you really should do it using apt-get:

sudo apt-cache search libpng

This command will show all 'libpng' packages available. Use Synaptic insteado of command line.

---

### Post by meniscus on 2006-06-14
What im trying to do is install rrdtool from this link [COLOR="Red"]http://oss.oetiker.ch/rrdtool/doc/rrdbuild.en.html[/COLOR]

and libpng must be installed for it to work.

In Synaptic  Manager when i type libpng into search it returns a whole list of them. How do i know which ones i need?

---

### Post by meniscus on 2006-06-14
will the command

[COLOR="Red"]sudo apt-get install libpng[/COLOR] install and configure it for me or is there more to it

---

### Post by Harleen on 2006-06-14
If you want to build other packages, that use libraries, you also have to install the according -dev (development) package.
So additionally to "apt-get install libpng12-0" you also have to do "apt-get install "libpng12-dev". There's no need for you to compile libpng for yourself. The same goes for zlib (packages zlib1g and zlib1g-dev) and freetype (libfreetype6 and libfreetype6-dev). It's sometimes tricky to find out, which one is the right package to install. For libpng, you just have to read the descriptions to filter out those unneeded packages.
And to answer your first question about unzipping files: It would have worked, if you gave the correct file name. ;) The command "tar zxvf libpng-1.2.8-config.tar.gz" would have worked. When working on the command line, you can often use the tab key to automatically complete filenames. So you avoid typing mistakes.

And if all that fails, you can also just install the Ubuntu package for rddtool. ;)
apt-get install rrdtool

---

### Post by meniscus on 2006-06-14
So you re saying
[COLOR="Red"]
sudo apt-get install rddtool [/COLOR]

would have done all what it says at this link. [COLOR="Blue"]http://oss.oetiker.ch/rrdtool/doc/rrdbuild.en.html[/COLOR]

Ive tried that method, failed miserably 2 because i cant run the examples it gives at the very end.  They are there but when i tried to run them it does nothing.
Could i just go [COLOR="Red"]
sudo apt-get install rddtool [/COLOR]
 and it should work? 

would installing it twice corrupt the whole thing?

---

### Post by Harleen on 2006-06-14
[QUOTE=meniscus]So you re saying
[COLOR="Red"]
sudo apt-get install rddtool [/COLOR]

would have done all what it says at this link. [COLOR="Blue"]http://oss.oetiker.ch/rrdtool/doc/rrdbuild.en.html[/COLOR][/QUOTE]

Yes - sort of. Someone else did all the things mentioned on that link and provides this package.

[QUOTE=meniscus]Ive tried that method, failed miserably 2 because i cant run the examples it gives at the very end.  They are there but when i tried to run them it does nothing.
Could i just go [COLOR="Red"]
sudo apt-get install rddtool [/COLOR]
 and it should work? 

would installing it twice corrupt the whole thing?[/QUOTE]

Installing twice won't help or hurt. You'd just overwrite the files.
I just tried that program myself and had to install the package librrds-perl also to make the examples work. Good luck!

---

### Post by meniscus on 2006-06-14
Got it working....Halleluya! had to install that package you had to 2! librrds-perl 
Thanks for your help

---

