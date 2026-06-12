---
title: "opera in ubuntu!!!"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by ishwar on 2007-09-29
hello there.. before i started this thread .. i searched and browesed thru many of the post's.. i understand the pain someone takes to read these posts and reply them carefull for nothing.!!!!!!! i thank the person from the bottom of my heart.. 

okay now the prob is .. i have been using ubuntu for a while.. today i started newstuff after a long gap!! i have used redhat b4 and used opera which was awsome!! so i got it and installed with my GUI application then had some errors with dependencies .. so i re-did that again using apt.. with following result..

my problem is: i dont have a short cut in my menu list!!! i cld use it, by opening it from a terminal without a prob!! 

sudo apt-get install opera
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed
  opera
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5655kB of archives.
After unpacking 13.1MB of additional disk space will be used.
Selecting previously deselected package opera.
(Reading database ...
dpkg: serious warning: files list file for package `libogg-dev' missing, assumin
g package has no files currently installed.

dpkg: serious warning: files list file for package `libslp1' missing, assuming p
ackage has no files currently installed.

dpkg: serious warning: files list file for package `libsndfile1' missing, assumi
ng package has no files currently installed.

dpkg: serious warning: files list file for package `libslang2' missing, assuming
 package has no files currently installed.

dpkg: serious warning: files list file for package `libtag1-dev' missing, assumi                                            ng package has no files currently installed.

dpkg: serious warning: files list file for package `libsm6' missing, assuming pa                                            ckage has no files currently installed.

dpkg: serious warning: files list file for package `libattr1-dev' missing, assum                                            ing package has no files currently installed.
132995 files and directories currently installed.)
Unpacking opera (from .../opera_9.23-20070809.6dapper1_i386.deb) ...
Setting up opera (9.23-20070809.6dapper1) ...


i dont know what is dpkg error.. and i cld not resolve the dependencies!!!! with apt.. can anyone pls suggest me what to do!!


thanx a million for u r time

reg
ishwar

---

### Post by obscur156 on 2007-09-29
I am not sure but try "sudo aptitude install opera".Usually "aptitude"takes care of dependencies.(if i am not wrong)

If  the terminal see opera , i guest its in your repositorie,its a good thing.
Maybe you can try ADD/REMOVE to install it or SYNAPTIC PACKAGE MANAGER.

Or you can go to the OPERA website to download it from there.
[http://www.opera.com/download/?platform=linux]("http://www.opera.com/download/?platform=linux")

And if you dare trying an alpha version you can try that package.
[http://snapshot.opera.com/unix/snapshot-1600/intel-linux/opera_9.50-20070928.6-shared-qt_i386.deb]("http://snapshot.opera.com/unix/snapshot-1600/intel-linux/opera_9.50-20070928.6-shared-qt_i386.deb")

Best regards,good luck budy.

---

### Post by Tyl3r on 2007-09-29
sudo apt-get -f install
This will detect and install all the residual dependencies ;)

Btw imo it's better to use the deb packages from opera site, or if you don't mind testing new features you can refer to the second link obscure posted for you.

---

### Post by TedGarvin on 2007-09-29
Or you get get Automatix and use that.  It will set it all up automatically, but you don't really learn anything.

---

### Post by chessercizes on 2007-09-29
> Or you get get Automatix and use that. It will set it all up automatically, but you don't really learn anything.

Please do correct me if i'm wrong, but automatix can really eff up your system right?

just asking. =)

---

### Post by Beernut on 2007-09-29
> **chessercizes said:**
> Please do correct me if i'm wrong, but automatix can really eff up your system right?

just asking. =) 

I always use Automatix and never have had any problems.  I might just be getting lucky though. :)

---

### Post by Sef on 2007-09-29
> I always use Automatix and never have had any problems. I might just be getting lucky though. 

Yes, it can.   

Ishwar:

What version of Ubuntu are you using?

---

### Post by ishwar on 2007-09-30
hi guys thanx a lot for all u r replies.. 
i am using ubuntu 6.06!!!
i m going to tryout today .. will post the results ASAP!!!

thanx again . ishwar

---

### Post by ishwar on 2007-09-30
hi there guys.... i removed and reinstalled the opera.. with the following output.. reading that i understand that (to my knowledge) is that sitting in a wrong place i.e in root!!!! without the root user permission.. again after installing i cld run da prog thru the terminal.. its awsome!!! i also tried to use synaptic but wiht the same result.. i tried installing individual packeges thru goole'g them ...  but its the same.. 

the error report follows.. pls help me!! 

opera
opera: $HOME set to /root. Use -personaldir if you do not want to use /root/.opera/
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed


reg
ishwar

---

### Post by Jimmyfj on 2007-09-30
Hi

I write this from within the opera browser in 7.10 Gutsy Gibbon right now. The easiest way to install Opera is by going to their home page:

[http://www.opera.com/download/?platform=linux](http://www.opera.com/download/?platform=linux)

And simply select the version of OS you run. Download the .deb file and let dep-installer do its job. My Opera installed without any issues and just works nice. Give it a try, but stay away from Automatix it's know to break systems along the way so why risk it?

---

### Post by TenPlus1 on 2007-09-30
Going to the [www.opera.com](www.opera.com) website and selecting the Ubuntu distro to download, double-clicking will simply install the package and that's it, working...

---

### Post by ishwar on 2007-09-30
hi thank u for the reply... 
i solved the problem...or it got solved by my update manager...
i tried to install it from the web site .. there was conflict error msg from my installer. at the same time it said there is a updated version available ... even though i tried installing the old one!! after finishing it my update manager installed the latest version .. so now everything is up and running..


so prob solved. but i really dont know whats going on behind the screen... 

thanx again
eswar

---

### Post by ishwar on 2007-09-30
another prob... 

i guess its worth trying .. and i belive ubuntu will do or can do more than the other famous OS!!


anyone tried real pluggins for opera. to stream .ram .. if any cld let me know how to install it ( in my case i have got real player installed already) but i dont see the pluggins in my opera list. i guess i need to modify sth in my .conf file .. but i dont know what to change and where!!! 

regs
ishwar

---

