---
title: "Windows Networks (smb) didn't load"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by razorbak on 2008-01-04
Hi,

I am trying to share a folder on my UBUNTU machine with me Windows network.
I right clicked the folder and services were automatically installed for sharing.  Problem is there was an error and windows netorking (SMB) was not installed just unix networking.  How do I get the SMB service in there??


Thanks

Mark

---

### Post by spiderbatdad on 2008-01-04
[https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

---

### Post by razorbak on 2008-01-04
Thanks but looks like greek to me.

How do I in simple terms load the SMB service into UBUNTU??

Thanks

---

### Post by razorbak on 2008-01-04
can't I just right click and share a folder?

---

### Post by razorbak on 2008-01-04
UBUNTU can see allmy windows PCs but none of them can see the UBUNTU one

---

### Post by spiderbatdad on 2008-01-04
yep

---

### Post by njparton on 2008-01-04
In a terminal:

```

sudo apt-get install samba smbfs

```

You can then try right clicking on folders to share them or directly editing the samba config file:

```

sudo gedit /etc/samba/smb.conf

```

---

### Post by razorbak on 2008-01-04
I input the code lines but smb optionis still not there as an share option after right clicking a folder

---

### Post by razorbak on 2008-01-04
USER@AMDLINUX:~$ sudo apt-get install samba smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed
  samba smbfs
0 upgraded, 2 newly installed, 0 to remove and 39 not upgraded.
Need to get 3768kB of archives.
After unpacking 9179kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  samba smbfs
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main samba 3.0.24-2ubuntu1.2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main smbfs 3.0.24-2ubuntu1.2
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.24-2ubuntu1.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.24-2ubuntu1.2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.24-2ubuntu1.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.24-2ubuntu1.2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
USER@AMDLINUX:~$

---

### Post by njparton on 2008-01-04
Do you have all the repositiories enabled?

Try ticking them all in Synaptic.  Samba is one of the most commonly used packages and for some reason your installation can't find it to download and install.

---

### Post by razorbak on 2008-01-04
Thanks....I ticked some boxes and stuff

cheers

---

### Post by handaxe on 2008-01-04
Go to [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/) and you will see why.  Your repo index is out of date and the file present is another version, viz samba_3.0.24-2ubuntu1.5_i386.deb (not 1.2).

Update synaptic by:

sudo apt-get update and try again.

HA

---

### Post by razorbak on 2008-01-04
Sharing ok now apart from the fact that wont work at all with Vista and my XP machine requires a user name and password which I don't remember having  set up!

---

### Post by razorbak on 2008-01-04
USER@AMDLINUX:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_GB
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_GB
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]       
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_GB      
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/universe Translation-en_GB
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/main Translation-en_GB
Get: 5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release [5999B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/restricted Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/multiverse Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/universe Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release.gpg                              
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Translation-en_GB
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/multiverse Sources
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-security/universe Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Packages
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Packages
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/free Sources
  404 Not Found
Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy/non-free Sources
  404 Not Found
Fetched 6193B in 0s (10.1kB/s)
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz)  404 Not Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
USER@AMDLINUX:~$

---

### Post by pavpan on 2008-01-04
Try this:
System > Administration > Software sources.
Enter you password if it asks you
Second tab at the top
uncheck the "medibuntu" lines
close
OK to reload.

---

### Post by njparton on 2008-01-04
Each windows user wanting access samba needs to have a linux account.

Then they need to have a samba password created:

```

sudo smbpasswd -a *username*

```

please read the samba guide linked to by someone else earlier :)

---

### Post by handaxe on 2008-01-04
There are 2 forms of share under samba on a linux box: user and share.  User is the default and as the prev poster wrote, needs an account on the Linux box to work. To emulate Windows "promiscuous" :-) sharing edit /etc/samba/smb.conf and seek the following section and change security from "user" to "share":

```
####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
   security = share
```

HA

PS for what it is worth, the Ubuntu default method of sharing seldom works for new users expecting Windows-like (ie share level) behaviour and enjoying the apparently simple gui interface provided by the gnome Ubuntu environment. A pity that no warning of the 2 options is provided...

---

