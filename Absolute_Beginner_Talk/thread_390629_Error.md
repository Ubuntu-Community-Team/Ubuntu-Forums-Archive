---
title: "Error"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-22
This error shows up when I either try to update my system or when I try to open synaptic

E: The package mercury-messenger needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by adam s on 2007-03-22
> **julie_lebou said:**
> This error shows up when I either try to update my system or when I try to open synaptic

E: The package mercury-messenger needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

Try running the following command in a terminal.

sudo apt-get -y update && sudo apt-get -y dist-upgrade

The command does the same as when you do updates through the update manager.

Do you still get the errors?
Has it fixed the problem.

Adam.

---

### Post by julie_lebou on 2007-03-22
julie@julie:~$ sudo apt-get -y update && sudo apt-get -y dist-upgrade
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Translation-en_CA                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Translation-en_CA             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Translation-en_CA             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Translation-en_CA               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_CA            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_CA
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_CA      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_CA        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Translation-en_CA     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Translation-en_CA     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy Release  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates Release                          
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_CA                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Packages                            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Packages                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Packages                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/main Sources                             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/restricted Sources                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/multiverse Sources                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy/universe Sources                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/main Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/restricted Sources     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/multiverse Sources     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) edgy-updates/universe Sources       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_CA                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_CA
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release             
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages       
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages       
  503 Service Temporarily Unavailable
Err [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages       
  503 Service Temporarily Unavailable
Get:4 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages [5125B]                   
99% [Waiting for headers]                                                      
Get:5 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages [5125B]
Fetched 10.3kB in 1m30s (114B/s)
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz) 503 Service Temporarily Unavailable
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/edgy/main/binary-i386/Packages.gz) 503 Service Temporarily Unavailable
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
julie@julie:~$ 
julie@julie:~$

---

### Post by taurus on 2007-03-22
You need to edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of a line for automatix since the site is still down.  Save it and run those two commands again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by sad_iq on 2007-03-22
You must have another instance of apt-get, aptitude, or automatix running...stop them (reboot if necesary)and try what **adam s** sugested!!!

---

### Post by julie_lebou on 2007-03-22
julie@julie:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  file libmagic1 libmysqlclient15off mysql-common 
4 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate a file for the mercury-messenger package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
julie@julie:~$

---

### Post by julie_lebou on 2007-03-22
How can I unistall mercury?

---

### Post by taurus on 2007-03-22
```
sudo aptitude --purge remove mercury-messenger
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by julie_lebou on 2007-03-22
julie@julie:~$ sudo aptitude --purge remove mercury-messenger
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libmysqlclient15off mysql-common 
The following packages have been kept back:
  file libmagic1 
The following packages will be REMOVED:
  mercury-messenger 
0 packages upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dpkg: error processing mercury-messenger (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted (core dumped)
julie@julie:~$ Errors were encountered while processing:
 mercury-messenger

---

### Post by Bachstelze on 2007-03-22
It suggests you reinstall it before removing it, have you tried that ?

---

### Post by julie_lebou on 2007-03-22
:S I had help to install it yesterday... can't remember what I did. I'm not good with installation with Ubuntu

---

### Post by julie_lebou on 2007-03-22
julie@julie:~$ /usr/share/mercury/startup/startup_linux.sh09:59:55:440 Mercury/1.8 [20060811] starting...
09:59:58:363 [5%] Welcome julie...
09:59:58:368 [10%] Starting Mercury 1.8...
09:59:58:368 [12%]   Verifying classpath...
09:59:58:369 [14%]   Verifying library path...
09:59:58:369 [16%] 
09:59:58:369 [18%]   Checking for update file...
09:59:58:370 [20%]   Loading tray icon...
09:59:58:624 [22%] Starting initializations
09:59:58:656 [24%]   18 initializations remaining
09:59:58:768 [26%]   17 initializations remaining
09:59:58:852 [28%]   16 initializations remaining
09:59:58:859 [30%]   15 initializations remaining
09:59:58:945 [32%]   14 initializations remaining
09:59:58:951 [34%]   13 initializations remaining
09:59:59:156 [36%]   12 initializations remaining
09:59:59:157 [38%]   11 initializations remaining
09:59:59:175 [40%]   10 initializations remaining
09:59:59:236 [42%]   9 initializations remaining
09:59:59:303 [44%]   8 initializations remaining
09:59:59:373 [46%]   7 initializations remaining
09:59:59:408 [48%]   6 initializations remaining
09:59:59:656 [50%]   5 initializations remaining
09:59:59:876 [52%]   4 initializations remaining
10:00:00:043 [54%]   3 initializations remaining
10:00:00:262 [56%]   2 initializations remaining
10:00:00:275 [58%]   1 initializations remaining
10:00:01:221 [62%]   -1.8...
10:00:03:601 [64%]   0 initializations remaining
10:00:03:603 [74%]   Initializations done
10:00:03:719 [78%] Starting plugins...
10:00:03:719 [82%] Loading Startup Tabs...
10:00:03:719 [100%] Done.
10:00:03:720 [100%] init completed in 8542 ms










did i reinstalled it?

---

### Post by julie_lebou on 2007-03-22
help me please! :-(

---

### Post by Arby on 2007-03-22
The last set of messages you posted are from trying to start the program. Did it start as you expect? If you still need to reinstall then use ```
sudo aptitude reinstall mercury-messenger
``` If that still produces errors then try ```
sudo aptitude -f reinstall mercury-messenger
``` If you still have errors show us what they are. If either of those commands completes without error then try removing the package with ```
sudo aptitude remove mercury-messenger
```

Also if you're having trouble understanding the installation process then it's probably worth reading these pages if you haven't already [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by julie_lebou on 2007-03-23
Hey! Thanks for the help, but I ended up reinstalling Ubuntu cause I didnt know how to fix this! Thanks anyways! :-)

---

### Post by tripolitan on 2007-05-26
that is not good. I'm running into the exact same problem and cannot fix it, just after I got my system fully in tune.

---

### Post by ramjet_1953 on 2007-05-27
If all else fails, do this:

1. Backup your[COLOR="Blue"] /var/lib/dpkg/status [/COLOR]file 

2. After you have backed it up, type this command into a termial: [COLOR="Red"]gksu gedit /var/lib/dpkg/status[/COLOR]

3. When the file opens in the editor, search the list for reference to the mercury-messenger package.

4. CAREFULLY delete the reference.

5. Save the file

6. Re-boot and Synaptic should be happy again, as it now doesn't know about the rogue package.

The package isn't deleted, but over time, it will be over-written.

Regards,
Roger :cool:

---

