---
title: "Termin error :S"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by Demon Designs on 2007-07-25
Hi guys I am really new at linux like a few days and well I was getting help from skymera to get beryl running on my ubuntu(feisty) and well i ketp getting this error

```
sidewinder@thomas-desktop:~$ sudo apt-get update
Err http://au.archive.ubuntu.com feisty Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/main Translation-en_AU                 
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/restricted Translation-en_AU           
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/universe Translation-en_AU             
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/multiverse Translation-en_AU           
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-updates Release.gpg                    
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Get:1 http://media.blutkind.org edgy Release.gpg [189B]                        
Ign http://media.blutkind.org edgy/main-edgy Translation-en_AU                 
Err http://au.archive.ubuntu.com feisty-updates/main Translation-en_AU         
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-updates/restricted Translation-en_AU   
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-updates/universe Translation-en_AU     
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-updates/multiverse Translation-en_AU   
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Hit http://media.blutkind.org edgy Release                                     
Get:2 http://ubuntu.beryl-project.org edgy Release.gpg [191B]                  
Err http://au.archive.ubuntu.com feisty-backports Release.gpg                  
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Get:3 http://medibuntu.sos-sts.com feisty Release.gpg [189B]                   
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_AU                 
Err http://media.blutkind.org edgy Release                                     
  
Err http://au.archive.ubuntu.com feisty-backports/main Translation-en_AU       
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-backports/restricted Translation-en_AU 
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-backports/universe Translation-en_AU   
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Get:4 http://media.blutkind.org edgy Release [5755B]                           
Err http://au.archive.ubuntu.com feisty-backports/multiverse Translation-en_AU 
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Get:5 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_AU
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_AU
Ign http://media.blutkind.org edgy Release                           
Hit http://ubuntu.beryl-project.org edgy Release                     
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_AU 
Hit http://medibuntu.sos-sts.com feisty Release
Err http://medibuntu.sos-sts.com feisty Release                    
  
Ign http://media.blutkind.org edgy/main-edgy Packages              
Ign http://security.ubuntu.com feisty-security/universe Translation-en_AU
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_AU
Hit http://security.ubuntu.com feisty-security Release               
Get:6 http://medibuntu.sos-sts.com feisty Release [2195B]            
Ign http://medibuntu.sos-sts.com feisty Release                            
Hit http://media.blutkind.org edgy/main-edgy Packages
Hit http://security.ubuntu.com feisty-security/main Packages
Ign http://medibuntu.sos-sts.com feisty/free Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Ign http://medibuntu.sos-sts.com feisty/free Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://medibuntu.sos-sts.com feisty/free Sources
Hit http://medibuntu.sos-sts.com feisty/non-free Sources
Fetched 8520B in 3s (2161B/s)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://ubuntu.beryl-project.org/dists/edgy/Release  Unable to find expected entry  main-edgy/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
W: GPG error: http://media.blutkind.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31A5F97FED8A569E
W: GPG error: http://medibuntu.sos-sts.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.
sidewinder@thomas-desktop:~$ 

``` 

and skymera help me get this far and well I hav already got a new source and that didn't help at all what can i do... Any ideas plz tell me.

thnx demon

---

### Post by skymera on 2007-07-25
weve tried the Ubuntu source generator to get different sources.
but the same error occured.

---

### Post by RomeReactor on 2007-07-25
Hi. Can you use the internet otherwise (browse with Firefox, chat, etc)? Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by Demon Designs on 2007-07-25
```
sidewinder@thomas-desktop:~$ cat /etc/apt/sources.list
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://au.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://au.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

deb-src http://au.archive.ubuntu.com/ubuntu feisty main restricted
deb-src http://au.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://au.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://au.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

deb-src http://au.archive.ubuntu.com/ubuntu feisty universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://au.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse 

deb-src http://au.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

# Upstream Beryl
# GPG key: ed8a569e
deb http://media.blutkind.org/xgl/ edgy main-edgy 

deb-src http://ubuntu.beryl-project.org/ edgy main-edgy

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free 

deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
sidewinder@thomas-desktop:~$ 

``` 

