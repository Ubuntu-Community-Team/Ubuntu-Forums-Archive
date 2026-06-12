---
title: "i messed up /etc/apt/confings.list !! can anyone help pls"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by ishwar on 2007-10-06
hi there..
i recently tried to install desktop lastfm version!!! for that i saw a post suggesting me to add a line in 
/etc/apt/configs.list  which i tried doing thru gedit.. i did back up my configs.list but .. i really dont know how to use gedit!!! the fun started after that... 


now when i give a command in the konsolw 

laptop:~$ sudo gedit /etc/apt/configs.list
****@****-laptop:~$ sudo gedit /etc/apt/configs.list.save


gedit opens the file but there seems to be nothing showing in that!!! when i tried to open thru GUI i was denied accesss or permission.. 

it seems to be logged in as a sudo all the time.. when i try open any of my system applications its no longer asking me for any password!!!! which sounds very controvertial.. by the way i m using ubuntu 6.06 i guess!!! 

and my update manager is always up with a error msg!! which is

software updates correct errors, eliminate security vulnerabilities and provide new features... 

i m deeeply worried!!

thanx in advance
regards

---

### Post by taurus on 2007-10-06
> **ishwar said:**
> 

laptop:~$ sudo gedit /etc/apt/configs.list
****@****-laptop:~$ sudo gedit /etc/apt/configs.list.save



Here is your problem.  If you want to make a backup copy of it before you edit it, you should have run

```
sudo cp /etc/apt/configs.list /etc/apt/configs.list.save
gksudo gedit /etc/apt/configs.list
```

---

### Post by FuturePilot on 2007-10-06
I don't think there is a problem here. 
> software updates correct errors, eliminate security vulnerabilities and provide new features...

That is normal. It is not an error message.
Second, there is no file /etc/apt/configs.list
At least I don't have one. I think what you are looking for is /etc/apt/sources.list.
When you enter your password it is kept in the keyring for 15 min which is why you are not prompted to enter it again.

---

### Post by ishwar on 2007-10-06
hi i no longer want to install the last fm.. i guess the source was not working for some reason.. so i do not want to edit my apt configs


yes i did back up the file... could you pls tell me what should i do to get the back up file to work for my updatemanager.. it seems to glow all the time!! 

and when tried opening the file with the command u suggested.. i got a output as bellow!
sudo cp /etc/apt/configs.list /etc/apt/configs.list.save
Password:
cp: cannot stat `/etc/apt/configs.list': No such file or directory
eswar@eswar-laptop:~$ gksudo gedit /etc/apt/conifgs.list

(gedit:9299): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
thanx for the reply!!
pls hlp me resolve or get back my original config file..

---

### Post by ishwar on 2007-10-06
yup sorrrrrrrrrrry


that was meant to be sources.list!!!!!!!!!!!!!!!!!!!!!!!

thanx for the corrrection...
and this is the output thru gedit!!



## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted

---

### Post by ishwar on 2007-10-06
but the problems is still existing i.e the update manager is glowing all the time.. will post u the exact details.. let me reboot the systme and get it up !!

thanx  guys

---

### Post by ishwar on 2007-10-06
i rebooted my system and the update manager comes up with a software update but when try to install the updates there no updates available. 

when i put my cursor over the icon i see this error msg!!

a error occured, please run package manager from the right-click menu or apt-get on a terminal to see what is wrong. the error msg was: 'Error': opening the cache (E:Opening /etc/apt/source.list - ifstream ::ifstream (13 permission denied), E:;The list of sources could be read.)'

i tried to do sudo apt-get update 
the out put as follow but idont see any problem with that.. i m assuming i have changed file permission in the process of editing the file pls help me .. i once tried (few hrs ago) chmod 735 or 700 for the sources.list file.. was that wrong.. if so what shld i do now!!

---

### Post by ishwar on 2007-10-07
thank u guys.....

---

### Post by Mike Krall on 2007-12-08
If you don't mind... how did you solve the problem?

Mike

---

