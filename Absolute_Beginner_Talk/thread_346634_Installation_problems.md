---
title: "Installation problems"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Ranganaths on 2007-01-26
I am having problems with jdk6 installation.  

 I am following the instructions as follows:-

chmod +x {downloaded_file_name}.bin:- this works fine

fakeroot make-jpkg {downloaded_file_name}.bin:- this will give error as make-jpkg :command not found

 So i tried browsing and found other ways and followd other instructions:-

sudo apt-get install java-package:- this will give error as follows
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libssl0.9.6

couldnt try other these commands 
fakeroot make-jpkg <java-binary-package-name>.bin
dpkg -i <created-package-name>.deb

 please let me know how to install jdk6 and netbeans i have .bin files and  i am struggling to install the yahoo messenger dependency files 
sudo apt-get install libssl0.9.6 
even the about command gives  the error as follows
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libssl0.9.6


 please let me know how to go about this.. its getting frustrated..

Regards


 e

---

### Post by Circus-Killer on 2007-01-26
dont install via methods mentioned on the sun site.

instead follow the instructions of the java howto that is in  my signiture.

---

### Post by Ranganaths on 2007-01-26
I followed your procedures. still it gives the same problem... 

sudo apt-get install jdk-6-linux-i586.bin
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package jdk-6-linux-i586.bin

---

### Post by seshomaru samma on 2007-01-26
Are you sure you enabled the multiverse repositories?
can you post your /etc/apt/sources.list
```
gedit /etc/apt/sources.list
```

also
you should do this (in a terminal):
```
sudo apt-get update 
```
after enabling the multiverse repos.
then try to apt-get java

---

### Post by Ranganaths on 2007-01-26
this is that file and i tried to update with this line below. but i was not able to save it as its readonly.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse



deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper universe



## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse

---

### Post by konst88 on 2007-01-26
Uncomment all the lines starts with the word: deb, but not the last line which is not for your ubuntu.

---

### Post by Ranganaths on 2007-01-26
i am not able to edit this file as its readonly. I tried to change the mode and edit it but still i am not able to save it.

 /etc/apt/sources.list


please let me know how to go about it.

thank you
Regards

---

### Post by bigken on 2007-01-26
sudo gedit   /etc/apt/sources.list

---

### Post by Ranganaths on 2007-01-26
i have uncommented all the deb packages here - /etc/apt/sources.list

still its giving the same error
sudo apt-get install java-packages
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-packages


sudo apt-get build-dep java-package
I even tried the above command but it gives the same error...

i already have the .bin folder of jdk6.0  i tried to use sudo make-jpkg   filname.bin but its giving  error as make-jpkg: command not found. 
  so please help me out to sort it out. 
i am really sorry  troubling with my  ignorant questions.

Regards

---

### Post by bigken on 2007-01-26
you have to run sudo apt-get update 

sudo apt-get upgrade

---

### Post by Ranganaths on 2007-01-26
i have done it...

---

### Post by bigken on 2007-01-26
what have you done ?

---

### Post by Ranganaths on 2007-01-26
have removed the commented lines which starts from deb
/etc/apt/sources.list

and i have run this command as well
sudo apt-get update

---

### Post by bigken on 2007-01-26
why dont you install automatix this will do just about everything for you ;)

---

### Post by Ranganaths on 2007-01-26
how to install auto matrix and where to download?

---

### Post by helliewm on 2007-01-26
I googled automatix and then just downloaded it. It was very easy.

Helen

---

### Post by Ranganaths on 2007-01-26
i installed the automatrix. but it doesnt have java 6.0 it has only java 1.5. so my problemis not yet solved

---

### Post by bigken on 2007-01-26
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by bigken on 2007-01-26
since you you did the apt-get update/upgrades have you checked in synaptic for java6 ?

---

### Post by Ranganaths on 2007-01-26
I have checked that java 6 package in the synaptic manager still when i say this command it says unable to find source pacakage for java-package as follows

sudo apt-get build-dep java-package
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for java-package

---

### Post by Ranganaths on 2007-01-26
thank you all so much.. I finally installed the jdk.....!

---

