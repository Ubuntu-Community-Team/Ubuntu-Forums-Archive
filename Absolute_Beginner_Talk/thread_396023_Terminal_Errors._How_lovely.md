---
title: "Terminal Errors. How lovely"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-28
I get this error in my terminial:
```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  apache2: Depends: apache2-mpm-worker (>= 2.2.3-3.2build1) but it is not going to be installed or
                    apache2-mpm-prefork (>= 2.2.3-3.2build1) but 2.0.55-4ubuntu4 is to be installed or
                    apache2-mpm-event (>= 2.2.3-3.2build1) but it is not going to be installed
  libapache2-mod-php5: Depends: apache2.2-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

What I have done and how do I fix it.

Edit>
When I do what it says it comes back with the same error btw.

---

### Post by nixclusive on 2007-03-28
by the way```
apt-get -f install
```attempts to fix broken dependencies on your system, which may require addition/removal of packages. From the looks of it, are you trying to install apache2 server with mod-php5 on your system? try: ```
apt-get install apache2 apache2-mpm-prefork libapache2-mod-php5
```

---

### Post by ceeg on 2007-03-28
Remove every unmet dependency:
```

sudo apt-get -f remove apache2-mpm-worker apache2-mpm-prefork apache2-mpm-event libapache2-mod-php5 apache2.2-common

```

Update apt:
```
sudo apt-get update
```

Try reinstalling the application again:
```
sudo apt-get install poopie
```

---

### Post by astoltz on 2007-03-28
apache2 is trying to install a dependency with a version that is different than what is in the repositories. For instance, it's trying to install 2.2.3-3.2build1 of the  apache2-mpm-worker package but the repos have 2.0.55-4ubuntu4.

What repo are you using to install apache2?

---

### Post by aysiu on 2007-03-28
Your repositories list is messed up.

[Get a fresh list](http://www.psychocats.net/ubuntu/sources) and start again: ```
sudo aptitude update
sudo aptitude install apache2
```

---

### Post by ProjectWhat on 2007-03-29
> **nixclusive said:**
> by the way```
apt-get -f install
```attempts to fix broken dependencies on your system, which may require addition/removal of packages. From the looks of it, are you trying to install apache2 server with mod-php5 on your system? try: ```
apt-get install apache2 apache2-mpm-prefork libapache2-mod-php5
```
Sorry but I get this error:
```
ben@ben-ubuntu:~$ apt-get install apache2 apache2-mpm-prefork libapache2-mod-php5
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ben@ben-ubuntu:~$ sudo apt-get install apache2 apache2-mpm-prefork libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2-mpm-prefork is already the newest version.
libapache2-mod-php5 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: apache2.2-common but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ben@ben-ubuntu:~$ 

```

> **ceeg said:**
> Remove every unmet dependency:
```

sudo apt-get -f remove apache2-mpm-worker apache2-mpm-prefork apache2-mpm-event libapache2-mod-php5 apache2.2-common

```

Update apt:
```
sudo apt-get update
```

Try reinstalling the application again:
```
sudo apt-get install poopie
```
Sorry I get another error:
```
ben@ben-ubuntu:~$ sudo apt-get -f remove apache2-mpm-worker apache2-mpm-prefork apache2-mpm-event libapache2-mod-php5 apache2.2-common
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apache2-mpm-worker is not installed, so not removed
Package apache2-mpm-event is not installed, so not removed
Package apache2.2-common is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  php5: Depends: libapache2-mod-php5 (>= 5.1.6-1ubuntu2.3) but it is not going to be installed or
                 php5-cgi (>= 5.1.6-1ubuntu2.3) but it is not going to be installed
  php5-curl: Depends: phpapi-20060613+lfs
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ben@ben-ubuntu:~$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Get:2 http://archive.canonical.com edgy-commercial Release.gpg [191B]          
Ign http://archive.canonical.com edgy-commercial/main Translation-en_US        
Get:3 http://us.archive.ubuntu.com feisty Release.gpg [191B]         
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Get:4 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Get:5 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Ign http://archive.ubuntu.com edgy/main Translation-en_US                      
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                
Hit http://archive.canonical.com edgy-commercial Release                       
Get:6 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release                      
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                  
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US                
Get:7 http://archive.ubuntu.com edgy-updates Release.gpg [191B]                
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_US              
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_US        
Get:8 http://archive.ubuntu.com edgy-backports Release.gpg [191B]              
Ign http://archive.ubuntu.com edgy-backports/main Translation-en_US            
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://archive.canonical.com edgy-commercial/main Packages                 
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Ign http://archive.ubuntu.com edgy-backports/restricted Translation-en_US      
Ign http://archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Hit http://security.ubuntu.com edgy-security/main Packages           
Hit http://security.ubuntu.com edgy-security/restricted Packages     
Hit http://security.ubuntu.com edgy-security/main Sources            
Hit http://archive.ubuntu.com edgy Release                           
Hit http://archive.ubuntu.com edgy-updates Release                   
Hit http://archive.ubuntu.com edgy-backports Release                           
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://us.archive.ubuntu.com feisty/universe Packages           
Hit http://security.ubuntu.com edgy-security/restricted Sources     
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages  
Hit http://us.archive.ubuntu.com feisty-updates/multiverse Packages 
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/main Sources
Hit http://archive.ubuntu.com edgy/restricted Sources
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://archive.ubuntu.com edgy/universe Sources
Hit http://archive.ubuntu.com edgy/multiverse Packages
Hit http://archive.ubuntu.com edgy/multiverse Sources
Hit http://archive.ubuntu.com edgy-updates/main Packages
Hit http://archive.ubuntu.com edgy-updates/restricted Packages
Hit http://archive.ubuntu.com edgy-updates/main Sources
Hit http://archive.ubuntu.com edgy-updates/restricted Sources
Hit http://archive.ubuntu.com edgy-backports/main Packages
Hit http://archive.ubuntu.com edgy-backports/restricted Packages
Hit http://archive.ubuntu.com edgy-backports/universe Packages
Hit http://archive.ubuntu.com edgy-backports/multiverse Packages
Fetched 8B in 1s (6B/s)  
Reading package lists... Done
ben@ben-ubuntu:~$ sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libapache2-mod-php5: Depends: apache2.2-common but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
ben@ben-ubuntu:~$ 

```
> **aysiu said:**
> Your repositories list is messed up.

[Get a fresh list](http://www.psychocats.net/ubuntu/sources) and start again: ```
sudo aptitude update
sudo aptitude install apache2
```

Nope sources are ok from what I see i followed the tutorial and I still get the same error.

---

### Post by ProjectWhat on 2007-03-29
Oh and if this helps when I go to localhost I get this:
> |/dev/hda|ST380011A|33|C|
I dont even have a index file so it should show me files for the root directory.

---

### Post by ceeg on 2007-03-29
> **ProjectWhat said:**
> Oh and if this helps when I go to localhost I get this:

I dont even have a index file so it should show me files for the root directory.

Follow my instructions again, but each time it comes up with an unmet dependency (in this case php5-cgi, phpcurl, etc) add them to the list.  (unless its something like ubuntu-desktop obviously)

Otherwise, I have no idea.

---

