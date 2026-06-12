---
title: "Problems accessing US.ARCHIVE.UB.COM"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Sushubh on 2007-05-28
[IMG]http://i17.tinypic.com/6h6h092.png[/IMG]

Looks like my ISP (Airtel Broadband) is facing issues with the US Ubuntu server. Is there any solution to this problem? Maybe I can access some mirror to install applications through Synaptics?

---

### Post by taurus on 2007-05-28
Edit /etc/apt/sources.list

```
kdesu kate /etc/apt/sources.list
```
and remove the **us.** from all your repos.  Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Sushubh on 2007-05-28
seems to have worked. but sudo gets stuck at: archive.ubuntu.com

looks like this service is not accessible from my isp either! :(

---

### Post by taurus on 2007-05-28
Can you post the whole message that you got from a terminal?  Any chance you are behind a firewall or proxy?

---

### Post by Sushubh on 2007-05-28
umm... pings are not working on either servers.

nope no firewall or proxy. just plain net connected to this ubuntu box. i can access the rest of the internet fine.

here are screens. 
[IMG]http://i8.tinypic.com/61x7cwh.png[/IMG]
[IMG]http://i11.tinypic.com/6exxsoy.png[/IMG]

---

### Post by taurus on 2007-05-28
Here is what I get.

```
ping -c 3 **archive.ubuntu.com**
PING archive.ubuntu.com (91.189.89.8) 56(84) bytes of data.
64 bytes from prat.canonical.com (91.189.89.8): icmp_seq=0 ttl=45 time=111 ms
64 bytes from prat.canonical.com (91.189.89.8): icmp_seq=1 ttl=45 time=111 ms
64 bytes from prat.canonical.com (91.189.89.8): icmp_seq=2 ttl=45 time=110 ms

--- archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 110.811/110.989/111.126/0.406 ms, pipe 2
```

---

### Post by Sushubh on 2007-05-28
exactly. my ISP is having issues with us. and archive. paths.

i tried pinging uk.archive.ubuntu.com.

it seems to be working and pointing towards:
ubuntu.datahop.it

should i replace all the archive.ub paths with uk.archive?

---

### Post by taurus on 2007-05-28
You can put the uk. in front of the lines that you removed us. earlier in /etc/apt/sources.list.

---

### Post by Sushubh on 2007-05-28
cool... can anyone give me the original file for backup? i did not take one :(

on running upgrade and update commands i get the following error:

> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


---

### Post by Sushubh on 2007-05-28
duh. looks like i replaced all instances of archive with uk.archive. some of the paths are broken. got this error:

> Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty/main Packages    
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty/restricted Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty/main Sources
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty/restricted Sources
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty/universe Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty/universe Sources 
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty/multiverse Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty/multiverse Sources
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-updates/main Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-updates/restricted Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-updates/main Sources
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-updates/restricted Sources
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-updates/universe Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-updates/multiverse Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-backports/main Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-backports/restricted Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-backports/universe Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-backports/multiverse Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-security/main Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-security/restricted Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-security/universe Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-security/multiverse Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-proposed/restricted Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-proposed/main Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-proposed/multiverse Packages
  400 Bad request
Err [http://uk.archive.ubuntu.comubuntu](http://uk.archive.ubuntu.comubuntu) feisty-proposed/universe Packages
  302 Found


would need the original file please! :P

---

### Post by taurus on 2007-05-28
```
deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu feisty universe
deb-src http://archive.ubuntu.com/ubuntu feisty universe

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

deb http://archive.ubuntu.com/ubuntu feisty multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty multiverse

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu feisty-commercial main 
```

p.s.  Just so you now, the repos should be
```
http://uk.archive.ubuntu.com**[COLOR="Blue"]/[/COLOR]**ubuntu
```

---

### Post by Sushubh on 2007-05-28
ok so i am supposed to replace us.archive.ubuntu.com with uk.archive.ubuntu.com/ubuntu...

what do i replace archive.ubuntu.com with coz that path is still not working for me!

---

### Post by taurus on 2007-05-28
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Sushubh on 2007-05-28
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main


i replaced my file with the content of your post.

ouchie. looks like i also ended up removing the files automatix threw in!

---

### Post by taurus on 2007-05-28
What happens when you run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Sushubh on 2007-05-28
it get stuck at the part when it tries to access archive.ubuntu.com!

> sushubh@ubuntu:~$ sudo aptitude update
0% [Working]
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]                                                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US                           
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]                         
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources           
99% [Connecting to archive.ubuntu.com (91.189.89.8)]         

the basic problem is that i cannot seem to connect to 91.189.xxx.xxx ip series. pings wont work on the two domains.

---

### Post by TheFlamingBush on 2007-05-28
same here

hangs on:

99% [Connecting to archive.ubuntu.com (91.189.89.8)]



**get this read out in terminal.**

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.31), connection timed out
99% [Connecting to archive.ubuntu.com (91.189.89.8)]


**I tried the above and got this read out:**

## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

# Dapper Security Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

# Dapper Bugfix Updates
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3

**In the terminal i get:**

~$ gksudo gedit /etc/apt/sources.list

(gedit:31078): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by Sushubh on 2007-05-29
> sushubh@ubuntu:~$ sudo apt-get install putty
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package putty
sushubh@ubuntu:~$ 


this is what happens when i try to install something.

---

### Post by yabbadabbadont on 2007-05-29
Just as a test (a safe one), edit your /etc/apt/sources.list file and add a '#' (without the tick marks) to the front of every line that starts with 'deb' or 'deb-src'.  Save your changes.  Run (without the quotes) "sudo apt-get update".  If there are no errors, edit the file and remove the '#' that you added to the lines starting with 'deb' and 'deb-src'.  Now run "sudo apt-get update" again.  Does it complete now?

---

### Post by Sushubh on 2007-06-04
i crashed my wubi ubuntu and reinstalled.

i am using [japanese servers]("http://ftp.ecc.u-tokyo.ac.jp") now. it works most of the times but i still am not able to access archive.ubuntu.com. looks like a japanese server mirror is not available for this domain?

---

