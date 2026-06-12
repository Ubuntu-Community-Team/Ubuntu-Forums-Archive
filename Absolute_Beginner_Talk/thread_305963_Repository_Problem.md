---
title: "Repository Problem"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Gerry Atric on 2006-11-24
Can anyone please advise why I am getting the below problem with updates. It does not appear to be affecting my installation of Dapper 6.06LTS but has only occured in the past few weeks. 

jeff123@jeff123-Main:~$ sudo apt-get update
Password:
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages [50.2kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [60.0kB]
99% [7 Packages gzip 0]                                             21.2kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
  Sub-process gzip returned an error code (1)
99% [8 Sources gzip 0]                                              21.2kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Sub-process gzip returned an error code (1)
Fetched 8B in 7s (1B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jeff123@jeff123-Main:~$


My Sources List  **

##Automatix sources.list
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
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports universe

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

## created by automatixrepo3
deb [http://people.ubuntu.com/~seb128/deb](http://people.ubuntu.com/~seb128/deb) ./
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

---

### Post by cantormath on 2006-11-24
try putting a # infront of 
[http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
then apt-get update again.

also, its not very safe to have the universe and multiverse open all the time, just when you need it.  

Note: If you have not tried it, you might like [automatix2]("http://getautomatix.com")

---

### Post by Gerry Atric on 2006-11-24
Thanks for your help. I Tried putting the hash in front and then tried updating again but still the same. If I install Automatix2 will that interfere with the entries for automatix1 etc.

---

### Post by ginkhao on 2006-11-24
cantormath, could you tell me what you mean by "to have the universe and multiverse open all the time" and why it isn't safe?

---

### Post by kenweill on 2006-11-24
> **Gerry Atric said:**
> 
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [60.0kB]
99% [7 Packages gzip 0]                                             21.2kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
  Sub-process gzip returned an error code (1)
99% [8 Sources gzip 0]                                              21.2kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Sub-process gzip returned an error code (1)
Fetched 8B in 7s (1B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jeff123@jeff123-Main:~$


Thats the problem. On dapper-main souce.

Try putting a # sign in:
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

So that would be:
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main

Then run:
sudo apt-get update
again....

---

### Post by Gerry Atric on 2006-11-24
Tried that as well but still getting the same result

---

### Post by Gerry Atric on 2006-11-24
Does anyone know if I install Automatix2 over the top of the existing installation of Automatix if it will cause any problems to my current installation. I am hoping it may correct the existing faults in the updates.
Thanks to all who have tried to help so far.

---

### Post by kenweill on 2006-11-24
Try adding # sign in all lines starting with "deb-src".
If that works, then one of the "deb-src" is not working.

---

### Post by Gerry Atric on 2006-11-24
Hi Kenweill,

Yes tried commenting out all the SRC lines and then tried updating again but still getting the same errors.

---

### Post by kenweill on 2006-11-24
Did you save the file?
Did you open it through "sudo gedit /etc/apt/sources.lst"?
Coz if you open and edit it without the sudo or gksudo command, editing the file is useless.

---

### Post by Gerry Atric on 2006-11-24
Hi Kenweill,

Yes I opened and saved the sources file with gksudo nautilus and edited and then saved same. I have just re opened and uncommented every entry and then saved and run update but I am getting the same errors.

jeff123@jeff123-Main:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Hit [http://dl.google.com](http://dl.google.com) stable Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [57.5kB]
99% [7 Sources gzip 0] [Waiting for headers]                        21.5kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Sub-process gzip returned an error code (1)
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages [50.2kB]
99% [Working]                                                       21.5kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 8B in 9s (1B/s)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
jeff123@jeff123-Main:~$

---

### Post by DX 00 on 2007-01-12
From what i've read, people have been able to fix this problem by using ftp:// instead of http:// on their repos. Try this on your repos:

From:
```
deb **http**://archive.ubuntu.com/ubuntu dapper main
```

To:
```
deb **ftp**://archive.ubuntu.com/ubuntu dapper main
```

---

