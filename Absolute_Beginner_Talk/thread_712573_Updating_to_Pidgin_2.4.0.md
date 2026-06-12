---
title: "Updating to Pidgin 2.4.0"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by darthlunchbox42 on 2008-03-01
I'm trying to figure out how to update my version of pidgin to 2.4.0, and I can't figure out how.  I got a download from [here](http://www.getdeb.net/comment.php?rel_id=2259).  I tried to open the file but it gives me a 'broken dependencies' error.  So I tried the following (a comment on the file from the link):
> To automatically remove the older packages, download the new ones, open up a terminal, \"cd\" to where you\'ve downloaded the .debs and type \"sudo dpkg -i *.deb\". This way, the older packages will be replaced with the new ones.
This also gave me an error:
> Selecting previously deselected package pidgin.
(Reading database ... 102478 files and directories currently installed.)
Unpacking pidgin (from pidgin_2.4.0-1~getdeb1_i386.deb) ...
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on pidgin-data (>= 1:2.4.0); however:
  Version of pidgin-data on system is 1:2.2.1-1ubuntu4.1.
 pidgin depends on libpurple0 (>= 1:2.4.0); however:
  Version of libpurple0 on system is 1:2.2.1-1ubuntu4.1.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin

The ubuntu update manager then pops up but then give me an error:
> Broken Dependencies

This system has broken dependencies.  This application cannot continue until this is fiexed.  To fix it run 'sudo synaptic' or 'sudo apt-get install -f'.

The second one gave me this:
[quote]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  pidgin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1868kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 102515 files and directories currently installed.)
Removing pidgin ...


And the first opened up Synaptic, but it gave me an error message along the lines of broken dependencies.  

I'm really confused and have no idea what these errors me.  Any help would be appreciated.

EDIT:
I'm trying to open Pidgin (in hopes that I didn't mess up what came with Ubuntu in the first place), but it just doesn't open.  And I try the following:
> ford@ford-desktop:~$ sudo apt-get install pidgin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pidgin is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  pidgin: Depends: pidgin-data (>= 1:2.4.0) but 1:2.2.1-1ubuntu4.1 is to be installed
          Depends: libpurple0 (>= 1:2.4.0) but 1:2.2.1-1ubuntu4.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ford@ford-desktop:~$ 

---

### Post by Gepetto on 2008-03-01
You're going to wanna uninstall Pidgin first, through the add/remove programs.

Then go to [http://www.getdeb.net/release.php?id=2259](http://www.getdeb.net/release.php?id=2259) and download all three packages. Install pidgin-data first, replacing the older one with the new one. Then do libpurple, again replacing old with new. Then you can install the new pidgin package.

---

### Post by fetisha on 2008-03-02
> **Gepetto said:**
> You're going to wanna uninstall Pidgin first, through the add/remove programs.

Then go to [http://www.getdeb.net/release.php?id=2259](http://www.getdeb.net/release.php?id=2259) and download all three packages. Install pidgin-data first, replacing the older one with the new one. Then do libpurple, again replacing old with new. Then you can install the new pidgin package.

I click on the pidgin-data first and the package install successfully installs it (after I removed the older version of pidgin via add/remove), but when I go to install lib purple, the package installer tells me this: 

Error:Wrong Architecture 'i386'
multi-protocol instant messaging library
libpurple is a library intended to be used by programmers seeking to write an IM client that connects to many IM networks. Currently supported are: AIM/ICQ, Yahoo!, MSN, IRC, Jabber, Napster, Zephyr, Gadu-Gadu, Bonjour, Groupwise, Sametime, SILC, and SIMPLE.
Some extra packages are suggested to use increased functionality:
* tcl8.4, tk8.4:
* Support for writing plugins with Tcl/Tk 

Did I do something wrong?

---

### Post by Ardrias on 2008-03-02
Looks like you're running 64-bit Ubuntu? Then the 32-bit Pidgin package wont install. 

On a sidenote, I compiled it from source, but it segfaults if I compile with msnp14 support. Anyone get this working?

---

### Post by darthlunchbox42 on 2008-03-02
I tried to open the Add/Remove applications thing, and it's spits an error out at me:  "Failed to check for installed and available applications".  I also tried to work with the pidgin data file and it gives me the broken dependencies error, too.  Finally, I'm not running x64, the pidgin file I downloaded is called "pidgin_2.4.0-1~getdeb1_i386.deb", but I'm not certain as to what the i386 means.

---

### Post by Gepetto on 2008-03-02
trying doing 
apt-get -f install
Then try running the intsalls again. When you run the pidgin data file install, what dependencies are they spitting at you that you need?
The i386 at the end just means that it's the deb file for the standard 32 bit operating system, so if you're not running 64 bit, then that should be the right one.

---

### Post by darthlunchbox42 on 2008-03-03
Hey, so I did what you suggested gepetto, and it works great.  Everything's back to normal.  Thanks!

---

### Post by highpitch on 2008-03-29
I got this error when trying to run Pidgin 2.4.0 after  "sudo make install"

> pidgin: symbol lookup error: pidgin: undefined symbol: purple_account_get_current_error

I fixed it by execute 

> sudo apt-get remove pidgin libpurple0

I guess it must remove the old libpurple0 first. Uninstall the old Pidgin doesn't seem to automatically remove libpurple0 Hope it helps.

---

