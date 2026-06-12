---
title: "reinstalling help please!!!!"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by valke on 2007-02-28
i had attempted to install alien arena 2007 from the deb on getdeb.net. my laptop froze and i forced a restart during the installation. now, i don't have the permissions to install from the deb file, and because it needs re-installation i cannot update my laptop or remove it. can someone help me please? i have decided i do not want it anyway.

---

### Post by valke on 2007-02-28
bump please do help!

---

### Post by ndefontenay on 2007-02-28
Hi mate,

consider a little patience. 40 minutes is not a long time to get an answer at that time.

Your explanation is not very clear, so let's calm down and think a little bit.

Are you able to use sudo? Can you show us the commands you've used so far?

This would be greatly useful in helping you.

---

### Post by valke on 2007-02-28
as root i have done this.

```
root@millimeter-laptop:/home/valke# dpkg -r alienarena2007
dpkg: error processing alienarena2007 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 alienarena2007
root@millimeter-laptop:/home/valke# sudo apt-get alienarena2007
E: Invalid operation alienarena2007
root@millimeter-laptop:/home/valke# 


```

i am not sure as to what to do with sudo... can you please walk me through it? i will definitely be more patient. sorry. :oops:

---

### Post by johnc4510 on 2007-02-28
How did you try to install it? Thru command line or GDebi Package installer?

---

### Post by valke on 2007-02-28
GDebi

---

### Post by ndefontenay on 2007-02-28
oh my.

it seems your package is not good and before removing it, you should install it properly first.

Concerning sudo, it's your root user. Except ubuntu don't use root anymore. When you want to use a command that requires root privilege, you would prefixe it with sudo.
It will prompt you for your use password (the one you provided on installation).

What I would try to do is use apt-get and try to repair my dependencies. We never know.

Try that:

```
sudo apt-get install -f
``` (or is it sudo apt-get -f  install, not sure now)

---

### Post by johnc4510 on 2007-02-28
If you type in this in a terminal, it should show you where all the alien arena files are:
whereis alienarena2007  
Then you can use the terminal to navigate to each file and delete it. Here is the command to navigate as root in Nautilus:
sudo natilus
NOTE: Be careful with this command!!!!

---

### Post by valke on 2007-02-28
i did, and this is what i have...
```
valke@millimeter-laptop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package alienarena2007 needs to be reinstalled, but I can't find an archive for it.
valke@millimeter-laptop:~$ 
```

---

### Post by johnc4510 on 2007-02-28
you can try sudo apt-get -f install first, but I'm not sure it will work. If it does install it we can go another way. Post back here

---

### Post by valke on 2007-02-28
i have located the alien arena 2007, its in usr/share...ect blah blah blah. if i delete these, the problem will be taken care of?

---

### Post by johnc4510 on 2007-02-28
what do you get with :  whereis alienarena2007?

---

### Post by valke on 2007-02-28
```
valke@millimeter-laptop:~$ whereis alienarena2007
alienarena2007: /usr/share/alienarena2007
valke@millimeter-laptop:~$ 
```

sorry, should have posted this i guess.

---

### Post by ndefontenay on 2007-02-28
the problem is not big.
Try to download the package again and re install it.
It should fix your problem.
An alternative is to go to their website and find a package repository that we would include in the apt config file.
Then it would find the archive it is looking for to install it using apt-get. It's the cleanest solution.

I would not recommand deleting them one by one. It's dirty and it does not update your application repository. Ubuntu will keep thinking there's a problem with this application.

---

### Post by johnc4510 on 2007-02-28
At this point I would take a chance and use the sudo nautilus command to delete that file and then make sure you delete the deb file where ever you have it. 

NOTE: At your own risk(but i think this will work)

---

### Post by valke on 2007-02-28
i am downloading the deb again...i've decided i want my repositories updated. i tried this before, but i will let you know either way what happens.

---

### Post by valke on 2007-02-28
uh it's telling me the file may be corrupted or i don't have permissions to open the file.

---

### Post by johnc4510 on 2007-02-28
I was afraid that it was a corrupt file and that's what caused you system to lock. Just for fun though, right click on the deb, choose properties, and choose permissions and see if you have it or not.

---

### Post by valke on 2007-02-28
here you go. i have read and write permissions.

---

### Post by valke on 2007-02-28
ok so what should i do now?

---

### Post by Maestro23 on 2007-02-28
> **valke said:**
> ok so what should i do now?

Open a terminal:

> cd /home/username/Desktop (where you package is)

sudo dpkg -i package(your package goes here).


---

### Post by valke on 2007-02-28
thank you all so much. this fixed the problem. just for kicks, this is what i did in the terminal, just so others may learn too!

```
valke@millimeter-laptop:~$ cd /home/valke/Desktop
valke@millimeter-laptop:~/Desktop$ sudo dpkg -i alienarena2007-linux20070121-x86.zip
Password:
dpkg-deb: `alienarena2007-linux20070121-x86.zip' is not a debian format archive
dpkg: error processing alienarena2007-linux20070121-x86.zip (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 alienarena2007-linux20070121-x86.zip
valke@millimeter-laptop:~/Desktop$ sudo dpkg -i alienarena2007_1.0-1.getdeb1_i386.deb
dpkg: error processing alienarena2007_1.0-1.getdeb1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 alienarena2007_1.0-1.getdeb1_i386.deb
valke@millimeter-laptop:~/Desktop$ sudo dpkg -i alienarena2007_1.0-1getdeb1_i386.deb
Selecting previously deselected package alienarena2007.
(Reading database ... 
dpkg: serious warning: files list file for package `alienarena2007' missing, assuming package has no files currently installed.
119807 files and directories currently installed.)
Preparing to replace alienarena2007 1.0-1getdeb1 (using alienarena2007_1.0-1getdeb1_i386.deb) ...
Unpacking replacement alienarena2007 ...
Setting up alienarena2007 (1.0-1getdeb1) ...
valke@millimeter-laptop:~/Desktop$ 

```

---

### Post by Maestro23 on 2007-02-28
Glad to help.

---

