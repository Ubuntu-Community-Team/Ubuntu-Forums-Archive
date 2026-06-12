---
title: "Ubuntu Synaptic problem with JRE package"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by pcl on 2007-05-13
Hi,

I first want you to picture my understanding of Ubuntu and/or Unix
like systems. I am like a car driver who has decided to take commands
of a space station. This is to say that I don't understand much about
how linux files work nor I can make my way into a linux file explorer
system...

I know from the command terminal how to deal with cd and ls and maybe
dir...

So far, I have to deal with this issue when I want to launch Synaptic
Package Manager :

"E: The package jre needs to be reinstalled, but I can't find archive
for it."

"E:Internal error opening cache(1). Please report."

1) Who is "I" (I can't find...)?

2) What means E: ?

3) How to solve that JRE issue?

If you have the answer, feel concerned, want to help me out, please
state commands I should enter with a character precision. If you tell
me in vague what to do or where to go, I am already a little lost.

I am running Ubuntu 7.04.

Thanks for your concern,

Pascal

---

### Post by orb9220 on 2007-05-13
Open a term and copy and paste line below:

 **sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts**

This will install java for you

---

### Post by pcl on 2007-05-13
This doesn't make Synaptic work.

And the update manager is also stuck... because of that jre broken link...

---

### Post by Happy_Man on 2007-05-13
1. "I" refers to the system. There are no gremlins sitting in your computer throwing error messages for kicks. ;)

2. E simply means "error"

3. Could you please post the output of 
```
cat /etc/apt/sources.list
```
?

---

### Post by pcl on 2007-05-13
hi,

here is the output:

scalpa@scalpa:~$ cat /etc/apt/sources.list

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Now if that can be of any help,

there is already 2 threads about it from a web search (the 2 threads are from the same author and for the same problem)

 [google:*ubuntu the package jre needs to be reinstalled, but i can't find an archive for it*] :

[[COLOR="DarkOrange"]http://linux.derkeiler.com/Newsgroups/comp.os.linux.setup/2006-05/msg00311.html[/COLOR]]("http://linux.derkeiler.com/Newsgroups/comp.os.linux.setup/2006-05/msg00311.html")
[B]
But the fact that I am not really familiar with Ubuntu file system makes things a little difficult to implement if someone doesn't tell me what to do from "the freezer", like what I have to enter in the command terminal... it should make sense afterward...
[/B]
Thanks for your concern

---

### Post by Happy_Man on 2007-05-13
Ok, enter the command ```
sudo gedit /etc/apt/sources.list
``` and change 
> # deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
 # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
to
> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
  deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

and change > # deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
 # deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
to
> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
  deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

and > # deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
 # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
to
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

then restart Synaptic and see if the thing installs.

---

### Post by rsambuca on 2007-05-13
I agree that those changes should work well.  However, you should use this command to edit the file instead:```
gksudo gedit /etc/apt/sources.list
```

Basically any time you are opening a gui program as sudo, you should use the command gksudo, otherwise you can mess your system up (although in this case, just using sudo will work).

---

### Post by pcl on 2007-05-14
Still same message:

E: The package jre needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

and Synaptic won't open.

I think it's all about that jre java package somewhere in the system...

---

### Post by pcl on 2007-05-14
So, I am still in the same position, I tried to do the sudo things but nothing changed... Should I keep the # as they are in my initial file? Anyway I did try with and without and it's still the same.

Here something else I got from a google forum...

Someone asked me to enter commands below that resulted in what you can see next.

=====start=====

 scalpa@scalpa:~$ sudo aptitude install sun-java6-jre sun-java6-plugin
sun-java6-fonts
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not
upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the jre package. This might mean
you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
scalpa@scalpa:~$ sudo -s
root@scalpa:~# sudo aptitude install sun-java6-jre sun-java6-plugin
sun-java6-fonts
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not
upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Error!
E: I wasn't able to locate a file for the jre package. This might mean
you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
root@scalpa:~# sudo aptitude install j2re1.4-mozilla-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  gsfonts-x11 j2re1.4
The following NEW packages will be installed:
  gsfonts-x11 j2re1.4 j2re1.4-mozilla-plugin
0 packages upgraded, 3 newly installed, 0 to remove and 0 not
upgraded.
Need to get 0B of archives. After unpacking 60.5MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the jre package. This might mean
you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
root@scalpa:~# sudo aptitude install j2re1.4-mozilla-plugin
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  gsfonts-x11 j2re1.4
The following NEW packages will be installed:
  gsfonts-x11 j2re1.4 j2re1.4-mozilla-plugin
0 packages upgraded, 3 newly installed, 0 to remove and 0 not
upgraded.
Need to get 0B of archives. After unpacking 60.5MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the jre package. This might mean
you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
root@scalpa:~# 

=====end=====

Which book could I find on amazon to get a good understanding of the system file in Ubuntu and navigate into it? 
Would an introduction book to Unix do the work?
(I am no university student in computer systems, just a hobby...), would ubuntu for dummies do it?

---

### Post by Nythain on 2007-05-14
ok, so after removing the # from all the lines in the /etc/apt/sources.list file that start with deb like told above... make sure you save the file, then in the terminal type
sudo aptitude update
if still no luck i would try
sudo aptitude clean
but im not sure if thats going to help much in this case

---

### Post by Detonate on 2007-05-14
Can you:

```
sudo update-alternatives --config java 
```

in the terminal.

Select Sun JRE as the default.  See if that helps.

---

### Post by christhemonkey on 2007-05-14
Also before you run any off these apt-get or aptitude commands, please close both synaptic and update-manager if you have them running!

Only one of these package management programs can be running hence the error:
> E: Couldn't lock list directory..are you root?

---

### Post by pcl on 2007-05-14
Still same issue, i guess i should reinstall :(  jre package not found when opening synoptic. Ubuntu can't get any update as well. WHERE AM I?

scalpa@scalpa:~$ sudo gedit /etc/apt/sources.list
scalpa@scalpa:~$ sudo aptitude update
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/universe Translation-en_GB
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports Release           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-backports/multiverse Sources
Fetched 4B in 0s (5B/s)  
Reading package lists... Done
scalpa@scalpa:~$ sudo aptitude clean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
scalpa@scalpa:~$

---

### Post by pcl on 2007-05-14
> **christhemonkey said:**
> Also before you run any off these apt-get or aptitude commands, please close both synaptic and update-manager if you have them running!

Only one of these package management programs can be running hence the error:

=

How do I stop update manager from running? Synaptic is not running as i can't merely get it started, it shuts itself downon start-up after that jre missing package it says "he" can't find.

There is that orange icon with a white star inside near my internet connection icons with a yellow sticker that says:

"An error occured, please run package manager from the right click menu or apt-get on a terminal to see what is wrong
The error message was: 'Unknown error type:'<type 'exceptions.SystemError'>' (E:The package jre needs to be reinstalled, but I can't find an archive for it.)'"

Sorry if this is confusing, hope i still can save my current system...

---

### Post by pcl on 2007-05-15
I am also experiencing the same thing as in this post:
 	
How to remove from desktop jre 1.6.0_01locked folder.
from drpas2k 

but the reply that says to enter something like sudo rm... brings nothing new.

Would someone who know about unix or ubuntu be able to help me out with my missing jre package if he can see how my system is configured and working? Is it about all the permissions and stuff that customize the system that make things not easy to solve from a forum?

---

### Post by bliffle on 2007-06-02
I have exactly the same prolem. No solution in sight.

I started out trying to bringup Azureus, and that's when I got into trouble. Strangely, I seem to remember Azureus working on this computer when I first installed Ubuntu a few days ago.

---

