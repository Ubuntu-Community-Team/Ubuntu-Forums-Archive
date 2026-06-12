---
title: "Yet more install problems"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by KeyboardJockey on 2006-05-13
After an untold amount of grief fitting a new hard drive I finally managed to get breezy up and running on the new drive and used Morphix so that I could see both drives to copy the data across from one to the other.  I've still got things wrong which may or may not be hardware problems (HP deskjet won't print) but I'm having trouble rebuilding my system such as getting streaming media going and downloading.

I having problems accessing RealPlayer10 but I reckon that there are ways and means of sorting this out which I should be able to do.

The biggie problem I'm having is installing aMule.  I've tried installing via Synaptic and also via Terminal but no joy.

When I try to install in Synaptic I get the following error message:

E: /var/cache/apt/archives/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb: unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install)
E: /var/cache/apt/archives/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb: unable to stat `./usr/share/man/fr' (which I was about to install)
E: /var/cache/apt/archives/amule_2.0.3-1ubuntu4_i386.deb: unable to stat `./usr/share/pixmaps' (which I was about to install)

What on earth do I need to do to sort these problems out.  I love Ubuntu but it is vague when it goes wrong.

I believe that I;ve done something wrong but I cant work out what.  

I've spent about 80 - 100 hours so far in the last month or two just to get the system working and rescue my data from the old drive.

How do I get out of this one?

](*,) 

Many thanks

---

### Post by KeyboardJockey on 2006-05-13
Tried to get new repositories but it messed up.  Got an error message and couldn't quit synaptic without forcing it to quit even though I'd selected apply marked changes.

Tried to go in to Terminal to download amule and got the following:

$ sudo apt-get install amule
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  libgtk2.0-0: Depends: libgtk2.0-common (>= 2.8.6-0ubuntu2.1) but 2.8.6-0ubuntu2 is to be installed
               Depends: libgtk2.0-bin (>= 2.8.6-0ubuntu2.1) but 2.8.6-0ubuntu2 is to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
marc@marc:~$ apt-get -f install
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


Any ideas?  From what I can see it is the last line of the above that seems to be causig the problem

Many thanks

---

### Post by KeyboardJockey on 2006-05-13
Tried again:

marc@marc:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgtk2.0-bin libgtk2.0-common
The following packages will be upgraded:
  libgtk2.0-bin libgtk2.0-common
2 upgraded, 0 newly installed, 0 to remove and 149 not upgraded.
10 not fully installed or removed.
Need to get 0B/3435kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 57229 files and directories currently installed.)
Preparing to replace libgtk2.0-common 2.8.6-0ubuntu2 (using .../libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb) ...
Unpacking replacement libgtk2.0-common ...
dpkg: error processing /var/cache/apt/archives/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb (--unpack):
 unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libgtk2.0-bin 2.8.6-0ubuntu2 (using .../libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement libgtk2.0-bin ...
dpkg: error processing /var/cache/apt/archives/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb (--unpack):
 unable to stat `./usr/share/man/fr' (which I was about to install): Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb
 /var/cache/apt/archives/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by KeyboardJockey on 2006-05-13
The whole sorry tale is.....


$ sudo apt-get install amule
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  libgtk2.0-0: Depends: libgtk2.0-common (>= 2.8.6-0ubuntu2.1) but 2.8.6-0ubuntu 2 is to be installed
               Depends: libgtk2.0-bin (>= 2.8.6-0ubuntu2.1) but 2.8.6-0ubuntu2 i s to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a s olution).
marc@marc:~$ apt-get -f install
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Unable to lock the list directory
marc@marc:~$ apt-get -f install amule
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Unable to lock the list directory
marc@marc:~$
marc@marc:~$
marc@marc:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgtk2.0-bin libgtk2.0-common
The following packages will be upgraded:
  libgtk2.0-bin libgtk2.0-common
2 upgraded, 0 newly installed, 0 to remove and 149 not upgraded.
10 not fully installed or removed.
Need to get 0B/3435kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 57229 files and directories currently installed.)
Preparing to replace libgtk2.0-common 2.8.6-0ubuntu2 (using .../libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb) ...
Unpacking replacement libgtk2.0-common ...
dpkg: error processing /var/cache/apt/archives/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb (--unpack):
 unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libgtk2.0-bin 2.8.6-0ubuntu2 (using .../libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement libgtk2.0-bin ...
dpkg: error processing /var/cache/apt/archives/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb (--unpack):
 unable to stat `./usr/share/man/fr' (which I was about to install): Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb
 /var/cache/apt/archives/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
marc@marc:~$
marc@marc:~$ sudo apt-get install amule
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  libgtk2.0-0: Depends: libgtk2.0-common (>= 2.8.6-0ubuntu2.1) but 2.8.6-0ubuntu2 is to be installed
               Depends: libgtk2.0-bin (>= 2.8.6-0ubuntu2.1) but 2.8.6-0ubuntu2 is to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
marc@marc:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgtk2.0-bin libgtk2.0-common
The following packages will be upgraded:
  libgtk2.0-bin libgtk2.0-common
2 upgraded, 0 newly installed, 0 to remove and 149 not upgraded.
10 not fully installed or removed.
Need to get 0B/3435kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... 57229 files and directories currently installed.)
Preparing to replace libgtk2.0-common 2.8.6-0ubuntu2 (using .../libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb) ...
Unpacking replacement libgtk2.0-common ...
dpkg: error processing /var/cache/apt/archives/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb (--unpack):
 unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace libgtk2.0-bin 2.8.6-0ubuntu2 (using .../libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb) ...
