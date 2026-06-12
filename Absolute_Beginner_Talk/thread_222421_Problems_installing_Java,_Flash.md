---
title: "Problems installing Java, Flash"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Chris R on 2006-07-25
I've tried to use apt-get to install both of these, but no luck, with Flash I get

 > chris@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chris@ubuntu:~$



Java gets me 

> chris@ubuntu:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chris@ubuntu:~$


I considered using EasyUbuntu, but that doesn't work, as while apt-get will get the program, the "tar -zxf easyubuntu-3.021.tar.gz" command seems to do nothing, thus when I put in "sudo python easyubuntu.in" it tells me 

> chris@ubuntu:~$ wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.ta](http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.ta) r.gz
--15:40:47--  [http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.021.tar.gz)
           => `easyubuntu-3.021.tar.gz.1'
Resolving easyubuntu.freecontrib.org... 213.246.58.132
Connecting to easyubuntu.freecontrib.org|213.246.58.132|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 92,260 (90K) [application/x-tar]

100%[====================================>] 92,260       129.25K/s

15:40:48 (128.95 KB/s) - `easyubuntu-3.021.tar.gz.1' saved [92260/92260]

chris@ubuntu:~$ tar -zxf easyubuntu-3.021.tar.gz
chris@ubuntu:~$ cd easyubuntu
[B]chris@ubuntu:~/easyubuntu$ sudo python easyubuntu.in
System sanity check: Failed!
Errors:
--------
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?

EasyUbuntu is now trying to run 'dpkg --configure -a'
System sanity check: Failed!
Errors:
--------
dpkg: status database area is locked by another process

EasyUbuntu will not run before these errors are fixed. Please fix them and try a gain
chris@ubuntu:~/easyubuntu$[/B]



Any help on either of these issues would be very much appreciated.

---

### Post by IrishGangsta on 2006-07-25
did u enable the multiverse and universe repositories?

---

### Post by Chris R on 2006-07-25
I have no idea how to do that, and what exactly will it do?

---

### Post by simonn on 2006-07-25
It looks like there is another instance of apt-get, synaptic, system update (or whatever it's called) running, make sure these are closed.

To go into more detail...

dpkg is the basic package manager.
apt-get is a front end to dpkg which handles downloading, dependencies etc
synaptic and update manager (or whatever it is called, again) are front ends to apt-get.

Only one instance of dpkg can be used at any one time.

I hope that makes sense. If not, please ask and I will do my best to clarrify.

---

### Post by IrishGangsta on 2006-07-25
i dont know the whole meaning behind it. 
But i do know that it is necissary for all Ubuntu Linux users to do it.

Go to your terminal applications>accessories>terminal and type the comand
sudo gedit /etc/apt/sources.list
Enter your password


then highlight everything 
Delete it
and paste this over it...


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free 




After you do this 
Save it and close. 
Then try to install your flash plug in once again with the first command u tried.
sudo apt-get install flashplugin-nonfree

---

### Post by Chris R on 2006-07-25
> **simonn said:**
> It looks like there is another instance of apt-get, synaptic, system update (or whatever it's called) running, make sure these are closed.

To go into more detail...

dpkg is the basic package manager.
apt-get is a front end to dpkg which handles downloading, dependencies etc
synaptic and update manager (or whatever it is called, again) are front ends to apt-get.

Only one instance of dpkg can be used at any one time.

I hope that makes sense. If not, please ask and I will do my best to clarrify.

That made sense, I'll try it again and make sure those are closed.

> **IrishGangsta said:**
> i dont know the whole meaning behind it. 
But i do know that it is necissary for all Ubuntu Linux users to do it.

Go to your terminal applications>accessories>terminal and type the comand
sudo gedit /etc/apt/sources.list
Enter your password


then highlight everything 
Delete it
and paste this over it...




I just saved that, hopefully is this file is corrupted Ubuntu will still start?

---

### Post by Chris R on 2006-07-25
> chris@ubuntu:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree


That's what I got this time.


Same with Java: 
> chris@ubuntu:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre


---

### Post by Sef on 2006-07-25
To get a simple way to add the repositories, [click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by Chris R on 2006-07-25
> **Sef said:**
> To get a simple way to add the repositories, [click here.]("https://help.ubuntu.com/community/Repositories/Ubuntu")


I tried those methods just now, here's the results I got

> Building dependency tree... Done
Package sun-java5-plugin is not available, but is referred to by another package .
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-plugin has no installation candidate


However, when I first did it there was the Ubuntu 6.06 LTS binary at the top of the list in the Software Preferences, so I told it to do the Universe and Multiverse on the Source, which was the 2nd in line. After that I got the error message up above, when I went back into the Software Packages there's now a Ubuntu 6.06 LTS Source at the top of the list, and when I try to get Multiverse or Universe for either Sources or the Binary I get an error message:

> E: Type 'sudo' is not known on line 34 in source list /etc/apt/sources.list
E: Unable to lock the list directory


Should I try to edit sources.list myself, or would I be able to just wipe source.list clean and then redo it all with Software Preferences?

---

### Post by IrishGangsta on 2006-07-25
u know
i think u can just go to 
System>admin>synaptics package manager

Search for keyword JAVA

And install java runntime environment and sun java 5 and search for flash also

This may save you alot of unneeded confusion

---

### Post by Chris R on 2006-07-25
> **IrishGangsta said:**
> u know
i think u can just go to 
System>admin>synaptics package manager

Search for keyword JAVA

And install java runntime environment and sun java 5 and search for flash also

This may save you alot of unneeded confusion


I think I tried that earlier but to no avail, but now the list in the SPM is completely blank.

---

### Post by Chris R on 2006-07-25
Right, so I just wiped the sources.list file completely blank, went into Software Preferences, set up all the channels, the SPM list is back. According to SPM java-common is installed, along with a couple other java componets, but I'm guessing somethings wrong since Frostwire won't work, and that's dependant on java.

---

### Post by aeto on 2006-07-25
good. now that u have set up ur repositories (u can go here [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic) to get a sources.list generated according to what kinda downloads you want), u can now install automatix [http://www.getautomatix.com/index.php](http://www.getautomatix.com/index.php)

---

### Post by Chris R on 2006-07-25
Automatix got Java to install, and several other codecs and useful programs, now to get 3d so google earth will run. Where can I find a good guide to installing the drivers from nvidias site? The last time I tried I broke linux, so I'm kind of weary.

-edit- Appearntly automatix does that too, thus now UT2004 and Google Earth work. Yay. Thanks all. Next up is finding a way to get at least HL1 going.

---

