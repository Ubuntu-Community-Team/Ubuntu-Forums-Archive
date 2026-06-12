---
title: "Cant find proftpd"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by cb2k on 2005-09-08
So im trying to setup up my Ubuntu machine as my FTP server. I have been doing some searching but everything I find tells me to install proftpd. Well I cant find it in synaptic and if I run the sudo apt-get install proftpd comand it cant find it either. So am I missing something, do they no longer produce proftpd, do I need to use a different app?

Please help!!

---

### Post by tonysathre on 2005-09-08
have u enabled all the repos in sources.list

---

### Post by cb2k on 2005-09-08
[QUOTE=tonysathre]have u enabled all the repos in sources.list[/QUOTE]
 How do I do that?
 ](*,)

---

### Post by tonysathre on 2005-09-08
open a terminal and type "sudo gedit /etc/apt/sources.list" (without quotes), it will open a text file, this file contains all the sites that apt-get and synaptic use to find packages, remove the # sign before all the lines in the file and then run your apt-get command again, this should fix your problem, if not post back

---

### Post by cb2k on 2005-09-08
[QUOTE=tonysathre]open a terminal and type "sudo gedit /etc/apt/sources.list" (without quotes), it will open a text file, this file contains all the sites that apt-get and synaptic use to find packages, remove the # sign before all the lines in the file and then run your apt-get command again, this should fix your problem, if not post back[/QUOTE]

Thanks ill give that a try.

---

### Post by vruum on 2005-09-08
before you do that, maybe try looking [here](http://ubuntuguide.org/#extrarepositories) 
generally speaking, lines preceeded by # are commented out, so the program that tries to read the file, in this case APT, wont try to read those lines, that way a text file can hold instructions on how to edit it, and what the different lines does/means, with out messing up whatever program tries to read it, and ubuntu is rather well commented, simply deleting every single # might confuse APT.

---

### Post by cragmonkey on 2005-09-10
[QUOTE=tonysathre]open a terminal and type "sudo gedit /etc/apt/sources.list" (without quotes), it will open a text file, this file contains all the sites that apt-get and synaptic use to find packages, remove the # sign before all the lines in the file and then run your apt-get command again, this should fix your problem, if not post back[/QUOTE]
 I have uncommented the appropriate lines in the sources.list file and I still cannot seem to find any packages name proftpd. I can find the tarballs for this app and can easily install it from there but I would stil like to know why I can't apt-get this app.. Any additional help would be greatly appreciated. I'm currently googling it and have not been able to find anything overly pertinent. still looking.......

---

### Post by cragmonkey on 2005-09-10
OK, for all the newbs (like me) out there that are having trouble with this. Here is the answer:
(Note: I use vi since I have worked with it before and feel comfortable in it. You can just as easily use gedit if that is your preference.)

```
sudo vi /etc/apt/sources.list
``` 

and add the following lines to the bottom of your list file:

```
## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

Save and close the file and update your apt-get:

```
apt-get update
```

You should now be able to get proftpd by using apt-get or the GUI package manager.

---

