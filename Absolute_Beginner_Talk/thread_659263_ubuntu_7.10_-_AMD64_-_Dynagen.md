---
title: "ubuntu 7.10 - AMD64 - Dynagen"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by 125franki on 2008-01-05
Good day all,

First,  I am new to the Linux environment. (But I would like to learn)

I want to use Dynagen and Dynamips on the following system:

     -Computer-
     Processor		                : 2x AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
     Memory		                : 2062MB (1214MB used)
     Operating System               : Ubuntu 7.10
     -Version- 
     Kernel		                   : Linux 2.6.22-14-generic (x86_64)
     Compiled		                : #1 SMP Tue Dec 18 05:28:27 UTC 2007
     C Library		                  : GNU C Library version 2.6.1 (stable)
     Distribution		         : Ubuntu 7.10
     -Current Session-
     Computer Name		   : george
     User Name		              : frank (frank)
     Home Directory		     : /home/frank/
     Desktop Environment          : GNOME 2.20 (session name: Default)
     -Misc-
     Uptime		                 : 7 hours, 1 minute
     Load Average		      : 0.46, 0.29, 0.13[/INDENT]

I can find a few of posts saying that Dynamips and Dynagen are working just fine with an Intel base processor.  On the other hand,  I did not see any post stating that Dynamips and Dynagen were working fine with an AMD64. 

Also, I did not find a Debian package for Dynagen on AMD64. (Only for I386)

So my questions are:

  Is it possible to installed Dynamips/Dynagen on a AMD64 ?
  If you had luck with this type of installation is it possible for you to post it ?
  
Thanks

125franki

---

### Post by ~LoKe on 2008-01-05
Dynagen is in the repositories.
```
[15:04:11 loke]$ sudo apt-cache search Dynagen
dynagen - Cisco 7200 Router Emulator Command Line Interface
```

Try...
```
sudo apt-get install dynagen
```

---

### Post by 125franki on 2008-01-05
Good day LoKe

--------  I am trying the command you recommend, but not luck:

frank@george:~$ sudo apt-cache search Dynamip[/B]s
dynagen - Cisco 7200 Router Emulator Command Line Interface
frank@george:~$
frank@george:~$
frank@george:~$
frank@george:~$
frank@george:~$ sudo apt-get install Dynamips
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package Dynamips
frank@george:~$
frank@george:~$
frank@george:~$ sudo apt-cache search Dynagen
dynagen - Cisco 7200 Router Emulator Command Line Interface
frank@george:~$
frank@george:~$
frank@george:~$
frank@george:~$ sudo apt-get install Dynagen
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package Dynagen
frank@george:~$   
              
--------------  Also, I am trying to the the following:(ok,  not good but I am trying) 

oot@george:/usr/bin# dynamips-0.2.7-amd64.bin -H 7200&
[2] 9846
root@george:/usr/bin# Cisco Router Simulation Platform (version 0.2.7-amd64)
Copyright (c) 2005-2007 Christophe Fillot.
Build date: May 26 2007 11:55:39

ILT: loaded table "mips64j" from cache.
ILT: loaded table "mips64e" from cache.
ILT: loaded table "ppc32j" from cache.
ILT: loaded table "ppc32e" from cache.
Hypervisor: unable to create TCP sockets.
Shutdown in progress...
Shutdown completed.

-------- Then (ok not good either but still trying)

root@george:/home/frank/Desktop/Dynamips/test_with_dynagen/dynagen-0.10.1# apt-get install dynagen
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  dynagen: Depends: dynamips (>= 0.2.6-0.2.7RC3) but it is not installable
E: Broken packages
root@george:/home/frank/Desktop/Dynamips/test_with_dynagen/dynagen-0.10.1#              

-------------------------

Is it possible that I am using I386 package and I should be using AMD64 package ?

Also, just to make sure I understand well. Since I am using Ubuntu, I have to used Debian package. Is this right ?

Thanks

125franki

---

### Post by ~LoKe on 2008-01-05
Case sensitive.
```
sudo apt-get install dynagen
```

---

### Post by 125franki on 2008-01-05
Hi LuKe,

Ok I am trying the command "apt-get install dynagen" and I have to following result:

---------------------------------

[sudo] password for frank:
root@george:~# sudo apt-get install dynagen
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  dynagen: Depends: dynamips (>= 0.2.6-0.2.7RC3) but it is not installable
E: Broken packages
root@george:~#


Thanks

125franki.

---

### Post by 125franki on 2008-01-05
Good day all,

I have find the following:

(extract from "http://www.ipflow.utc.fr/index.php/Cisco_7200_Simulator_FAQ")

If you have an AMD64 or an Intel with EM64T, you have to specify the "noexec=off"     option to the Linux kernel boot command line (thanks to Yannick for this information). 

In my case I have an AMD64

How do I change the Kernel with the command "noexec=off" ?

Thanks 

123frank

---

### Post by zvacet on 2008-01-05
```
sudo apt-get install dynamips
```

After that you will be able to install your program.And off topic,why you use 64 bit version when you have 2GB or ram?It will be much easyer to you to use 32 bit version,but that is your choice.

---

### Post by 125franki on 2008-01-05
Good day zvacet,

I did tried the command the you suggest. (please see belows)

--------------------------------------
root@george:~# sudo apt-cache search dynamips
dynagen - Cisco 7200 Router Emulator Command Line Interface
root@george:~#
root@george:~#
root@george:~# sudo apt-get install dynamips
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package dynamips is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dynamips has no installation candidate
root@george:~#                                       

---------------------------------------------

For the 32 and 64 bit version. I just assumed that the 64 bit would be better on a AMD64.

If you have anymore suggestion please just lets me kno

Thanks


125franki

---

### Post by 125franki on 2008-01-06
Good day all,

Ok this was becoming a bit hard for me. So I did a downgrade from the 64 bit version to the 32 bit version. I was than able to install Dynamips and dynagen with the followings two commands:

   sudo apt-get install dynamips
   sudo apt-get install dynagen

I would like to thanks LoKe and zvacet for their helps.

Thanks to all and have a nice days

(I still have a few problems but the are related to Dynagen)

125frank

---

