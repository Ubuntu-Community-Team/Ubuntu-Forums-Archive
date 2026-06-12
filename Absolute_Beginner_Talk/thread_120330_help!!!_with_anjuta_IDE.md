---
title: "help!!! with anjuta IDE"
date: 2006-01-21
forum: Absolute Beginner Talk
---

### Post by v1ckey on 2006-01-21
hello everyone,
im a complete linux newbie.So Please help me out.

!I do not have an internet connection..!
so i guess sdo apt-get wont work.

I need to know which version of anjuta works on ubuntu and how to install it cause i just switched from red hat to ubuntu for the better GUI.I have earlier versions like anjuta 1.2.4 and others which worked fine on redhat but while installling same on ubuntu there is an error 

!!!Perl dependencies!!!.

Can anyone please suggest the installation method and version .
Also can anyone tell where to find list of shell commands and uses  i have to have those.

Thanks in advance.

---

### Post by Adrian on 2006-01-21
[QUOTE=v1ckey]hello everyone,
im a complete linux newbie.So Please help me out.
I need to know which version of anjuta works on ubuntu and how to install it cause i just switched from red hat to ubuntu for the better GUI.I have earlier versions like anjuta 1.2.4 and others which worked fine on redhat but while installling same on ubuntu there is an error 

!!!Perl dependencies!!!.

Can anyone please suggest the installation method and version .
Also can anyone tell where to find list of shell commands and uses  i have to have those.

Thanks in advance.[/QUOTE]

Enable the universe repository and install it from Synaptic. This will install version 1.2.4-1 if you're using Breezy. I've done it many times and I've never had any problems.

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by v1ckey on 2006-01-21
[QUOTE=Adrian]Enable the universe repository and install it from Synaptic. This will install version 1.2.4-1 if you're using Breezy. I've done it many times and I've never had any problems.

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)[/QUOTE]


I am very very thankful for your reply.
But i still do not understand that if the package is on the harddrive
then how come 
sudo apt update 
or
sudo apt-get install would work after adding extra repositories.
I think repositories are sites from where contents are downloaded .
Please be free to correct me .
I dont have an internet on my desktop.
  
Thanks a lot

---

### Post by Adrian on 2006-01-21
[QUOTE=v1ckey]I am very very thankful for your reply.
But i still do not understand that if the package is on the harddrive
then how come 
sudo apt update 
or
sudo apt-get install would work after adding extra repositories.
I think repositories are sites from where contents are downloaded .
Please be free to correct me .
I dont have an internet on my desktop.
  
Thanks a lot[/QUOTE]

What method are you using when you try to install the package? **dpkg -i**?

When you do an **apt-get** from a repository, it will also download and install all other packages that are needed. It seems like they are not installed on your harddrive.

---

### Post by v1ckey on 2006-01-21
[QUOTE=Adrian]What method are you using when you try to install the package? **dpkg -i**?

When you do an **apt-get** from a repository, it will also download and install all other packages that are needed. It seems like they are not installed on your harddrive.[/QUOTE]


i Downloaded the anjuta package from a college server .I tried extracting and then

./configure
make 
make install
through root user
i only have a single anjuta tar.bz2 file.
Do i need to have anything more.
Thanks

---

### Post by Adrian on 2006-01-21
[QUOTE=v1ckey]i Downloaded the anjuta package from a college server .I tried extracting and then

./configure
make 
make install
through root user
i only have a single anjuta tar.bz2 file.
Do i need to have anything more.
Thanks[/QUOTE]

To compile it yourself, you need to have all dependencies installed already. In this case, it needs some Perl libraries, and those are not installed by default. I just checked the Anjuta dependencies, and there are a lot of them.
If you can connect your computer to the Internet somehow and do an **apt-get install anjuta**, you will save a lot of time.

---

### Post by ysse on 2006-01-21
Hi,

Maybe a good way to begin is by installing the 1.2.4-1 Anjuta that exists as a package in the Ubuntu repositories. Then all dependent packages will be downloaded and installed for you.

System - Administration - Synaptic Package Manager and mark Anjuta for installation. Or, from a terminal: sudo apt-get install anjuta. 

If you really, really need the latest anjuta version, then you could uninstall anjuta from Synaptic, and then do your manual build with ./configure, make etc. Hopefully that newer version will be able to run with the same dependent packages as 1.2.4-1.

Cheers
/Anders

---

