---
title: "something wrong with sources.list"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-09-18
Whenever I try and do just about ANYTHING in the terminal it tells me that it cant read line 24 in my sources list. And also when I try and run the update manager it says that I have some other software management tool running but I dont.

---

### Post by Poeffie on 2006-09-18
is there a terminal/process or synaptic busy? then there is another software magagement tool running (restarting helps in this case)

have you tried running whatever you want to do as a root user (permission to read)
```
sudo <command>
```
then enter your password

---

### Post by jd65pl on 2006-09-18
try rebooting, does the problem still occur after the reboot?

---

### Post by voodoonirvana on 2006-09-18
sam@sam-laptop:~$ sudo apt-get update
Password:
E: Type 'servers.' is not known on line 24 in source list /etc/apt/sources.list

Got the same thing...

---

### Post by rene86 on 2006-09-18
go to terminal:

```

sudo gedit /etc/apt/sources.list

```

And replace the file with:

```

## Ubuntu Software
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

```

After you should be able to run:

```

apt-get update

```

and then have fun with synaptics, if i did not underrate this problem

---

### Post by Poeffie on 2006-09-18
Try getting rid of line 24 in your sources.list, I think it's caused by something that's spelled wrong in the file:
```
sudo vi /etc/apt/sources.list
press down untill you get to line 24
if you see an obvious mistake, correct it
otherwise: press "i", put a # in front of the line and press ESC
exit with :wq
```

actually, could you post the text in the file here? Maybe we can correct the error without resetting it

---

### Post by voodoonirvana on 2006-09-18
Okay so I just restarted my system and the first thing I did was hit the update button and it gave me the same thing about having something else open. And sudo apt-get update is still not working, Im going to try what Poeffie said but I need to know something first. When it says line 24, is that counting the blank lines too? cause if it is then line 24 is:

## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports

Not counting the open lines it is:

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)

---

### Post by voodoonirvana on 2006-09-18
> **Poeffie said:**
> Try getting rid of line 24 in your sources.list, I think it's caused by something that's spelled wrong in the file:
```
sudo vi /etc/apt/sources.list
press down untill you get to line 24
if you see an obvious mistake, correct it
otherwise: press "i", put a # in front of the line and press ESC
exit with :wq
```

actually, could you post the text in the file here? Maybe we can correct the error without resetting it

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
## deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
## deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
## deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
 servers. RealPlayer10, Opera and more to come.) 
## deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
## deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main


## deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) breezy main



That is my sources.list

---

### Post by jd65pl on 2006-09-18
Comment out the line:

> "servers. RealPlayer10, Opera and more to come.)"

And uncomment those lines identifed by rene86

edit:
starting a line with "#" comments it out remove the "#" to uncomment a line

---

### Post by voodoonirvana on 2006-09-18
> **jd65pl said:**
> Comment out the line:



And uncomment those lines identifed by rene86

edit:
starting a line with "#" comments it out remove the "#" to uncomment a line


## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
## deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
## deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
## deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main


## deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) breezy main


Okay I have this now, did I uncomment that right?

---

### Post by jd65pl on 2006-09-18
You commented it out right but is that your whole sources list now?

It seems you have deleted some of the other sources if so,

---

### Post by Poeffie on 2006-09-18
This is what you should have:

```
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
## deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free
## deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers. RealPlayer10, Opera and more to come.)
## deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
## deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) breezy main
```

Actually, what rene86 said would do the same.

---

### Post by voodoonirvana on 2006-09-18
> **jd65pl said:**
> You commented it out right but is that your whole sources list now?

It seems you have deleted some of the other sources if so,

Ok, what Poeffie gave me worked, and it goes through the update process but when it gets done it says:

Fetched 4782kB in 28s (169kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by jd65pl on 2006-09-18
copy the list Poeffie   just posted and paste it in to you sources.list file.

Then run```
 sudo apt-get update
```

---

### Post by voodoonirvana on 2006-09-18
> **jd65pl said:**
> copy the list Poeffie   just posted and paste it in to you sources.list file.

Then run```
 sudo apt-get update
```

I did that and it went through the update process and then said this:

Fetched 4782kB in 28s (169kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by jd65pl on 2006-09-18
So you understand more about sources for your own learning curve benefit you may find this useful.
[URL="https://help.ubuntu.com/community/SourcesList"]
https://help.ubuntu.com/community/SourcesList[/URL]

To add repositories via a gui:[URL="https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto"]
https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto[/URL]

---

### Post by voodoonirvana on 2006-09-18
> **jd65pl said:**
> So you understand more about sources for your own learning curve benefit you may find this useful.
[URL="https://help.ubuntu.com/community/SourcesList"]
https://help.ubuntu.com/community/SourcesList[/URL]

To add repositories via a gui:[URL="https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto"]
https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto[/URL]


Yeah, I knew about that. But not my problem is this:

Fetched 4782kB in 28s (169kB/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


It gives me that when I do sudo apt-get update.

---

### Post by jd65pl on 2006-09-18
Reboot and then run

```
sudo apt-get update
```

Do you still get the error?

---

