---
title: "[SOLVED] which are the Important files ?"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by jd3010 on 2007-10-30
I am really new with _Linux .
.. and trying to found out which are the important files for Ubuntu.

Like autoex.bat and config.sys and registry .... what are these files inUbuntu.

Where are the drivers loaded, 

Where do I have to look when I have a boot problem.

Where are firmwares loaded

I read a lot that the Kernel has to be "reconfigured" if you install a new driver.... Why how do you do that ...

I know these might be a lot questions, and answers might be very long ... just a need a crash cours and indications

thanks

---

### Post by captaink on 2007-10-30
Hello my friend, and welcome to the wonderful world of Linux!

Unfortunately, I couldn't answer to your questions here, it would be a too long reply!!! Also, as I am at work right now, I don't have enough time, so just the basics.

First of all, there is no registry! All settings and configuration are stored in files, seperated each other, not all together in an enormous database, like in windows. Most of these configuration files are stored in the /etc folder.
Boot settings are located in /boot folder, so this is a nice place to visit if you have problems booting AND if you know what you're doing. So, until you feel more comfortable with command line, use automated proccesses. When having a problem with grub (the loader that boots the linux kernel), the best way is to use the alternate cd available from ubuntu.com.
Now, about drivers and firmware, I think there are in /proc folder, but I'm not sure.

Don't hang on my words, search on the web for "Linux File System", that may be a good choice. Here is an article I found explaining linux filesystem. This may help you answer your questions: [http://www.freeos.com/articles/3102/]("http://www.freeos.com/articles/3102/")
Or maybe this: [http://tldp.org/LDP/intro-linux/html/sect_03_01.html]("http://tldp.org/LDP/intro-linux/html/sect_03_01.html") This has more chapters to read.

Remember, you may need to read some things in order to get to know linux, but believe me, it's worth the try! Almost 10 months ago I would never believe myself leaving windows for any reason. Now, I couldn't think of anything more stupid for me than to go back to windows!!!

P.S.: Most times you won't need to install drivers for your hardware, unless it is too new or too old (too rare to happen!), or the hardware is not supported. In that cases, dig into this and/or other forums to find a solution to your problem. Always do this in order to find a solution to a problem. Maybe, another person hound the same problem in the past and found a solution.

---

### Post by jd3010 on 2007-10-30
Thanks a lot for the Link, I will read carefully through it .... Yes I am pleased with what I saw for the Moment, and the Community is of great Help....

I do have a prob with NIC card 

[http://ubuntuforums.org/showthread.php?p=3668106#post3668106](http://ubuntuforums.org/showthread.php?p=3668106#post3668106) 

You might want to have a look....

Thanks a lot again

---

### Post by devilears on 2007-10-30
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)
[http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)


enjoy!

---

### Post by jd3010 on 2007-10-30
Thanks a lot ... I will ....

---

