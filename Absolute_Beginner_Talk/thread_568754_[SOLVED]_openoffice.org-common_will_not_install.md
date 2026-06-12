---
title: "[SOLVED] openoffice.org-common will not install"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-10-06
I have been trying to get openoffice to reinstall and get errors both in terminal and synaptic

in synaptic they end up being broken and cannot be fixed and in terminal the errors are

dpkg: dependency problems prevent configuration of openoffice.org-style-human:
openoffice.org-style-human depends on openoffice.org-common (= 2.2.0-1ubuntu5); however:
Package openoffice.org-common is not installed.
dpkg: error processing openoffice.org-style-human (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
openoffice.org-core depends on openoffice.org-common (>> 2.2.0); however:
Package openoffice.org-common is not installed.
dpkg: error processing openoffice.org-core (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
openoffice.org-style-human
openoffice.org-core

any help would great, this started after a update

---

### Post by Freqs on 2007-10-06
Did you try it twice? Maybe the second time will work :)

---

### Post by J11Gyro on 2007-10-06
no duh

---

### Post by philinux on 2007-10-06
> **Freqs said:**
> Did you try it twice? Maybe the second time will work :)

Help like this is no help at all. [-X

---

### Post by por100pre1 on 2007-10-06
Please try this:

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

You are not alone with this issue. :-k

---

### Post by J11Gyro on 2007-10-06
been there done that many times in past two days

---

### Post by por100pre1 on 2007-10-06
Let's see where the problem is:

```
sudo dpkg-reconfigure openoffice.org-style-human
```

```
sudo dpkg-reconfigure openoffice.org-core
```

Post the results. :-k

---

### Post by J11Gyro on 2007-10-06
here is the error list


root@gyro-desktop:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcompizconfig0 ndiswrapper-common libwww-ssl0 libdecoration0
  libcompizconfig-backend-gconf libraptor1 libemeraldengine0 libxul-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openoffice.org-common
Recommended packages:
  openoffice.org-style-industrial openoffice.org-style-tango
  openoffice.org-style-crystal openoffice.org-style-andromeda
  openoffice.org-style-hicontrast
The following NEW packages will be installed:
  openoffice.org-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
Need to get 0B/12.0MB of archives.
After unpacking 35.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 198789 files and directories currently installed.)
Unpacking openoffice.org-common (from .../openoffice.org-common_2.2.0-1ubuntu5_all.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu5_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/share/template/wizard/letter/pl/bus-office_l.ott')
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@gyro-desktop:~# sudo dpkg-reconfigure openoffice.org-style-human
/usr/sbin/dpkg-reconfigure: openoffice.org-style-human is broken or not fully installed
root@gyro-desktop:~# sudo dpkg-reconfigure openoffice.org-core
/usr/sbin/dpkg-reconfigure: openoffice.org-core is broken or not fully installed
root@gyro-desktop:~#

---

### Post by por100pre1 on 2007-10-06
Have you tried aptitude?

```
sudo aptitude reinstall openoffice.org-core openoffice.org-style-human
```

post the results. :-k

**EDIT:** That ' ./usr/lib/openoffice/share/template/wizard/letter/ pl/bus-office_l.ott' doesn't look good. :-k

---

### Post by Arcturus691 on 2007-10-06
I believe I am also having the same problem.   I attempted to update by using the update manager and it appears that the openoffice common 5 package is broken. The error is Broken count > 0.
So in the terminal I ran the command:
sudo apt-get install -f
(see attachment error1.txt for output)

I tried to fix the problem with synaptic and still no luck.

Next I tried the following command:
sudo aptitude reinstall openoffice.org-core openoffice.org-style-human
(see attachment error2.txt for output)

My next step would be to completely remove openoffice with synaptic and reinstall but I would like to see if anyone else has any suggestions before I attempt that.
    
I am running on Feisty AMD64 Ubuntu.

---

### Post by J11Gyro on 2007-10-07
Well it looks like I am not alone in this, that is for sure LOL I am using this load up to learn  anyway so I may do a clean OS install and start over, not quite sure.

---

### Post by J11Gyro on 2007-10-10
Transfered a bunch of files to CD and was about to reload feisty but got stubborn and decided I will try and figure this one out, any new ideas?  :guitar:

---

### Post by Arcturus691 on 2007-10-12
:biggrin: I found an error in the script!!    If you look at line 6650 in the /var/lib/dpkg/available file you will find that at the depends section there is a list of all the dependancies.  I looked at the file available-old in the dir and compared them.   There is a dependancy called 
time 
in the available-old file it is listed as 
time
and in the current available file it is 
| ime

oooppsss looks like a typo. Erase the pipe and the space, replace it so it looks like below:
time

So I then ran the command:
 sudo aptitude reinstall openoffice.org-core openoffice.org-style-human

and it worked without any errors.
Synaptic now does not report a broken link and I was able to update my system.

Please let me know if this works for others and I'll mark the thread complete.  Also who should I notify about this script error so it can get fixed?

---

### Post by ryanVickers on 2007-10-12
>     [quote]    

                 [I]Did you try it twice? Maybe the second time will work :smile:

[/I]                                  
Help like this is no help at all. [-X
[/quote]
Yes it is - it worked for me! :p

---

### Post by J11Gyro on 2007-10-15
Still with all the work cannot get Open office to reinstall or update, I think I am just going to reload system when Gutsy releases and go just linux with no dual boot and XP:lolflag:

---

### Post by Arcturus691 on 2007-10-19
Ok the issue is not solved yet.  Due to an issue with my hard drive I had to reinstall ubuntu.  When updating open office that comes with the original Feisty 7.04 DVD to the latest version I get the broken package issue again and this time line 6650 in the available file does not contain the same information.  So there are two seperate issues here.  The first is if you installed ubuntu about six months ago and ran the updates regularly until you get to the open office common update.   This probably can fixed by the instructions in my previous post (this is a guess, I am not an expert in ubuntu, I know enough about linux to be dangerous ;) LOL )  The second issue is if you just installed ubuntu recently and ran all the updates.  Either way it seems like you get a broken pakage and you can no longer update anything.  Ok below is my terminal output:

XXXXXX@XXXXXX:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-common
Recommended packages:
  openoffice.org-style-industrial openoffice.org-style-tango
  openoffice.org-style-crystal openoffice.org-style-andromeda
  openoffice.org-style-hicontrast
The following packages will be upgraded:
  openoffice.org-common
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/12.0MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 103466 files and directories currently installed.)
Preparing to replace openoffice.org-common 2.2.0-1ubuntu3 (using .../openoffice.org-common_2.2.0-1ubuntu5_all.deb) ...
Unpacking replacement openoffice.org-common ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu5_all.deb (--unpack):
 [COLOR="DarkRed"]corrupted filesystem tarfile - corrupted package archive[/COLOR]
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 [COLOR="DarkRed"]/var/cache/apt/archives/openoffice.org-common_2.2.0-1ubuntu5_all.deb[/COLOR]
E: Sub-process /usr/bin/dpkg returned an error code (1)

Notice the lines highlighted in red.  I think this is telling me that the file:
openoffice.org-common_2.2.0-1ubuntu5_all.deb is corrupted.  Running synaptic and attempting to fix the broken package gives an error that the package is corrupted. 

J11Gyro do you get the same result if you run synaptic and try to fix the broken package?

---

