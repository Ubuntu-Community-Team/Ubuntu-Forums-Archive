---
title: "Where do all of the files go?"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-12
I'm a new Ubuntu 7.04 user with 1 weeks experience and been having lots of fun learning stuff.  I do feel really confused nad wonder where do all of the files that i have download go.  It feels like the days of Windows95 when I bought a book Windows 95 for dummies.  I have done lost of updates and downloaded a few apps and have no idea where they reside on my system.  I also want to know how can i get rid of files that I have installed and no longer want them.  for example, i installed a flash addon for firefox and it doesn't work so I would like to remove it.  I there a history log of changes to the system that i could read to follow what i have done the last week?  Where is the map of my hardrive structure that I could post here and get some advice that have the right directories?  How so I back-up Ubunto so that i can do a quick reinstall if I screwup everything in the near future.  Any help or adice will be appreciated.

VC

---

### Post by Najand on 2007-06-12
I believe this map can help you.
[http://tldp.org/LDP/intro-linux/html/sect_03_01.html#sect_03_01_03](http://tldp.org/LDP/intro-linux/html/sect_03_01.html#sect_03_01_03)
Actually that online book which has that map in it, is a good book for beginners and newbies. Have fun.

---

### Post by kevinlyfellow on 2007-06-12
> **videocheez said:**
> I'm a new Ubuntu 7.04 user with 1 weeks experience and been having lots of fun learning stuff.  I do feel really confused nad wonder where do all of the files that i have download go.

If you downloaded using firefox, then they go by default either to /home/{user}/Desktop or /home/{user}  I forget which.

> **videocheez said:**
> 
It feels like the days of Windows95 when I bought a book Windows 95 for dummies.  I have done lost of updates and downloaded a few apps and have no idea where they reside on my system.  


you can use the graphical search tools (Applications -> Accessories -> Search) or if you like command line you can type 
```
locate something
```

> **videocheez said:**
> 
I also want to know how can i get rid of files that I have installed and no longer want them.  

Open up synaptic (System ->  Administration -> Synaptic Package Manager) and uninstall the program you want to get rid of.

> **videocheez said:**
> 
for example, i installed a flash addon for firefox and it doesn't work so I would like to remove it.  

That is handles by firefox.  Go to Tools -> Add-ons and there will be a button to uninstall.

> **videocheez said:**
> 
I there a history log of changes to the system that i could read to follow what i have done the last week?  

There are tons of logs.  For installation through synaptic, go to file -> History
For system logs go to System -> Administration -> System Log
For a log of the things you entered into the command line, they are in your home directory in a file called .bash_history.  This file (and any file that has a period in front) is hidden.  In the file manager (nautilus) just hit ctrl-h to see all of the hidden files.

> **videocheez said:**
> 
Where is the map of my hardrive structure that I could post here and get some advice that have the right directories?  

There is a utility in the latest ubuntu under Applications -> Accesories -> Disk Usage Analyser  

Is that what you needed?

---

### Post by incubus on 2007-06-12
> **videocheez said:**
> I'm a new Ubuntu 7.04 user with 1 weeks experience and been having lots of fun learning stuff.  I do feel really confused nad wonder where do all of the files that i have download go.  It feels like the days of Windows95 when I bought a book Windows 95 for dummies.  I have done lost of updates and downloaded a few apps and have no idea where they reside on my system.  I also want to know how can i get rid of files that I have installed and no longer want them.  for example, i installed a flash addon for firefox and it doesn't work so I would like to remove it.  I there a history log of changes to the system that i could read to follow what i have done the last week?  Where is the map of my hardrive structure that I could post here and get some advice that have the right directories?  How so I back-up Ubunto so that i can do a quick reinstall if I screwup everything in the near future.  Any help or adice will be appreciated.

VC


cheez, that's a good question and you shouldn't feel ashamed of asking it.  Unfortunately, it's pretty hard to give a quick answer, because the Unix/Linux directory structure has a lot of details.  If you google the subject, you will find excellent guides that I don't dare to compete with.  But regarding the Ubuntu and Debian packages that you *download*, they are kept in:
```

/var/cache/apt/archives/

```

Each of the packages will install files to specific directories.  You could check it with this command:
```

$ dpkg -L <package name>

```

So, for example:
```

$ dpkg -L zip
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/zip
/usr/share/doc/zip/copyright
/usr/share/doc/zip/CHANGES.gz
/usr/share/doc/zip/TODO
/usr/share/doc/zip/WHATSNEW
/usr/share/doc/zip/changelog.Debian.gz
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/zip.1.gz
/usr/bin
/usr/bin/zip
/usr/bin/zipnote
/usr/bin/zipsplit
/usr/bin/zipcloak
/usr/share/doc/zip/changelog.gz
/usr/share/man/man1/zipnote.1.gz
/usr/share/man/man1/zipsplit.1.gz
/usr/share/man/man1/zipcloak.1.gz

```

But the beauty of the Debian packaging system is that you don't have to worry about these details.  It will take care of it for you.  Whenever you feel like you have downloaded unnecessary packages, you can remove them through: (this means remove the deb files, not uninstall them)
```

$ sudo apt-get autoclean

```

Or uninstall unused packages through:
```

$ sudo apt-get autoremove

```

Regarding backup, you can also search the forums for more advice, but your personal files are saved in /home, while the system config files are in /etc.  That what I usually back up.  But if storage is not an issue, you can backup everything and if something happens, you can restore your system to exactly how it was before.  In Unix/Linux people like to use the command tar and gzip.

I hope that gives you a starting point.

incubus

PS: Oops, other people have replied while I was writing.

---

### Post by terabite on 2007-06-13
About backup....

U can backup all ur .deb files from /var/apt/archives
Else u can download APTonCD. Its a gui application that automatically backs up all downloaded archives and creates an ISO file that u can burn to a CD and use as a third party repository later....
Its available on sourceforge as well as Feisty repos:

```
sudo apt-get install aptoncd
```

---

