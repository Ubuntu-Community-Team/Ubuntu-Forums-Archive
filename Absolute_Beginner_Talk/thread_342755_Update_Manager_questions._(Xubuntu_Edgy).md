---
title: "Update Manager questions. (Xubuntu Edgy)"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2007-01-20
I have a few questions about the update manager in Xubuntu (edgy):

- Does it slow down my computer if I download and install all the updates?

- I get this error message:```
You must check for updates manually

Your system does not check for updates automatically. You can configure this behavior in Software Sources on the Internet Updates tab.
``` Where is this tab?

- I have checked and installed updates anyway. When I try to update Gimp and Gimp-data, I get an error message. Is it very important to fix this problem? Now Gimp and gimp-data stay in my recommended update list.

- How often should I perform an update? Can I set my pc up to do this automatically?

---

### Post by an.echte.trilingue on 2007-01-20
There is a difference between update and upgrade.  My system is in French so I cannot tell you exactly what is located under which tab on the GUI, but this is how it works on the command line:

Linux uses a lot of shared libraries, meaning that usually there are several very small programs that do very specific things (like draw lines on the screen, for example) that are called by many different higher level programs (that then use them to turn those lines into buttons, for example).  This makes the OS smaller and faster, but means that you need a very advanced package (or program) manager that makes sure that all the versions are compatible with eachother.

The package manager that Ubuntu uses is called apt or aptitude.  Apt keeps a couple of databases, one is the list of packages that is installed with their versions and dependancies, and another is the list of packages available in the repositories and their versions and dependancies.  This second one needs to be refreshed (aka, a new list downloaded) every time what is in the repositories changes, or else it will try to get something that is not there, which is probably what your error with GIMP is.

So, you need to refresh the second data base with this:
```
sudo aptitude update
```

Note that this does not update your system, just the apt database.  I believe the synaptic version of this is a "refresh" button, but I am not sure.  If you skip this step, eventually you won't be able to install anything.

To update your system, do this:
```
sudo aptitude upgrade
```

You should do this once a week or so.  Although updates sometimes break things, it is almost always a good thing to do and will improve your performance.

Take care
-mat

---

### Post by stroopwafel on 2007-01-21
the commands you gave me cause the same problems update manager gave me:

The error is shown at the very bottom of the list. 

Danke, merci, bedankt, thanks for looking at my problem. (I'm a Dutchman living in the US)

```
maarten@maarten-laptop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]               
Ign http://security.ubuntu.com edgy-security/main Translation-en_US             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US       
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US      
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]                     
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US                   
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US             
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy/multiverse Translation-en_US
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com edgy-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com edgy Release                                 
Hit http://us.archive.ubuntu.com edgy-updates Release                         
Hit http://security.ubuntu.com edgy-security/main Packages                      
Hit http://us.archive.ubuntu.com edgy/main Packages                             
Hit http://security.ubuntu.com edgy-security/restricted Packages              
Hit http://security.ubuntu.com edgy-security/universe Packages                  
Hit http://security.ubuntu.com edgy-security/multiverse Packages                
Hit http://us.archive.ubuntu.com edgy/restricted Packages                       
Hit http://security.ubuntu.com edgy-security/main Sources                       
Hit http://security.ubuntu.com edgy-security/restricted Sources                 
Hit http://security.ubuntu.com edgy-security/universe Sources                   
Hit http://security.ubuntu.com edgy-security/multiverse Sources                 
Hit http://us.archive.ubuntu.com edgy/universe Packages                         
Hit http://us.archive.ubuntu.com edgy/multiverse Packages                     
Hit http://us.archive.ubuntu.com edgy/main Sources                            
Hit http://us.archive.ubuntu.com edgy/restricted Sources                      
Hit http://us.archive.ubuntu.com edgy/universe Sources                        
Hit http://us.archive.ubuntu.com edgy/multiverse Sources                      
Hit http://us.archive.ubuntu.com edgy-updates/main Packages                   
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Sources
Hit http://us.archive.ubuntu.com edgy-updates/multiverse Sources
Ign http://getswiftfox.com unstable Release.gpg
Ign http://getswiftfox.com unstable/non-free Translation-en_US
Ign http://getswiftfox.com unstable Release
Ign http://getswiftfox.com unstable/non-free Packages
Hit http://getswiftfox.com unstable/non-free Packages
Fetched 3B in 5s (1B/s)
Reading package lists... Done
maarten@maarten-laptop:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  gimp gimp-data 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2105kB/5066kB of archives. After unpacking 4096B will be used.
Do you want to continue? [Y/n/?] y
Get:1 http://us.archive.ubuntu.com edgy-updates/main gimp-data 2.2.13-1ubuntu3 [2105kB]
Err http://us.archive.ubuntu.com edgy-updates/main gimp-data 2.2.13-1ubuntu3    
  Connection timed out [IP: 195.248.90.38 80]

```

---

