---
title: "VMWare on Ubuntu 6.09 LTS installation problem"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by powergrip on 2006-09-15
I went to 2 places to see if I can get a guide on installing VMware on my system. 

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)
and
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)

in both there is a step that I can't get to work. 

_______________________________________________________________________
From [http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware)
-----------------------------------
Execute the installation script.
Code:
sudo ./vmware-install.pl
-----------------------------------
______________________________________________________________________
From [http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)
-----------------------------------
Running the installer script:

cd vmware-server-distrib
./vmware-install.pl
-----------------------------------
_______________________________________________________________________

When I type in "sudo ./vmware-install.pl" I get this...

rene@Linux-Box:~/vmware-server-distrib$ sudo ./vmware-install.pl
Password:
sudo: ./vmware-install.pl: command not found
rene@Linux-Box:~/vmware-server-distrib$

[B]
What am I doing wrong? [/B]:confused: ](*,) :sad:

---

### Post by davmac on 2006-09-15
I followed the first of these guides myself a couple of weeks ago and didn't have any problem.

Did the previous step (tar xvzf...) work OK?

It should have created a directory that starts "vmware..."

Change into this directory and list the contents (type "ls -la"). Can you see the vmware-install.pl file?

Dave Mac

---

