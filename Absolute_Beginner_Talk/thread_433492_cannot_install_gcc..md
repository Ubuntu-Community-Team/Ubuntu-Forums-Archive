---
title: "cannot install gcc."
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by alfahat on 2007-05-05
hi all .im using ububtu 6.06 i tried to install dsniff . but got this result

loading cache ./config.cache
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.
.

**then i realized that u need to upgrade my gcc4.0 to gcc 4.1**

then tried this @the terminal 

** sudo apt-get install gcc build-essential**

Reading package lists... Done
Building dependency tree... Done
gcc is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:4.1.1) but 4:4.0.3-1 is to be installed
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages.

**how can i install gcc 4.1.?**

---

### Post by DSn0wMan on 2007-05-05
gcc 4:4.1.2 is in the fiesty repository. It is possible you could get it from the backports repository.

Try adding this repo.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

---

### Post by adameye on 2007-05-05
I have same problem, I'm getting annoyed by Ubuntu 7.04
I couldn't understand why not have the complete c libraies in the original CD
I searched online for a lot of time, and still can not figure it

---

### Post by adameye on 2007-05-05
I just downloaded Ubuntu 7.04 and installed it today
however, I can not use gcc,cc,g++ to compile the C program which can run in Ubuntu 6.04


 sudo apt-get install build-essential
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
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages


sudo apt-get install libc6-dev
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
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.4-1ubuntu12.3) but 2.5-0ubuntu14 is to be installed
E: Broken packages

---

### Post by Sef on 2007-05-05
>  sudo apt-get install gcc build-essential

The correct way to install build-essential is this way:

```
sudo apt-get update
```

```
sudo apt-get install build-essential
```

---

### Post by adameye on 2007-05-06
thanks for you reply, however I still have problem:

sudo apt-get install gcc build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages


sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                   
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]         
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 5B in 0s (7B/s)  
Reading package lists... Done



sudo apt-get install build-essential
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
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

---

### Post by taurus on 2007-05-06
```
sudo aptitude update
sudo aptitude install build-essential
```
Don't include gcc in there since build-essential package will take care of the gcc stuff for you.

---

### Post by adameye on 2007-05-06
sudo aptitude update
 sudo aptitude update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [191B]            
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                   
.....
...
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Fetched 5B in 3s (1B/s)  
Reading package lists... Done


 sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  g++-4.1 libc6-dev libstdc++6-4.1-dev 
The following NEW packages will be automatically installed:
  dpkg-dev g++ linux-libc-dev 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ linux-libc-dev 
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7932kB of archives. After unpacking 30.4MB will be used.
The following packages have unmet dependencies:
  g++-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed.
           Depends: gcc-4.1 (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed.
  libstdc++6-4.1-dev: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed.
  libc6-dev: Depends: libc6 (= 2.4-1ubuntu12.3) but 2.5-0ubuntu14 is installed.
Resolving dependencies...
open: 9; closed: 5; defer: 0; conflict/break: 1                                .The following actions will resolve these dependencies:

Keep the following packages at their current version:
build-essential [Not Installed]
g++ [Not Installed]
g++-4.1 [Not Installed]
libc6-dev [Not Installed]
libstdc++6-4.1-dev [Not Installed]

Score is -9965

Accept this solution? [Y/n/q/?]

---

### Post by taurus on 2007-05-06
> **adameye said:**
> sudo aptitude update
 sudo aptitude update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) [COLOR="Red"]edgy[/COLOR] Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) [COLOR="Red"]edgy-updates[/COLOR] Release.gpg [191B]              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) [COLOR="Red"]edgy-backports[/COLOR] Release.gpg [191B]            
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) [COLOR="Red"]dapper-backports[/COLOR] Release.gpg [191B]             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) [COLOR="Red"]edgy[/COLOR] Release                                   
.....
...
Hit [http://security.ubuntu.com](http://security.ubuntu.com) [COLOR="Red"]edgy-security[/COLOR]/universe Sources
Fetched 5B in 3s (1B/s)  
Reading package lists... Done

Hold a second.  You have both Dapper and Edgy repos in your /etc/apt/sources.list!  You are asking for trouble if you mix the two releases in there.  If you are running Edgy, your /etc/apt/sources.list should contain only repos from Edgy.  And if you are running Dapper, remove all the repos that have edgy in there.

Can you post your /etc/apt/sources.list here?

```
cat /etc/apt/sources.list
```

---

### Post by adameye on 2007-05-06
cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by taurus on 2007-05-06
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove this line from it.

```
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```
And while you are in there, remove the **us.** from your repos also.  Save the changes.  Then, run

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by adameye on 2007-05-06
sudo aptitude update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]                 
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release [34.7kB]                           
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release [38.4kB]                   
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release [44.6kB]                 
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages [940kB]                      
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages [5974B]                
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources [274kB]                      
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources [1436B]                
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages [3559kB]                
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources [1068kB]                 
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages [81.1kB]            
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages [14B]         
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources [24.2kB]             
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources [14B]          
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages [17.8kB]          
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages [14B]       
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages [40.1kB]      
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages [6087B]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources [5571B]            
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources [14B]        
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources [14.4kB]       
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources [2382B]      
Fetched 6158kB in 2m3s (49.8kB/s)                                               
Reading package lists... Done

sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  g++-4.1 libc6-dev libstdc++6-4.1-dev 
The following NEW packages will be automatically installed:
  dpkg-dev g++ linux-libc-dev 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ linux-libc-dev 
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 7932kB of archives. After unpacking 30.4MB will be used.
The following packages have unmet dependencies:
  g++-4.1: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed.
           Depends: gcc-4.1 (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed.
  libstdc++6-4.1-dev: Depends: gcc-4.1-base (= 4.1.1-13ubuntu5) but 4.1.2-0ubuntu4 is installed.
  libc6-dev: Depends: libc6 (= 2.4-1ubuntu12.3) but 2.5-0ubuntu14 is installed.
Resolving dependencies...
open: 9; closed: 5; defer: 0; conflict/break: 1                                .The following actions will resolve these dependencies:

Keep the following packages at their current version:
build-essential [Not Installed]
g++ [Not Installed]
g++-4.1 [Not Installed]
libc6-dev [Not Installed]
libstdc++6-4.1-dev [Not Installed]

Score is -9965

Accept this solution? [Y/n/q/?] 


I will use no to continue, hope it will work

---

### Post by adameye on 2007-05-06
I searched online and someone think it might be useful to remove build-essential first..
so I try:

 apt-get remove build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not installed, so not removed
The following packages were automatically installed and are no longer required:
  sysvinit
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = "zh_CN.gbk",
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up gtk-gnutella (0.96.3-0ubuntu1~edgy1) ...

---

### Post by adameye on 2007-05-07
I fixed the problem, I used a wrong source.list, 7.07 should never have "edgy..lsourcr list"
thanks

---

