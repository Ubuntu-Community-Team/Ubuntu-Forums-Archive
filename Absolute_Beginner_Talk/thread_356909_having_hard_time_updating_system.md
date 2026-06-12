---
title: "having hard time updating system"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-02-08
i keep getting notice that my system needs updating, but it keeps failing. :(

```

gail@gail-oldpos:~$ sudo apt-get update
Password:
Get:1 http://security.ubuntu.com dapper-security Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Err http://ca.archive.ubuntu.com dapper Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Networ k is unreachable)
Ign http://ca.archive.ubuntu.com dapper-backports Release
Ign http://ca.archive.ubuntu.com dapper-backports/main Packages
Ign http://ca.archive.ubuntu.com dapper-backports/restricted Packages
Ign http://ca.archive.ubuntu.com dapper-backports/universe Packages
Ign http://ca.archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://ca.archive.ubuntu.com dapper-backports/main Sources
Ign http://ca.archive.ubuntu.com dapper-backports/restricted Sources
Ign http://ca.archive.ubuntu.com dapper-backports/universe Sources
Ign http://ca.archive.ubuntu.com dapper-backports/multiverse Sources
Err http://ca.archive.ubuntu.com dapper-backports/main Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/restricted Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/universe Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/multiverse Packages
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-backports/main Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-backports/restricted Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-backports/universe Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-backports/multiverse Sources
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Fetched 1B in 24m3s (0B/s)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
gail@gail-oldpos:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-386 linux-restricted-modules-386
The following packages will be upgraded:
  app-install-data-commercial cpio dpkg dselect hal hal-device-manager language-pack-en language-pack-gnome-en
  libc6 libc6-i686 libhal-storage1 libhal1 liblircclient0 libtag1c2a libtheora0 linux-386
  linux-restricted-modules-common locales lvm2 readahead synaptic
21 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 16.1MB/16.1MB of archives.
After unpacking, 11.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  dpkg locales libc6 libc6-i686 lvm2 language-pack-en language-pack-gnome-en cpio dselect
  app-install-data-commercial libhal1 hal hal-device-manager libhal-storage1 libtag1c2a libtheora0 readahead
  synaptic liblircclient0
Install these packages without verification [y/N]? y
Err http://ca.archive.ubuntu.com dapper-updates/main dpkg 1.13.11ubuntu7
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main locales 2.3.18.1
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main libc6 2.3.6-0ubuntu20.4
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-updates/main libc6-i686 2.3.6-0ubuntu20.4
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-updates/main lvm2 2.02.02-1ubuntu1.2
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-updates/main language-pack-en 1:6.06+20061130
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-updates/main language-pack-gnome-en 1:6.06+20061205
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main cpio 2.6-10ubuntu0.2
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main dselect 1.13.11ubuntu7
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main app-install-data-commercial 5.3
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main libhal1 0.5.7-1ubuntu18.2
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-updates/main hal 0.5.7-1ubuntu18.2
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main hal-device-manager 0.5.7-1ubuntu18.2
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main libhal-storage1 0.5.7-1ubuntu18.2
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/main libtag1c2a 1.4-4~dapper1
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://ca.archive.ubuntu.com dapper-backports/main libtheora0 0.0.0.alpha7-1ubuntu1~dapper1
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/main readahead 1:0.20050517.0220-0ubuntu5~dapper1
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-updates/main synaptic 0.57.8ubuntu13
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Err http://ca.archive.ubuntu.com dapper-backports/main liblircclient0 0.8.0-9ubuntu1~dapper1
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.13.11ubuntu7_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/langpack-locales/locales_2.3.18.1_all.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.6-0ubuntu20.4_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.6-0ubuntu20.4_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/lvm2/lvm2_2.02.02-1ubuntu1.2_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_6.06+20061130_all.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.06+20061205_all.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/c/cpio/cpio_2.6-10ubuntu0.2_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dselect_1.13.11ubuntu7_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_5.3_all.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.7-1ubuntu18.2_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.7-1ubuntu18.2_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal-device-manager_0.5.7-1ubuntu18.2_all.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.7-1ubuntu18.2_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/t/taglib/libtag1c2a_1.4-4~dapper1_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora0_0.0.0.alpha7-1ubuntu1~dapper1_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/r/readahead-list/readahead_0.20050517.0220-0ubuntu5~dapper1_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.57.8ubuntu13_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/lirc/liblircclient0_0.8.0-9ubuntu1~dapper1_i386.deb Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0). - connect (101 Network is unreachable)
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

```

...oh damn, i cant show my source list cuz i closed terminal. :( umm... i'll try again tomorrow...

---

### Post by taurus on 2007-02-08
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **ca.** from all your repos.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by romi7519 on 2007-02-13
^ Thanks for the info. Helped me a lot.

---

### Post by garymc1 on 2007-04-19
hi there I am having the same problem when you said remove the ca. what do you mean
 thanks gary

---

### Post by Seisen on 2007-04-19
[http://**ca](http://**ca)**.archive.ubuntu.com dapper Release.gpg 

He's talking about the part that I made bold.

---

### Post by garymc1 on 2007-04-19
i have not got any with   [http://ca](http://ca).
thats a copy of my source.list but i cant update the connection timed out


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main

##Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security restricted

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) edgy main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-security main universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END
# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

# Repository for wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

---

### Post by Seisen on 2007-04-19
Its because everybody is upgrading to Feisty, the same thing happened when Edgy came out.

---

### Post by il-luzhin on 2007-04-19
So I'm in the same boat and removing the ca just turned "connection timed out"  into "cannot resolve".

If this is an upgrade issue what's the fix?

```

Err http://.archive.ubuntu.com edgy Release.gpg
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy/main Translation-en_CA                  
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy/restricted Translation-en_CA            
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates Release.gpg                     
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/main Translation-en_CA          
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/restricted Translation-en_CA    
  Could not resolve '.archive.ubuntu.com'
Ign http://.archive.ubuntu.com edgy Release                                 
Ign http://.archive.ubuntu.com edgy-updates Release                         
Ign http://.archive.ubuntu.com edgy/main Packages                           
Ign http://.archive.ubuntu.com edgy/restricted Packages                     
Ign http://.archive.ubuntu.com edgy/main Sources                            
Ign http://.archive.ubuntu.com edgy/restricted Sources                      
Ign http://.archive.ubuntu.com edgy-updates/main Packages                    
Ign http://.archive.ubuntu.com edgy-updates/restricted Packages              
Ign http://.archive.ubuntu.com edgy-updates/main Sources                     
Ign http://.archive.ubuntu.com edgy-updates/restricted Sources               
Err http://.archive.ubuntu.com edgy/main Packages                            
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy/restricted Packages                      
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy/main Sources                             
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy/restricted Sources                       
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/main Packages                    
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/restricted Packages              
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/main Sources                     
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/restricted Sources               
  Could not resolve '.archive.ubuntu.com'
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]            
Ign http://security.ubuntu.com edgy-security/main Translation-en_CA          
Get:2 http://ca.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://ca.archive.ubuntu.com edgy/universe Translation-en_CA
Get:3 http://ca.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://ca.archive.ubuntu.com edgy-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com edgy Release  
Hit http://ca.archive.ubuntu.com edgy-updates Release               
Hit http://ca.archive.ubuntu.com edgy/universe Packages             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_CA
Ign http://security.ubuntu.com edgy-security/universe Translation-en_CA
Hit http://security.ubuntu.com edgy-security Release
Hit http://ca.archive.ubuntu.com edgy-updates/universe Packages
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://security.ubuntu.com edgy-security/universe Packages
Fetched 3B in 1s (2B/s)  
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_CA.bz2 Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_CA.bz2 Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_CA.bz2 Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_CA.bz2 Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz Could not resolve '.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

thnx

---

### Post by splatmatic on 2007-04-19
> **il-luzhin said:**
> So I'm in the same boat and removing the ca just turned "connection timed out"  into "cannot resolve".

If this is an upgrade issue what's the fix?

```

Err http://.archive.ubuntu.com edgy Release.gpg
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy/main Translation-en_CA                  
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy/restricted Translation-en_CA            
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates Release.gpg                     
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/main Translation-en_CA          
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/restricted Translation-en_CA    
  Could not resolve '.archive.ubuntu.com'
Ign http://.archive.ubuntu.com edgy Release                                 
Ign http://.archive.ubuntu.com edgy-updates Release                         
Ign http://.archive.ubuntu.com edgy/main Packages                           
Ign http://.archive.ubuntu.com edgy/restricted Packages                     
Ign http://.archive.ubuntu.com edgy/main Sources                            
Ign http://.archive.ubuntu.com edgy/restricted Sources                      
Ign http://.archive.ubuntu.com edgy-updates/main Packages                    
Ign http://.archive.ubuntu.com edgy-updates/restricted Packages              
Ign http://.archive.ubuntu.com edgy-updates/main Sources                     
Ign http://.archive.ubuntu.com edgy-updates/restricted Sources               
Err http://.archive.ubuntu.com edgy/main Packages                            
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy/restricted Packages                      
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy/main Sources                             
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy/restricted Sources                       
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/main Packages                    
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/restricted Packages              
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/main Sources                     
  Could not resolve '.archive.ubuntu.com'
Err http://.archive.ubuntu.com edgy-updates/restricted Sources               
  Could not resolve '.archive.ubuntu.com'
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]            
Ign http://security.ubuntu.com edgy-security/main Translation-en_CA          
Get:2 http://ca.archive.ubuntu.com edgy Release.gpg [191B]
Ign http://ca.archive.ubuntu.com edgy/universe Translation-en_CA
Get:3 http://ca.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://ca.archive.ubuntu.com edgy-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com edgy Release  
Hit http://ca.archive.ubuntu.com edgy-updates Release               
Hit http://ca.archive.ubuntu.com edgy/universe Packages             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_CA
Ign http://security.ubuntu.com edgy-security/universe Translation-en_CA
Hit http://security.ubuntu.com edgy-security Release
Hit http://ca.archive.ubuntu.com edgy-updates/universe Packages
Hit http://security.ubuntu.com edgy-security/main Packages
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://security.ubuntu.com edgy-security/universe Packages
Fetched 3B in 1s (2B/s)  
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_CA.bz2 Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_CA.bz2 Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_CA.bz2 Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_CA.bz2 Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz Could not resolve '.archive.ubuntu.com'
Failed to fetch http://.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/source/Sources.gz Could not resolve '.archive.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

thnx

You'll probably kicking your self for overlooking something so small, but you forgot to take out the "[SIZE="5"].[/SIZE]" (dot/period) from the front.

it should be "archive.ubuntu.com"
not "**[SIZE="5"].[/SIZE]**archive.ubuntu.com"

:)

---

### Post by il-luzhin on 2007-04-20
Oops.  That was a foolish mistake.  Sorry about that but I'm still having trouble.

when I sudo gkedit /etc/apt/sources.list

```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

```

notice the lack of any **ca.** anywhere.  Yet when I sudo apt-get update I get the connection refusal again.

```

Err http://ca.archive.ubuntu.com edgy Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Err http://ca.archive.ubuntu.com edgy/universe Translation-en_CA               
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Err http://ca.archive.ubuntu.com edgy-updates Release.gpg                      
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]        
Ign http://security.ubuntu.com edgy-security/main Translation-en_CA            
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_CA      
Err http://ca.archive.ubuntu.com edgy-updates/universe Translation-en_CA       
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Ign http://security.ubuntu.com edgy-security/universe Translation-en_CA        
Hit http://security.ubuntu.com edgy-security Release                      
Hit http://security.ubuntu.com edgy-security/main Packages                
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources           
Hit http://security.ubuntu.com edgy-security/universe Packages            
Get:2 http://archive.ubuntu.com edgy Release.gpg [191B]                        
Ign http://archive.ubuntu.com edgy/main Translation-en_CA
Ign http://archive.ubuntu.com edgy/restricted Translation-en_CA
Get:3 http://archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com edgy-updates/main Translation-en_CA
Ign http://archive.ubuntu.com edgy-updates/restricted Translation-en_CA
Hit http://archive.ubuntu.com edgy Release
Hit http://archive.ubuntu.com edgy-updates Release
Hit http://archive.ubuntu.com edgy/main Packages
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/main Sources
Hit http://archive.ubuntu.com edgy/restricted Sources
Hit http://archive.ubuntu.com edgy-updates/main Packages                       
Hit http://archive.ubuntu.com edgy-updates/restricted Packages                 
Hit http://archive.ubuntu.com edgy-updates/main Sources                        
Hit http://archive.ubuntu.com edgy-updates/restricted Sources                  
Fetched 383B in 25s (15B/s)                                                    
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_CA.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

notice the **ca.** is back

---