There ya go luv ur tux by the way :P

---

### Post by Seisen on 2007-07-25
Those repo's are down as of right now you would be better off trying the main servers or another mirror.

---

### Post by RomeReactor on 2007-07-25
You have Edgy entries mixed in there; since you run feisty, this could be a problem (though I'm not sure this is your case). You could try to use the one I'm going to post, though it will only have the official Ubuntu repositories plus Medibuntu.

If you decide to go ahead with this:

1.- Back up your current sources.list:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

2.- Open your sources.list file in Gedit:
```
gksudo gedit /etc/apt/sources.list
```
empty your file, and paste the following:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free


3.- Save and close Gedit, then:
```
sudo apt-get update
```

-----------------------------------------
> There ya go luv ur tux by the way :P
Thanks!

---

### Post by Demon Designs on 2007-07-25
I tried that and it did this...
```
idewinder@thomas-desktop:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
Password:
sidewinder@thomas-desktop:~$ gksudo gedit /etc/apt/sources.list
sidewinder@thomas-desktop:~$ sudo apt-get update
Err http://au.archive.ubuntu.com feisty Release.gpg                            
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/main Translation-en_AU                 
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/restricted Translation-en_AU           
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/universe Translation-en_AU             
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty/multiverse Translation-en_AU           
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-updates Release.gpg                    
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-updates/main Translation-en_AU         
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err http://au.archive.ubuntu.com feisty-updates/restricted Translation-en_AU   
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_AU
Get:2 http://medibuntu.sos-sts.com feisty Release.gpg [189B]
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_AU
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_AU
Ign http://security.ubuntu.com feisty-security/universe Translation-en_AU
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_AU
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_AU
Hit http://medibuntu.sos-sts.com feisty Release
Err http://medibuntu.sos-sts.com feisty Release
  
Hit http://security.ubuntu.com feisty-security Release
Get:3 http://medibuntu.sos-sts.com feisty Release [2195B]
Ign http://medibuntu.sos-sts.com feisty Release          
Hit http://security.ubuntu.com feisty-security/main Packages
Ign http://medibuntu.sos-sts.com feisty/free Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Fetched 2385B in 4s (518B/s)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_AU.bz2  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Reading package lists... Done
W: GPG error: http://medibuntu.sos-sts.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Any ideas coz I am stumped...

---

### Post by Seisen on 2007-07-25
Take the **au** out of all of your archives and then try it. For some reason they are down, actually they have been down since yesterday at least. For the mediubuntu key  here is how to get it.

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add
``` put that in the terminal.

---

### Post by RomeReactor on 2007-07-25
I think **Seinen** is right. You could try repositories from another place. (Just an example): Suppose you want  to use repositories from New Zealand, you again open the sources.list file in Gedit:
```
gksudo gedit /etc/apt/sources.list
```
go to **Search**->**Replace**, and in **Search for:** enter
```
au.
```
and in **Relpace with:** enter:
```
nz.
```
Then press **Replace All**. Save the file and close gedit, and:
```
sudo apt-get update
```

---

### Post by Demon Designs on 2007-07-25
OMG!!! U guys are amazing its perfectly working no errors WOW!!!

to prove it :P 
```
sidewinder@thomas-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sidewinder@thomas-desktop:~$ sudo apt-get update
Get:1 http://nz.archive.ubuntu.com feisty Release.gpg [191B]        
Ign http://nz.archive.ubuntu.com feisty/main Translation-en_AU              
Ign http://nz.archive.ubuntu.com feisty/restricted Translation-en_AU
Ign http://nz.archive.ubuntu.com feisty/universe Translation-en_AU
Ign http://nz.archive.ubuntu.com feisty/multiverse Translation-en_AU
Get:2 http://nz.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://nz.archive.ubuntu.com feisty-updates/main Translation-en_AU
Ign http://nz.archive.ubuntu.com feisty-updates/restricted Translation-en_AU
Hit http://nz.archive.ubuntu.com feisty Release                      
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B]  
Ign http://security.ubuntu.com feisty-security/main Translation-en_AU
Get:4 http://medibuntu.sos-sts.com feisty Release.gpg [189B]         
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_AU       
Hit http://nz.archive.ubuntu.com feisty-updates Release              
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_AU
Ign http://security.ubuntu.com feisty-security/universe Translation-en_AU
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_AU
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_AU
Hit http://medibuntu.sos-sts.com feisty Release
Hit http://nz.archive.ubuntu.com feisty/main Packages
Hit http://nz.archive.ubuntu.com feisty/restricted Packages
Hit http://nz.archive.ubuntu.com feisty/main Sources
Hit http://nz.archive.ubuntu.com feisty/restricted Sources
Hit http://nz.archive.ubuntu.com feisty/universe Packages
Hit http://nz.archive.ubuntu.com feisty/universe Sources
Hit http://nz.archive.ubuntu.com feisty/multiverse Packages
Hit http://nz.archive.ubuntu.com feisty/multiverse Sources
Hit http://security.ubuntu.com feisty-security Release
Ign http://medibuntu.sos-sts.com feisty/free Packages               
Hit http://nz.archive.ubuntu.com feisty-updates/main Packages
Hit http://nz.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://nz.archive.ubuntu.com feisty-updates/main Sources
Hit http://nz.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://security.ubuntu.com feisty-security/main Packages
Ign http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://medibuntu.sos-sts.com feisty/free Packages
Hit http://medibuntu.sos-sts.com feisty/non-free Packages
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Fetched 192B in 3s (58B/s)
Reading package lists... Done
sidewinder@thomas-desktop:~$ 

```

thnx here is a pic of my beryl upgrade its kinda gay... I havn't tried with the new updates just bout to do it when I post this but wow!!! thnx

piccy:
[img]http://img458.imageshack.us/img458/6646/screenshotjb9.png[/img] (that isn't my screen res i resized it for upload :))

---

### Post by RomeReactor on 2007-07-25
Glad you sorted it out!

---

### Post by Demon Designs on 2007-07-25
any ideas on how to fix my beryl upgrade just for thos interested my graphics card is a 'ATI radeon 9550' U can get all stats by googleing its name I am not to sure it works with buntu. I hav this card coz i got it for my xp and it worked i am just annoyed its screwing up for ubuntu 

any help is great!

---

### Post by skymera on 2007-07-25
how weird.
but at least its sorted :)

