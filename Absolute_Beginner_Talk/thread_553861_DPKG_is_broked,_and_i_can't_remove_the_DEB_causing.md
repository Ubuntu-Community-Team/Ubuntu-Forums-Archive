---
title: "DPKG is broked, and i can't remove the DEB causing the trouble! i think it's a bug?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by ijason on 2007-09-18
hey all. i posted this late last night, but want to post again since - despite some very helpful suggestions - i haven't been able to find a solution yet. i'd really prefer not to reinstall.

the back story is that i installed a .deb (converted from a .rpm via Alien) with the package manger, and then later tried installing it again through a terminal with dpkg when i was following a different howto for installing maya. that's when things got broke.

the dpkg install attempt threw out a bunch of errors and now my "update now" icon is active with the following message :
> A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: 'Unknown Error: '<type 'exceptions.SystemError'>' (E:The package awcommon needs to be reinstalled, but I can't find an archive for it.)'
this is the same error i get when i try to open the synaptic package manager.

so the first suggestion to solve the problem was to force the package to be removed using the dpkg command. here's what i did and what happened :
> jason@jason-laptop:~$ sudo dpkg --force-remove-reinstreq --remove awcommon
dpkg - warning, overriding problem because --force enabled:
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
(Reading database ... 164032 files and directories currently installed.)
Removing awcommon ...
/usr/bin/test: invalid integer `remove'
exit: 26: Illegal number: -0
dpkg: error processing awcommon (--remove):
subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
awcommon

with that error, it was suggested that i reinstall the package like the error code says to do. here's what i typed and what happened :
> root@jason-laptop:/home/jason/Desktop/mayainstalls#
root@jason-laptop:/home/jason/Desktop/mayainstalls# ls aw*
awcommon_10.80-14_i386.deb
root@jason-laptop:/home/jason/Desktop/mayainstalls#
root@jason-laptop:/home/jason/Desktop/mayainstalls# aptitude reinstall awcommon_10.80-14_i386.deb
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "awcommon_10.80-14_i386.deb"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the awcommon package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@jason-laptop:/home/jason/Desktop/mayainstalls#

i tried switching between listing the exact file name and simply 'awcommon' to let dpkg decide the exact file name. i got the same error codes for both attempts. so, with everything else failing for me, it was suggested that i simply purge the file. which sounded like a great idea, but failed just like the other solutions. here's what i typed and what i got :
> jason@jason-laptop:~$
jason@jason-laptop:~$ sudo aptitude purge awcommon
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REMOVED:
awcommon{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 4100kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing awcommon (--purge):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
Errors were encountered while processing:
awcommon
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
jason@jason-laptop:~$

any suggestions?! i've rebooted now, and i've checked to make sure there's nothing going on with the sessions manager that might be saving settings. this morning i'm still getting the same error in my update-now icon.

---

### Post by Kilz on 2007-09-18
have you tried ```
sudo apt-get install -f
```  ?

---

### Post by ijason on 2007-09-18
here's what happens when i try that :
> jason@jason-laptop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package awcommon needs to be reinstalled, but I can't find an archive for it.
jason@jason-laptop:~$ 


---

### Post by aktiwers on 2007-09-18
I had a problem like this, and got a lot of good suggestions..
Try read the entire post and use some of the tools / commands suggested.
[http://ubuntuforums.org/showthread.php?t=252762](http://ubuntuforums.org/showthread.php?t=252762)

---

### Post by ijason on 2007-09-18
**@aktiwers** : did you solve the problem with gtkorphan?

---

### Post by aktiwers on 2007-09-18
Nope, as you can read the problem fixed it self.. or at least after I did all the stuff suggested a lot of times. But other people I pointed to that post, did solve the problem.. So try it! :)

---

### Post by ijason on 2007-09-18
**@atkiwers** : i looked through the thread you suggested, but the conclusion of it was that the problem just went away on it's own. so it doesn't really help me too much :( i tried the various things they suggested, and am still getting the same errors.

---

### Post by aktiwers on 2007-09-18
Sorry ijason, I hoped some of the information in there could help you. Im afraid I dont have any other suggestions.

I do remember using:
```
aptitude
``` 
Alot for cleaning manually, and grkorphan. And basicly most of the commands suggested all through the posting.

Sorry I cant be of more help.

---

### Post by ThrobbingBrain66 on 2007-09-18
I believe aptitude only manages packages found in the repos.  Issuing a command like ```
sudo aptitude reinstall awcommon
```
is only going to look in the repositories for the package, no matter what directory you are in.

Open nautilus and navigate to /var/cache/apt/archives

This is where archive packages are kept.  If you don't see the awcommon package listed there, open nautilus as root and copy it to the directory.  This might allow you to reinstall/remove the package.

---

### Post by ijason on 2007-09-18
**@brain** : ok, i've copied the files (i had to use a terminal, how do i SU inside nautilus?) now should i retry the dpkg commands? or something else?

---

### Post by ijason on 2007-09-18
**@brain** : i'm going to go ahead and try the dpkg reinstall command, here's the in/output from the attempt :
> root@jason-laptop:/home/jason/Desktop/mayainstalls# 
root@jason-laptop:/home/jason/Desktop/mayainstalls# ls /var/cache/apt/archives
awcommon_10.80-14_i386.deb  lock  partial
root@jason-laptop:/home/jason/Desktop/mayainstalls# aptitude reinstall awcommon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins 
  libcompizconfig0 
The following packages have been kept back:
  compiz compiz-fusion-plugins-extra compizconfig-settings-manager 
  libdecoration0 
The following packages will be REINSTALLED:
  awcommon 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate file for the awcommon package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@jason-laptop:/home/jason/Desktop/mayainstalls# 

---

### Post by ThrobbingBrain66 on 2007-09-18
You have to use the full package name, including the version number, I believe.  And you must be root to modify any packages.  ```
sudo aptitude reinstall awcommon_10.80-14_i386.deb
```
Give the command above a shot, and let me know if it works.

---

### Post by alienexplorers on 2007-09-18
I believe the command to use would be"

First remove ALL the archives (scripts) whose name began with awcommon in the directory /var/lib/dpkg/info/.
> sudo rm /var/lib/dpkg/info/awcommon.xxxx
Then use this
> sudo dpkg --remove --force-remove-reinstreq awcommon

Thats it. yeah!

---

### Post by ijason on 2007-09-18
hey guys. had to go to work for a few hours, but i'm back and trying your suggestions!

**@ throbbingbrain** :
> root@jason-laptop:/home/jason/Desktop/mayainstalls#
root@jason-laptop:/home/jason/Desktop/mayainstalls# sudo aptitude reinstall awcommon_10.80-14_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "awcommon_10.80-14_i386.deb"
The following packages have been automatically kept back:
  compiz-core compiz-fusion-plugins-main compiz-gnome compiz-plugins 
  libcompizconfig0 
The following packages have been kept back:
  compiz compiz-fusion-plugins-extra compizconfig-settings-manager 
  libdecoration0 
0 packages upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the awcommon package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
root@jason-laptop:/home/jason/Desktop/mayainstalls# 

and now i'll try **Alienexplorers** :
> root@jason-laptop:/home/jason/Desktop/mayainstalls#
root@jason-laptop:/home/jason/Desktop/mayainstalls# sudo rm /var/lib/dpkg/info/awcommon*
root@jason-laptop:/home/jason/Desktop/mayainstalls#
root@jason-laptop:/home/jason/Desktop/mayainstalls# sudo dpkg --remove --force-remove-reinstreq awcommon
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `awcommon' missing, assuming package has no files currently installed.
164032 files and directories currently installed.)
Removing awcommon ...
root@jason-laptop:/home/jason/Desktop/mayainstalls# 
root@jason-laptop:/home/jason/Desktop/mayainstalls#

good god man! i think you've done it! the "update notice" icon in my tray went silent, and then when i clicked it i got successful downloading of a bunch of compiz stuff! looks like you found the solution! thank you very very much!

---

