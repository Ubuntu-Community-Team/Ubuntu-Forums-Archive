---
title: "Ethernet network wont work"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by RodneyW on 2007-03-09
I need to get my network connection to work. Firefox works but thats it. Cannot update with update manager, wont connect or some garbage. Im under the impression I need to update before i can even install my video card drivers which also will not work but one step at a time. All I want is update to work, and to be able to download drivers for vid card from nvidia and follow the post on installing them but it wont connect to that either. What the hell is going on. Firefox works but no other internet activity? Whats with that. I can ping my laptop which is running win xp. Is this OS for real? Please help.

---

### Post by shanepardue on 2007-03-09
It may not be a network issue if you're getting internet connection from everything but update manager. What's the error message say?

---

### Post by RodneyW on 2007-03-09
it gets to file 19 of 45 and says    101 network is unreachable

---

### Post by shanepardue on 2007-03-09
Try putting "#" in front of the repository that's causing the problem.

"sudo gedit /etc/apt/sources.list" will show your repositories.

---

### Post by RodneyW on 2007-03-09
getting msg command not found

---

### Post by RodneyW on 2007-03-09
tried this command as root and as user still wont wowk, anyone know why? ive looked at it from within the OS and the specific ones have no # but cant save it from within os either

---

### Post by shanepardue on 2007-03-09
Not sure exactly what you are saying, but in the terminal simply copy and paste this command...

```
sudo gedit /etc/apt/sources.list
```

paste the contents into a reply on this forum.

---

### Post by RodneyW on 2007-03-09
This is the terminal window, it opened the file.


rodney@Rodney-linux:~$ sudo gedit /etc/apt/sources.list
Password:

(gedit:5039): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.


This is how it looks now that ive added a # to the ones without and saved the file

#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe



This is what happens when i run the update manager after above steps.

[http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2:](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz:) Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
[http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz:) Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)

---

### Post by shanepardue on 2007-03-09
paste this into that file..then type "sudo apt-get update" then "sudo aptitude dist-upgrade"

```
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
```

---

### Post by RodneyW on 2007-03-09
After pasting that code into the file, and saving it, i then get:

rodney@Rodney-linux:~$ sudo gedit /etc/apt/sources.list

(gedit:5304): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
rodney@Rodney-linux:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg 
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Translation-en_US     
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports Release.gpg                    
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/main Translation-en_US         
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/restricted Translation-en_US   
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/universe Translation-en_US
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                     
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US   
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages               
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release                                  
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources                      
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates Release                          
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources                
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports Release                        
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources                  
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Packages                      
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Sources 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/multiverse Sources
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/main Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/restricted Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy/universe Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/main Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/restricted Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-updates/universe Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/main Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/restricted Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/universe Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/multiverse Packages
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/main Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/restricted Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/universe Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/multiverse Sources
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/Release.gpg)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/i18n/Translation-en_US.bz2)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/source/Sources.gz)  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
rodney@Rodney-linux:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
rodney@Rodney-linux:~$

---

### Post by RodneyW on 2007-03-09
tried removing au. from beginning still not working

---

### Post by Malac on 2007-03-09
> **RodneyW said:**
> tried removing au. from beginning still not working
You say Firefox works does that mean that it just opens or that you can connect to the internet with it.
You say you can ping you're other computer but not whether you can ping anywhere on the internet.
Open terminal and run:```
ping www.google.com
```(Ctrl + C will stop it.)
Please post the output of running ifconfig in terminal too.

---

### Post by RodneyW on 2007-03-09
I pinged the ubuntu update to no avail. Dont worry i am going to get vista because i know it will work and there is nothing wrong with the stability of xp anyway. Just thought I'd try out linux and see what the fuss is about. Prob is i spent 5 hrs yesterday trying to get vid driver working on linux xp, and seven hrs today trying on ubuntu and in that time i could have done a million things with hardware and software in windows. Thanks for help everyone but I do not like Linux at all.

---

### Post by Malac on 2007-03-09
> **RodneyW said:**
> I pinged the ubuntu update to no avail. Dont worry i am going to get vista because i know it will work and there is nothing wrong with the stability of xp anyway. Just thought I'd try out linux and see what the fuss is about. Prob is i spent 5 hrs yesterday trying to get vid driver working on linux xp, and seven hrs today trying on ubuntu and in that time i could have done a million things with hardware and software in windows. Thanks for help everyone but I do not like Linux at all.
Okay RodneyW, that's fine, Linux isn't for everyone.
It might be worth pointing out this about Vista though :
[http://www.google.co.uk/search?hl=en&q=Vista+Bugs&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&q=Vista+Bugs&btnG=Search&meta=)
And the number of people that have bought HD Video Cards and other peripherals which are now useless in Vista as the drivers won't work or aren't certified and unlike XP, in Vista you can't tell it to ignore the lack of certification and install the driver anyway.

Good Luck with Vista. :)

---