Thanks for helping him out

---

### Post by RomeReactor on 2007-07-25
First use Synaptic to completely remove Beryl. What are the problems you're having with it? do you have direct rendering?
```
glxinfo | grep rendering
```
if not, your video card must be properly set up before attempting to re-install Beryl. Also, Beryl is now being merged back into Compiz (now [Compiz Fusion]("http://www.opencompositing.org/")), so I suggest you wait until Gutsy Gibbon comes out in October which will include it.

---

### Post by Demon Designs on 2007-07-26
Yes I used that code i Hav dirrect rendering... I am using compiz fusion...
my problems are...:
- it has lines on the menu bars and on all windows(cannot see anyything)
... well thats bout it

---

### Post by skymera on 2007-07-26
turn as manty settings to low.
as that card is intergrated, and low power. i beliee

---

### Post by RomeReactor on 2007-07-26
I haven't used Compiz Fusion, so I really don't know how to advise you there. Note that as Compiz Fusion is rather new, it is bound to have many bugs. Perhaps [this thread]("http://ubuntuforums.org/showthread.php?t=499368") can help you with the display issue.

Also, [Freebird]("http://ubuntuforums.org/showpost.php?p=3065581&postcount=17") has the same card as you; perhaps he can help you there, so you should probably PM him. [Here's the thread]("http://ubuntuforums.org/showthread.php?p=3065769") where he posted.

---