Unpacking replacement libgtk2.0-bin ...
dpkg: error processing /var/cache/apt/archives/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb (--unpack):
 unable to stat `./usr/share/man/fr' (which I was about to install): Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb
 /var/cache/apt/archives/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I can see the error but don't know what to do with it.

---

### Post by KeyboardJockey on 2006-05-13
Just tried to fix a broken package in Synaptic and got the following error message.


E: /var/cache/apt/archives/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb: unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install)
E: /var/cache/apt/archives/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb: unable to stat `./usr/share/man/fr' (which I was about to install)


Which is spookily similar to the errors I am getting on the Terminal.

---

### Post by KeyboardJockey on 2006-05-13
Just tried to upgrade apt in synaptic just in case that is the problem and got:

E: /var/cache/apt/archives/libgtk2.0-common_2.8.6-0ubuntu2.1_all.deb: unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install)
E: /var/cache/apt/archives/libgtk2.0-bin_2.8.6-0ubuntu2.1_i386.deb: unable to stat `./usr/share/man/fr' (which I was about to install)
E: /var/cache/apt/archives/amule_2.0.3-1ubuntu4_i386.deb: unable to stat `./usr/share/pixmaps' (which I was about to install)
E: /var/cache/apt/archives/make_3.80-9_i386.deb: unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install)
E: /var/cache/apt/archives/dpkg-dev_1.13.10ubuntu4_all.deb: unable to stat `./usr/share/man/fr' (which I was about to install)
E: /var/cache/apt/archives/devscripts_2.9.4_i386.deb: unable to stat `./usr/share/man/fr' (which I was about to install)
E: /var/cache/apt/archives/apt-build_0.12.9_i386.deb: unable to stat `./usr/share/man/fr' (which I was about to install)

---

### Post by KeyboardJockey on 2006-05-13
OK I'm trying another tack.  I've gone into the file browser and followed the path 

/var/cache/apt/archives/amule_

I can find the amule file and I thought that should I delete this and try to re install amule but it gives me 'permission denied'.

---

### Post by mostwanted on 2006-05-13
The "can't stat" errors usually appear when the repositories you've listed in your sources list are down or if the package for some reason hasn't been uploaded yet. These things happen, servers on the Internet are not always failsafe and there's nothing you can do to get them back up. If you really need to upgrade/install som packages, you can change your server locale (in the sources list, it's in the URLs you reference to), but you can always wait until the servers are back up. Don't panic!

The reason you're getting the same errors in the different programs is because they all use the same backend, Advanced Package Manager (abbreviated APT).

Also, you don't have to make so many posts in such a short period of time :) I appreciate you kept them inside this topic though.

---

### Post by KeyboardJockey on 2006-05-13
[QUOTE=mostwanted]The "can't stat" errors usually appear when the repositories you've listed in your sources list are down. These things happen, servers on the Internet are not always failsafe and there's nothing you can do to get them back up. If you really need to upgrade/install som packages, you can change your server locale (in the sources list, it's in the URLs you reference to), but you can always wait until the servers are back up. Don't panic!

The reason you're getting the same errors in the different programs is because they all use the same backend, Advanced Package Manager (abbreviated APT).

Also, you don't have to make so many posts in such a short period of time :) I appreciate you kept them inside this topic though.[/QUOTE]

Aha! Thank You.  I didn't think that the 'can't stat' error was the key feture of he error  message.  I'm going to leave installing amule until tomorrow.  I just hope I haven't done any damage with my ham fisted terminal pounding. :)   I'm  not going to change the URL as I don't feel confident about the outcome.

The reason I made muliple posts was to put up the results of each operation or workaround that I ws trying to do.  

Many thanks

---

### Post by mostwanted on 2006-05-13
If you post your /etc/apt/sources.list here I'll change it for you. It doesn't really matter what server mirror you download packages from. But yeah, you could also just wait and hope it's gonna be fixed in the meantime.

---

### Post by KeyboardJockey on 2006-05-13
I think that it is a bit more than just the server being offline ](*,) 

I've just tried to re install bittorrent as it doesn't seem to do anything when I select it and I got a very similar error message.

So it is definitely a system problem rather than a case of not being able to get hold of the software. 

What is annoying is that I installed Breezy yesterday.  Had problems with transferring data from the old drive and then re installed Breezy again.  The install onto the first install of breezy went absolutely fine but now I've got my rescued data on the drive aMule fails.

And now Synaptic has died on me. Grrrr!

---

### Post by catlett on 2006-05-13
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) Make your life easy. Follow this link and install Automatix. It will take care of amule and alot of other things.

---

### Post by KeyboardJockey on 2006-05-13
[QUOTE=catlett][http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405) Make your life easy. Follow this link and install Automatix. It will take care of amule and alot of other things.[/QUOTE]


Will this require Synaptic as it now appears to be broken and is giving me the same errors and won't quit unless I 'Force Quit' 

E: /var/cache/apt/archives/apt_0.6.40.1ubuntu10_i386.deb: unable to stat `./usr/share/locale/zh_CN/LC_MESSAGES' (which I was about to install)

