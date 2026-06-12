---
title: "Real Player 10 Problem"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by shoaibi on 2007-02-10
Here is what i am doing.
```

shoaibi@saber-rider:~$ chmod +x RealPlayer10GOLD.bin
shoaibi@saber-rider:~$ su
Password:
root@saber-rider:/home/shoaibi# sudo ./RealPlayer10GOLD.bin
Extracting files for RealPlayer installation........................

Welcome to the RealPlayer (10.0.8.805) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...

Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/shoaibi/RealPlayer]: /opt/realplayer
You have selected the following RealPlayer configuration:

Destination:            /opt/realplayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]: F

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: .Y.
enter the prefix for symbolic links [/usr]: .@
Setting up realplay symlinks in @...
ln: creating symbolic link `@/share/realplay' to `/opt/realplayer/share': No such file or directory
ln: creating symbolic link `@/bin/realplay' to `/opt/realplayer/realplay': No such file or directory
ln: creating symbolic link `@/lib/realplay' to `/opt/realplayer/lib': No such file or directory
configuring icons...
configuring document icons...
configuring pixmaps...
configuring locale...
.configuring desktop...
configuring applications...
configuring GNOME mime types...
Configuring realplay script...

RealPlayer installation is complete.
Cleaning up installation files...
Done.

root@saber-rider:/home/shoaibi# 

```


Hmmm and Going to Application>Sound and Video and runnning RealPlayer 10 from there gives

Could not launch menu item
Failed to execute child process
"realplayer" (no such file ordirectory)

Then i did this

```

root@saber-rider:/home/shoaibi# ls /opt/realplayer
Bin     common  install.log  LICENSE  plugins   README    realplay.bak  share
codecs  doc     lib          mozilla  postinst  realplay  realplay.bin


```

---

### Post by Perfect Storm on 2007-02-10
Remove the current realplayer10, add this to your source list


## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

and get it through there.

---

### Post by nudnik on 2007-02-10
Real Player should be installed in /usr/bin. You should be in root from the start for a trouble free install.

Remember....this : ](*,)  isn't the mascot for no reason you know!

---

### Post by shoaibi on 2007-02-10
how to remove it? :(
```

root@saber-rider:/home/shoaibi# sudo apt-get remove real
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package real
root@saber-rider:/home/shoaibi# sudo apt-get remove RealPlayer10GOLD
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package RealPlayer10GOLD


```

By the way there is a file called realplayer in thedirectory that i listed, and if i double click it real player opens up and works just fine....

---

### Post by nudnik on 2007-02-10
You will have to manually remove it from the directory in which you installed it using the command line. Use "rm" followed by whatever file you wish to remove.

Once the above is done, reinstall using either my method or the one provided by the administrator a moment ago.

---

### Post by shoaibi on 2007-02-10
i tried to this:
```

sudo ln -s /opt/realplayer/real /usr/bin

```
thought it would resolve the problem, but same error pops again adn again...

---

### Post by nudnik on 2007-02-10
Remove that link you just made and all other Real files and start over as we recommended. I seriously doubt anything else will work.

---

### Post by shoaibi on 2007-02-10
Hmmm okay, Done.
RESOLVED!

---

