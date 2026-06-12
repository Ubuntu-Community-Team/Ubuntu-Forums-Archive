---
title: "[SOLVED] how to get kdar installed in fiesty"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by stinger30au on 2007-07-13
im still a fairly new user to Ubuntu and i have installed Fiesty fawn (the gnome version). id really like to get dar and kdar running. i have installed dar via cli with "sudo apt-get install dar" and it worked nicely.
but if i do a search on kdar like this "apt-cache search kdar" from the cli, i get no search hits??? 
i don't suppose anyone knows how to install kdar with a simple tutorial for a noobie like me to follow. thanks

---

### Post by wolfen69 on 2007-07-14
i know it says for dapper, but may work:

You can also use the following procedure when you do this you need to be very careful what you are doing.

you can edit the /etc/apt/sources.list file

sudo vi /etc/apt/sources.list

add the following line

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

save and exit the file.

Now update the souce list using the following command

sudo apt-get update

Install libdar3c2a from dapper packages using the following command

sudo apt-get install libdar3c2a

Once this finished the installation you need to remove the line we have added in /etc/apt/sources.list for dapper save the file and exit

Now you need to update the source list using the following command

sudo apt-get update

This will complete the installation now if you want to open the application go to Applications&#8212;>Accessories&#8212;>KDar
(Disk-Based Archive Tool)

---

### Post by stinger30au on 2007-07-14
awesome. thank you. i will try it. hopefully i wont destroy anything!

---

### Post by stinger30au on 2007-07-14
ok i did everything you said, and it downloaded the file it had to and gave me this
 sudo apt-get install libdar3c2a
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpoppler1-qt
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libdar3c2a
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 429kB of archives.
After unpacking 1077kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe libdar3c2a 2.2.4-2ubuntu2 [429kB]
Fetched 429kB in 4s (100kB/s)      
Selecting previously deselected package libdar3c2a.
(Reading database ... 201115 files and directories currently installed.)
Unpacking libdar3c2a (from .../libdar3c2a_2.2.4-2ubuntu2_i386.deb) ...
Setting up libdar3c2a (2.2.4-2ubuntu2) ...

and i went to applications accessories, and no kdar :-((
any other suggestions?

---

### Post by stinger30au on 2007-07-14
ok. i figured it out.
after you edit the sources list and do this

sudo apt-get update

Install libdar3c2a from dapper packages using the following command

sudo apt-get install libdar3c2a

you also need to do this

sudo apt-get install kdar

NOW you can go back and remove the sources file and remove this

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe


now do the 

sudo apt-get update

all done!!

AWESOME!!!

thanks so much

---

### Post by jwillar on 2007-10-27
I am fairly new to Linus and changing important file via the Konsle makes me nervous. I like approaching the problem from the GUI side if possible. In Kubuntu, open Adept Manager the from the menu 'Adept' open 'Manage.  Next, open the tab 'Third_Party Software' and add your source string.  Save and go back to the main window and hit the 'Fetch Updates" and your done.  Now KDar will list from either Adept Manager or Add/Remove Programs.  

Hope this helps,
jwillar

---

### Post by wickstopher on 2008-01-10
jwillar: unfortunately, kdar has been removed from the repositories for newer versions of (k)ubuntu.

I know this thread has been marked as solved, but there is a much easier way to go about installing kdar in a more recent version of (k)ubuntu without having to mess around with the sources.list file and risk causing problems with your system.  All you have to do is go to [http://packages.ubuntu.com]("http://packages.ubuntu.com") and the .deb files are available for download in the Dapper section.

here are the links for the necessary .deb packages:

libdar3c2a (pre-requisite for installing the kdar package):
[http://packages.ubuntu.com/dapper/libs/libdar3c2a]("http://packages.ubuntu.com/dapper/libs/libdar3c2a")

kdar:
[http://packages.ubuntu.com/dapper/kde/kdar]("http://packages.ubuntu.com/dapper/kde/kdar")

This got kdar installed for me just fine, and is much less of a hassle and potential risk than editing your sources.list file to synch up with outdated repositories!  Hope this helps.

---

### Post by Andreas_DK on 2008-02-25
Does this approach of installing KDar from debian packages also work for Gutsy Gibbon  (7.10)?

Compiling from the sources does not work (see here [http://ubuntuforums.org/showthread.php?t=336802](http://ubuntuforums.org/showthread.php?t=336802))

Best regards
Andreas

---

### Post by wickstopher on 2008-02-26
Yes, it does.  My apologies for not mentioning that I am running Gutsy and installed the packages just fine.  It may be important to note based on the wording of your question that these are packages provided on the Ubuntu package website, not Debian.  It achieves the exact same results as adding the Edgy repos to your sources.list, using aptitude to install the software, and then removing the repositories, except you don't have to mess around with manually editing the file.

Also, this method needs an update.  I recently reinstalled Gutsy on my machine.  I was running Mint Daryna previously, and went back to a pure Gutsy installation.  After installing Kdar, I attempted to do a backup, and it ended up crashing on me several times.  I ended up running kdar from a command line to see if I could figure out the problem, and it turned out that it also relies on a package called drkonqi in order to run successfully.  This package was no longer in Gutsy Gibbon, but it indicated a replacement in kdebase-runtime-data.   I installed this package and everything went smoothly after that.

So, in addition to installing the 2 older packages from Dapper listed in my previous post, you will need to:

```
sudo apt-get install kdebase-runtime-data
```

---