---

### Post by catlett on 2006-05-13
The thread explains it well. It uses the terminal to install . It uses repositories and synaptic is affected but I don't think it is used. It was a while ago when I ran it. The thread attached to the link is pretty thorough and should answer that.
It is basically a script that downloads packages and installs . You don't open synaptic package manager and you don't type apt-get but I don't know if the script is accessing synaptic from the command line or not. Check the thread and you can always post in the automatix thread for an answer.

---

### Post by KeyboardJockey on 2006-05-14
[QUOTE=catlett]The thread explains it well. It uses the terminal to install . It uses repositories and synaptic is affected but I don't think it is used. It was a while ago when I ran it. The thread attached to the link is pretty thorough and should answer that.
It is basically a script that downloads packages and installs . You don't open synaptic package manager and you don't type apt-get but I don't know if the script is accessing synaptic from the command line or not. Check the thread and you can always post in the automatix thread for an answer.[/QUOTE]

I tried Automatix and it works - well as usual with Ubuntu it sort of half works -- Still no amule (when I tried to select it from the apps menu it told me that files needed to be removed and pointed me to Advanced which opened synaptic)  so I tried to initialise Azureus which installed but there is no way to search for files or see what files I've shared.   

What shall I do now?  Shall I re install Ubuntu 5.10 yet again (without touching my rescued data) ?

---

### Post by catlett on 2006-05-14
I think it wants you to remove whatever amule files have been installed. Try opening synaptic. It should be on "all" in the left comlumn.
Search through the entries until you come to amule. A package that is NOT installed will have a blank box. An installed package will have a solid block in front of it.
Right click any amule entries and this will highlight it and bring up a menu. Choose "mark for removal". Go through all amule entries like this. Hit "apply" at the top of the synaptic menu. Retry Automatix and see if amule will install
Hopefully there were packages to remove. Because if there were packages to remove then hopefully Automatix is satified and will install amule. If there were no amule packages installed in synaptic then I don't know what to do.

I don't know much about reinstallling without data loss. I know that if you have a "home" partition outside of the "root" partition then only the root partition gets formatted and rewritten. The home folder is left untouched. I don't know what can be done when your home folder is in your root partition.

---

### Post by KeyboardJockey on 2006-05-14
[QUOTE=catlett]I think it wants you to remove whatever amule files have been installed. Try opening synaptic. It should be on "all" in the left comlumn.
Search through the entries until you come to amule. A package that is NOT installed will have a blank box. An installed package will have a solid block in front of it.
Right click any amule entries and this will highlight it and bring up a menu. Choose "mark for removal". Go through all amule entries like this. Hit "apply" at the top of the synaptic menu. Retry Automatix and see if amule will install
Hopefully there were packages to remove. Because if there were packages to remove then hopefully Automatix is satified and will install amule. If there were no amule packages installed in synaptic then I don't know what to do.
[/QUOTE]

Mark for removal doesn't appear in the menu.  It is greyed out. Amule wasn't blocked inthe list either.  I know that there is an aMule file in the var folder but I can't drag and drop it into the trash.
[QUOTE=catlett]
I don't know much about reinstallling without data loss. I know that if you have a "home" partition outside of the "root" partition then only the root partition gets formatted and rewritten. The home folder is left untouched. I don't know what can be done when your home folder is in your root partition.[/QUOTE]

I think tht this might be the best option as I've probably screwed up the OS pretty badly with Automatix.  Oh well heres to another 100 hours work. ](*,)

---

