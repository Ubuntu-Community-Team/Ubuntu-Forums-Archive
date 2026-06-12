---
title: "need e2fsprogs on xubuntu f.fawn"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Cafargo on 2007-10-02
Hello.

A newbie question: I need e2fsprogs in order to inst and run a specific app, and need to know how to go about it. I've not found anything close in the synaptic pkg manager, so where would I start, and how do I install these libs, etc.

many thanks!
Cafargo.

---

### Post by Cafargo on 2007-10-02
addendum: this is on a P2 x86 system.
caf.

---

### Post by schorsch on 2007-10-02
As ext3 (the journaled version of ext2) is the default filesystem for *buntu, they are installed with the default installation. What is the app you are trying to install and where did you get it from?

---

### Post by Cafargo on 2007-10-02
I'm attempting to install a trial version of softimage xsi (Foundation) for linux. Though xsi is sanctioned to run on redhat, I understand one can get it to work on other flavors. hence my experiments. One of the conditions for installing, is for there to be the e2fsprogs libs. I found out through reading other forums that these files do exist, but I could not find myself, as others have also mentioned. Right now, I've unpacked the installations files, but can't run the setup, either from the file manager or from the terminal. The package includes many folders that have been tar and bzip2 compressed, though those respective apps are presently installed on my system. I just would like to be able to run the installation setup, but I guess there are key files missing^

Many thanks.
Caf.

---

### Post by schorsch on 2007-10-02
I just downloaded the full version (as I do not want to give them my personal data for the trial version) from [this]("http://www.softimage.com/downloads/XSI_Foundation/default.aspx") website  and I can run both setup commands for the license manager and the XSI program itself without any problem. I did not install the program.
What is the exact error message? Do you have an 64 bit system installed as the binaries seem to to run only on 32 bit systems?

---

### Post by Cafargo on 2007-10-02
Humm? That's interesting. When I double-click on the setup icon itself from the window manager, now nothing happens. But, the 1st few times I tried it, I got that utility window that prompted me to either open the file with Xarchiver or another app of my choice, so I quit out of that window. From the terminal, I tried directly from the cmd line and with csh, using sudo, but maybe my cmd-line syntax is wrong. I tried this:

valis@valis-desktop:/media/disk/tmp/XSI-6.01-linux32$ sudo ./setup
Password:
sudo: unable to execute ./setup: Permission denied
valis@valis-desktop:/media/disk/tmp/XSI-6.01-linux32$ 

I've then added full permissions to all the bloody files, but I still get the same error. 

I'm obviously doing something basically wrong. 

Many thx.
Caf.

---

### Post by Cafargo on 2007-10-02
Sorry schorsch, I failed to mention that it's 32bit.
C.

---

### Post by Cafargo on 2007-10-02
Hey schorsch, I started from scratch using your link (which I think was the same as mine). I discovered one important thing. My system has two volumes, and I copied to and was trying to execute the installation from my 2nd volume, where the OS and all the other goodies are NOT installed. There is way more space on my 2nd volume, hence the reason why I wanted to store xsi there. Well, when I decided to extract and execute the installation files from my 1st volume, I was able to launch the XSI installation process. Hoohoo! Except that I've now run into other more xsi related issues relating to stuff that cannot be registered. Drats! Well, at least I'm getting closer. Time to bother the XSI forums now ;-) 

Many many thanks for all your help. This is truly a wonderful forum. I mean it.

Best.
Caf.

---

### Post by schorsch on 2007-10-03
Glad to hear that it seems to work now for you! Could it be that the second volume you mentioned is formatted as a NTFS or FAT32 partition? This can cause some trouble sometimes ...

Nethertheless could you please mark this thread  as solved?

---

