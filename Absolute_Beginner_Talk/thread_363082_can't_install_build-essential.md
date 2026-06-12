---
title: "can't install build-essential"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by RoryWalsh on 2007-02-16
I'm trying to install the build-essential package with apt-get but I get the following errors:

rory@rory-laptop:~/ladspa_sdk/src$ sudo apt-get install build-essential
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

Can anyone help? I've checked previous posts about this after trying different things I can't seem to make any progress....

Rory.

---

### Post by Perfect Storm on 2007-02-16
```
cat /etc/apt/sources.list
```

---

### Post by taurus on 2007-02-16
And don't forget to run the update first.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by RoryWalsh on 2007-02-16
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by Perfect Storm on 2007-02-16
Looks okay. Have you done what Taurus suggested?

---

### Post by RoryWalsh on 2007-02-16
I tried that. Here is the output, let me know if it's a problem to post such lengthy replies...cheers,

Rory.

rory@rory-laptop:~/ladspa_sdk/src$ sudo apt-get update
Password:
Get:1 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/multiverse Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/universe Translation-en_US
Get:2 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy Release
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages          
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/multiverse Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/universe Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
rory@rory-laptop:~/ladspa_sdk/src$ sudo apt-get install build-essential
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
rory@rory-laptop:~/ladspa_sdk/src$

---

### Post by Perfect Storm on 2007-02-16
Is that from a fresh install or a distro upgrade?

Hmmm...

EDIT - hmmm...Try setup a new sourcelist, there might be something missing: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by RoryWalsh on 2007-02-16
It's a fresh install. I downloaded the .iso file on Wednesday. I would really like to get it sorted, thanks for the help.

Rory.

---

### Post by taurus on 2007-02-16
Try inserting the install CD into the drive and run

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Perfect Storm on 2007-02-16
Okay, see my updated post above.

You can edit the source list like this 
```
sudo nano /etc/apt/sources.list
```
Replace it, save and exit (ctrl + o) (ctrl + x)

then:
```
sudo aptitude update && sudo aptitude upgrade
```
(some error may output may shows up about something about KEY, don't worry we'll solve that later).

---

### Post by Ptero-4 on 2007-02-16
You may also use archive.ubuntu.com instead of ie.archive.ubuntu.com. The reason is that the main archive (archive.ubuntu.com) usually is more current than the mirrors.

---

### Post by hod139 on 2007-02-16
Before playing with the source.list, just try using aptitude instead of apt.  Aptitude tends to be smarter and may be able to fix whatever is wrong.

---

### Post by RoryWalsh on 2007-02-16
tried that, still no joy I'm afraid. I also tried the suggestion about installing it from the cd, that also resulted in the same error... I've posted the output below. Any further ideas?? 


rory@rory-laptop:~$ sudo aptitude update && sudo aptitude upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Get:1 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:2 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates Release
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/main Packages                 
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Fetched 3B in 0s (4B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
rory@rory-laptop:~$ sudo apt-get install build-essential
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

### Post by RoryWalsh on 2007-02-16
Great, that worked, aptitude that is. Thank you all for your help!

Rory.

---

### Post by bracc0 on 2007-03-01
Rory,
can you please post the exact command sequence you entered to make it work?

Thanks
Claudio

---

