---
title: "vmware install"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by evkefalas on 2007-02-20
Hi, I tried to follow the instructions here:

[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

to install vmware because i am really interested in running work related windows  apps through linux,

i follow the instructions and after i run the install
i get
evan@evan-laptop:~/Desktop/tmp/vmware-server-distrib$ vmware
bash: vmware: command not found
evan@evan-laptop:~/Desktop/tmp/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

evan@evan-laptop:~/Desktop/tmp/vmware-server-distrib$

i ve tried to install nmplayer before from the synaptic pakg manager
but didnt use it and removed it normally
so it thinks i have a previous vmware installation there
any ideas how to solve this? can i remove anything left from previous installation?
from synaptic pakg manager i ve removed everythin vmware installed previously
but still nothing

Many Thanks

---

### Post by zvacet on 2007-02-21
Chek usr/bin.maybe there is still vmplayer uninstall file.See etc,etc/init.d,tmp,home.Something is left and now you can do another install.Maybe the best way is to uninstall all vmware files and folders you have and do the frash install.It is not that hard like it sounds.

---

### Post by evkefalas on 2007-02-21
Thanks for the answer :)
how you do the frash install
sorry i am a beginner
tnx

---

### Post by evkefalas on 2007-02-21
found a folder vmware in etc with a config file
i try to delete it but i get 

Access denied to /home/evan/.local/share/Trash/files/vmware_1.

---

### Post by evkefalas on 2007-02-21
allso vm-ware-player file in /etc/init.d but i can delete that to
how can i delete those files?
tnx

---

### Post by xpod on 2007-02-21
If you want an easy simple way of setting up a vitual XP for your windows apps then i suggest you have a look at Virtualbox...

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Just click on your distro specific link to download and off you go.
Once it`s installed setting up the VM`s themselves are as easy as 123

Theres a few threads if you do a search that cover most of the basic problems people run into but it`s really simple stuff ....even for me:mrgreen: 
Although mabey you would be better getting to know your Ubuntu a bit better first if your just starting out:) 

Good luck either way

---

### Post by evkefalas on 2007-02-21
thanx for the reply, 
tried to intsall it and get:

dpkg -i '///home/evan/Desktop/VirtualBox_1.3.6_Ubuntu_edgy_i386.deb' ;echo RESULT=$?
(Reading database ... 162197 files and directories currently installed.)
Preparing to replace virtualbox 1.3.6_Ubuntu_edgy (using .../VirtualBox_1.3.6_Ubuntu_edgy_i386.deb) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
virtualbox-puel-1-1 license has already been accepted
Unpacking replacement virtualbox ...
dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on libxalan110; however:
  Package libxalan110 is not installed.
 virtualbox depends on libxerces27; however:
  Package libxerces27 is not installed.
dpkg: error processing virtualbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox
RESULT=1

any ideas?
tnx

---

### Post by evkefalas on 2007-02-21
dpkg -i '///home/evan/Desktop/VirtualBox_1.3.6_Ubuntu_edgy_i386.deb' ;echo RESULT=$?
(Reading database ... 162197 files and directories currently installed.)
Preparing to replace virtualbox 1.3.6_Ubuntu_edgy (using .../VirtualBox_1.3.6_Ubuntu_edgy_i386.deb) ...
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
virtualbox-puel-1-1 license has already been accepted
Unpacking replacement virtualbox ...
dpkg: dependency problems prevent configuration of virtualbox:
 virtualbox depends on libxalan110; however:
  Package libxalan110 is not installed.
 virtualbox depends on libxerces27; however:
  Package libxerces27 is not installed.
dpkg: error processing virtualbox (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox
RESULT=1

---

### Post by xpod on 2007-02-21
I`m sorry you`ve had probs here too.It looks like it`s telling you the same thing that is mentioned just below the download links on the actual Vistallbox site

>     You will need to install some additional libraries on your Linux system in order to run VirtualBox - in particular, you will need libxalan-c, libxerces-c and version 5 of libstdc++. How to install these will depend on the Linux distribution you are using.

See the changelog for what has changed. Older versions of VirtualBox can be found on this separate page. 

I never had this prob with edgy myself though and the edgy link completed the enitire install for me without complaining about the dependancies as yours seems to be.

I did have to use the older version of VB on a recent fresh insall of edgy last week as the new one would not install due to some libc-dev dependancy that i had alreAdy installed(????)

Resorting to the earlier version installed flawlessly though as it had always had done previously.

EDIT:as i first mentioned mabey getting to know the basics of Ubuntu might be a better idea than worrying about XP apps....dualbooting is mabey the beSt way to start out for that stuff

---

### Post by HereInOz on 2007-02-21
In the original instructions, you will find, down the bottom, the following:

    * Uninstallation failed and reinstall won't work
      ====
      A previous installation of VMware software has been detected.
      The previous installation was made by the tar installer (version 3).
      Keeping the tar3 installer database format.
      Error: Unable to execute "/usr/bin/vmware/vmware-uninstall.pl.
      Failure
      Execution aborted.
      ====

        Look for the /etc/vmware directory and either move it to a different location or remove it altogether.
        Code:

        sudo rm -R /etc/vmware

Did you try this at all?  I had a similar problem and this sorted it out, and allowed me to re-run the vmware install successfully.

---

### Post by evkefalas on 2007-02-21
i tried  sudo rm and now i am intalling it
at the moment normally,
many thanks for yr help
:)

---

### Post by evkefalas on 2007-02-21
the only thing missing now, is the serial for VMWare Server
 i tried to register on the vmware site but my registration is partial and doesnt get all the way
does anyone have any serial plz?
tnx

---

### Post by evkefalas on 2007-02-21
Got it installation success
tnx

---

