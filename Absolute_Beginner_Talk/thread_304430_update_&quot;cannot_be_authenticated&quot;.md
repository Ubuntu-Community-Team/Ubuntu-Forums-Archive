---
title: "update &quot;cannot be authenticated&quot;"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by ginkhao on 2006-11-21
My update notifier popped up and advised me the Thunderbird 1.5.0.8 update was available so I went ahead to update it and it advised me that this update couldn't be authenticated.  I have added no 3rd party repositories and I have the cdimage and ftpmaster gpg keys installed.

What I would like to know is if it is normal for software installs from the standard repositories to not be authenticated?

---

### Post by ReaderRat on 2006-11-21
No, I believe you have to download a "public key" for the mozilla(?) repository. You already have 2 keys installed for authentication of repos you're using....just guessing here, really...

---

### Post by ginkhao on 2006-11-21
Thanks for your response, however as the update wasn't installed from a Mozilla repository I'm not sure where to start looking for the key for it.  Is there a way to check who (if anyone) has signed an package/update before installing it?

---

### Post by ReaderRat on 2006-11-21
When I had need of a public key, iy was given in the error message...ah, phooey. Here is something about it:
KEY Public HowTo get
          **[http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773](http://www.ubuntuforums.org/showthread.php?p=1653773#post1653773)**
Forgot I had that...

---

### Post by ginkhao on 2006-11-21
Thanks for that, only I didn't get an error as such, and I didn't see any key ID...the standard Software Updates window appears, and after choosing to install the updates, it says they "cannot be authenticated", provides a warning and asks if you wish to go ahead anyway.

It doesn't appear to be a public key error, it's like the update wasn't signed...I wish I hadn't installed the update now so I could take a screenshot!

---

### Post by Manuel Siggen on 2006-11-23
I encountered the same problem :

```

msi@x40:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libggi2 mplayer
The following packages will be upgraded:
  mozilla-thunderbird
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 10.7MB of archives.
After unpacking 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  mozilla-thunderbird
Install these packages without verification [y/N]? N
E: Some packages could not be authenticated

```

Previously I did :

```
msi@x40:~$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]                                                        
Ign http://security.ubuntu.com edgy-security/main Translation-en_US                                                      
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US                                  
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US                                    
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US                                  
Get:2 http://security.ubuntu.com edgy-security Release [27.3kB]                                            
Get:3 http://archive.ubuntu.com edgy Release.gpg [191B]                                                    
Ign http://archive.ubuntu.com edgy/universe Translation-en_US               
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US             
Ign http://archive.ubuntu.com edgy/main Translation-en_US
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US
Hit http://archive.ubuntu.com edgy Release                            
Get:4 http://ch.archive.ubuntu.com edgy Release.gpg [191B]          
Get:5 http://ch.archive.ubuntu.com edgy-updates Release.gpg [189B]  
Ign http://ch.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://ch.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com edgy-security/main Packages          
Get:6 http://ch.archive.ubuntu.com edgy-backports Release.gpg [191B]
Ign http://ch.archive.ubuntu.com edgy-backports/main Translation-en_US
Ign http://ch.archive.ubuntu.com edgy-backports/restricted Translation-en_US
Hit http://archive.ubuntu.com edgy/universe Packages                 
Hit http://security.ubuntu.com edgy-security/restricted Packages     
Hit http://security.ubuntu.com edgy-security/main Sources            
Hit http://security.ubuntu.com edgy-security/restricted Sources      
Hit http://security.ubuntu.com edgy-security/universe Packages       
Hit http://security.ubuntu.com edgy-security/multiverse Packages     
Ign http://ch.archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://ch.archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Hit http://ch.archive.ubuntu.com edgy Release                        
Hit http://ch.archive.ubuntu.com edgy-updates Release                
Hit http://ch.archive.ubuntu.com edgy-backports Release              
Hit http://archive.ubuntu.com edgy/multiverse Packages               
Hit http://archive.ubuntu.com edgy/main Packages                    
Hit http://archive.ubuntu.com edgy/restricted Packages              
Hit http://security.ubuntu.com edgy-security/universe Sources       
Hit http://security.ubuntu.com edgy-security/multiverse Sources
Hit http://ch.archive.ubuntu.com edgy/main Sources
Hit http://ch.archive.ubuntu.com edgy/restricted Sources
Hit http://ch.archive.ubuntu.com edgy/universe Sources
Hit http://ch.archive.ubuntu.com edgy/multiverse Sources
Hit http://ch.archive.ubuntu.com edgy-updates/main Packages
Hit http://ch.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://ch.archive.ubuntu.com edgy-updates/main Sources
Hit http://ch.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://ch.archive.ubuntu.com edgy-backports/main Packages
Hit http://ch.archive.ubuntu.com edgy-backports/restricted Packages
Hit http://ch.archive.ubuntu.com edgy-backports/universe Packages
Hit http://ch.archive.ubuntu.com edgy-backports/multiverse Packages
Hit http://ch.archive.ubuntu.com edgy-backports/main Sources
Hit http://ch.archive.ubuntu.com edgy-backports/restricted Sources
Hit http://ch.archive.ubuntu.com edgy-backports/universe Sources
Hit http://ch.archive.ubuntu.com edgy-backports/multiverse Sources
Fetched 5552B in 1s (3825B/s)
Reading package lists... Done

```

... which doesn't show any kind of error.

Then I spent a few minutes searching the forums and googling for a solution. But I didn't found anything really matching the problem.

Then, I did again :
```

msi@x40:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libggi2 mplayer
The following packages will be upgraded:
  mozilla-thunderbird
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 10.7MB of archives.
After unpacking 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://security.ubuntu.com edgy-security/main mozilla-thunderbird 1.5.0.8-0ubuntu0.6.10 [10.7MB]
Fetched 10.7MB in 1m35s (113kB/s)                                                                                        
Preconfiguring packages ...
(Reading database ... 137088 files and directories currently installed.)
Preparing to replace mozilla-thunderbird 1.5.0.7-0ubuntu1 (using .../mozilla-thunderbird_1.5.0.8-0ubuntu0.6.10_i386.deb) ...
Unpacking replacement mozilla-thunderbird ...
Setting up mozilla-thunderbird (1.5.0.8-0ubuntu0.6.10) ...

```

... and this time everything went nicely !

Could be that first *apt-get update* somehow silentely failed to  authenticate the *[http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main* repository ?

---

### Post by helmeteye on 2006-11-23
I need to know the same thing.

---

### Post by ginkhao on 2006-11-28
Same thing again this morning but I haven't installed it so I can copy out the messages.

- Update notifier icon appears - Software Updates advises that 1 update can be installed (tar)
- Click Install Updates and a dialog box appears:

Summary
Apply the following changes...etc?
Warning You are about to install software that can't be authenticated!  Doing this could allow a malicious individual to damage or take control of your system. 

Then the details of the tar update under 'NOT AUTHENTICATED'

Can anyone tell me if this is normal?  If it is not, how can I find out who signed this update before I install it so I can get the public key?

---

### Post by ginkhao on 2006-11-28
I think I've resolved my problem and hopefully this may be of use to others.  It appears the problem is due to my ISP using a transparent proxy for http traffic.  I ran this command:

apt-get update -o Acquire::http::No-Cache=True
(from here: [https://launchpad.net/distros/ubuntu/+source/apt/+bug/33505](https://launchpad.net/distros/ubuntu/+source/apt/+bug/33505))

It gave me an error-free update and then the security update authenticated without any problems.

---

### Post by hyperduck on 2006-12-08
> I think I've resolved my problem and hopefully this may be of use to others. It appears the problem is due to my ISP using a transparent proxy for http traffic.

Yep, I got the same error twice when I was trying to update an ubuntu desktop at work (a little runty HP Pavillion that I run for s&giggles), and I just tried updating and upgrading again and it worked okay.

We've had several issues with our ISP's proxies in the past...

---

