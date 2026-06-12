---
title: "Path Environment Variable for Adobe Acrobat Reader"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by GrayMiata on 2006-01-20
I have recently downloaded and installed Adobe Acrobat Reader 7.0 for Linux into my Ubuntu 5.10 system.  The listing for the program shows up in Applications/Office and the plugin shows up in the listing for Firefox.  I tried to follow the instructions as best as I can but the program will not start on its own, only get the logo screen then disappears, and clicking on a pdf file in Firefox only gives me the same thing this time with an error message "Could not launch Acrobat Reader 7.0. Please make sure it exists in Path variable in environment. If problem persists please reinstall the application".

I did reinstall the application with the same results.  I searched the on line documentation for any help and found little.  I searched the on line forums for help and found something about the file /etc/profile that needs to be modified.  This is the only file I found with a Path entry in it so I added the following /usr/local/Adobe/Acrobat7.0/bin to the lines with the Path satement.  After saving and restarting, I still get the same results.  The reader will still not work.

Back in the old DOS days, the path statement used to be added in the config.sys file.  Can someone help a new user of Ubuntu by pointing out what file needs to be updated and how with a Path statement for the reader to work, or where instructions for this is written?  Is this the right forum for this question?

Thanks,
GrayMiata:cool:

---

### Post by Perfect Storm on 2006-01-20
Did you install all 3 packages which are needed?

```
sudo apt-get install acroread mozilla-acroread acroread-plugins
```

---

### Post by GrayMiata on 2006-01-20
Thanks for your response.  I originally used the automatic install from the install script that came with the Adobe Acrobat 7.0.  I just tried your suggestion and the terminal reported an error "Couldn't find package acroread".  Obviously, there must be something I am not doing right.  If there are any other suggestions I will try them.

Thanks,

GrayMiata

---

### Post by Tomy on 2006-01-23
[quote=GrayMiata]I have recently downloaded and installed Adobe Acrobat Reader 7.0 for Linux into my Ubuntu 5.10 system. The listing for the program shows up in Applications/Office and the plugin shows up in the listing for Firefox. I tried to follow the instructions as best as I can but the program will not start on its own, only get the logo screen then disappears, and clicking on a pdf file in Firefox only gives me the same thing this time with an error message "Could not launch Acrobat Reader 7.0. Please make sure it exists in Path variable in environment. If problem persists please reinstall the application".

I did reinstall the application with the same results. I searched the on line documentation for any help and found little. I searched the on line forums for help and found something about the file /etc/profile that needs to be modified. This is the only file I found with a Path entry in it so I added the following /usr/local/Adobe/Acrobat7.0/bin to the lines with the Path satement. After saving and restarting, I still get the same results. The reader will still not work.

Back in the old DOS days, the path statement used to be added in the config.sys file. Can someone help a new user of Ubuntu by pointing out what file needs to be updated and how with a Path statement for the reader to work, or where instructions for this is written? Is this the right forum for this question?

Thanks,
GrayMiata:cool:[/quote] 
I ran into the same problem installing Acrobat Reader 7.0 that I downloaded from the Adobe web site on Ubuntu 6.04, Dapper Drake.

The solution I found was to delete the installation:
```
$ sudo rm -R /usr/local/Adobe/
``` 
and install the Acrobat Reader 7.0 that is in the multiverse repository:

```

$ sudo apt-get update
$ sudo apt-get install acroread
``` 
you need to have the "multiverse" repository activated in /etc/apt/sources.list.

I always combine all of repositories on one line like this:


```

# /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
``` 
of course you would have "breezy" in that line not "dapper"

maybe this will help
Tomy

or maybe Acrobat 7.0 is not in the "breezy" repositories?

---

### Post by Perfect Storm on 2006-01-23
It's there. The multiverse just need to be enable.

---

### Post by ubuntuross on 2006-02-04
How does one come to know which packages to tell apt-get to install?  How did you know exactly which three packages to install?  I'm very new to Linux.  Thanks.

---

### Post by Perfect Storm on 2006-02-04
Where I know it from? I read it and memorized it.

---

### Post by Hereford on 2006-02-04
Having exactly the same problem, I just applied the suggestions above.  Here is the result from *apt-get install:*
> 
Reading package lists... Done
Building dependency tree... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate

The /etc/apt/sources-list that came with 5.10 has all the access URL's commented out with instructions to uncomment as needed.  The only reference to 'multiverse' there also has 'backports' on the sameline.

---

### Post by Perfect Storm on 2006-02-04
You need multiverse in your sourcelist.

---

### Post by Hereford on 2006-02-04
Here is the entry from /etc/apt/sources.list that I uncommented per instructions to reveal 'multiverse'.  The results of 'install' are posted above.  

> ## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

The part that says "breezy-backports main restricted" sounds strange here.  Elsewhere in the file I uncommented these:

 > deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe


Exactly what is "multiverse" and "Universe"?  Or where can I go to read about it?

-Thanks-

---

### Post by Perfect Storm on 2006-02-04
## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

---

### Post by Hereford on 2006-02-04
Got it!  Thanks.  The Ubuntu Wiki page provided the information I needed to use the Synaptic Package Manager.  Highly recommended.

---

