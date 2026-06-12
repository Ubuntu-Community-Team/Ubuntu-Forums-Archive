---
title: "Update-manager"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Vamp381 on 2007-07-27
I`m using ubuntu 7,04 three monts and this is first error that i got.
Presently when i stood i saw update icon and when i clicked to install update i got next error
[http://img514.imageshack.us/my.php?image=errorwd1.png](http://img514.imageshack.us/my.php?image=errorwd1.png)

Name of update that can`t be downloaded is gaim.
Please help :confused:

---

### Post by ugm6hr on 2007-07-27
Do you use GAIM? Or Pidgin? Or some other Messenger Client?

If so - how did you install it?  From repository, or not?

I don't recognise the IM system tray icon on your system (is it aMSN?)

---

### Post by isaacj87 on 2007-07-27
go to terminal and do this

```
sudo apt-get update -f
```

I think that's right...and it should correct your problem.

---

### Post by Vamp381 on 2007-07-27
I use Amsn only and i installed it via automatix,that is Amsn icon in tray,
I have gaim but don`t use it (i goth it when i installed ubuntu)
[http://img508.imageshack.us/my.php?image=error2dm8.png](http://img508.imageshack.us/my.php?image=error2dm8.png)

I entered that now update icon is gray,to wait ?

---

### Post by isaacj87 on 2007-07-27
Does the update manager work like usual now?

---

### Post by Vamp381 on 2007-07-27
Same error ;-<

when i enter in terminal sudo apt-get update -f  i get

```
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/Release  Unable to find expected entry  avant-window-navigatorp/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: http://hendrik.kaju.pri.ee feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: GPG error: http://packages.dfreer.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D4C9CD8F7572013D
W: GPG error: http://repository.debuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
W: Duplicate sources.list entry http://www.getautomatix.com feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntustudio.org feisty/main Packages (/var/lib/apt/lists/archive.ubuntustudio.org_ubuntustudio_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntustudio.org feisty/main Packages (/var/lib/apt/lists/archive.ubuntustudio.org_ubuntustudio_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://hendrik.kaju.pri.ee feisty/screenlets Packages (/var/lib/apt/lists/hendrik.kaju.pri.ee_ubuntu_dists_feisty_screenlets_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by moffa on 2007-07-27
> **Vamp381 said:**
> Same error ;-<

when i enter in terminal sudo apt-get update -f  i get

```
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/Release  Unable to find expected entry  avant-window-navigatorp/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: http://hendrik.kaju.pri.ee feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: GPG error: http://packages.dfreer.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D4C9CD8F7572013D
W: GPG error: http://repository.debuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
W: Duplicate sources.list entry http://www.getautomatix.com feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntustudio.org feisty/main Packages (/var/lib/apt/lists/archive.ubuntustudio.org_ubuntustudio_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntustudio.org feisty/main Packages (/var/lib/apt/lists/archive.ubuntustudio.org_ubuntustudio_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://hendrik.kaju.pri.ee feisty/screenlets Packages (/var/lib/apt/lists/hendrik.kaju.pri.ee_ubuntu_dists_feisty_screenlets_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

The first two entries have to do with a server side issue.  The GPG errors are because you do not have the signed keys for the repositories.  You don't have to install them but it is recommended.  The duplicate entry errors are because you have those servers more than once in your /etc/apt/sources.list or in /var/lib/apt/lists/ folder.  I think if you clean out the /var/lib/apt/lists folder of those entries (eg. [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty/screenlets) it should be okay.

---

### Post by ugm6hr on 2007-07-27
I think this is something to do with Automatix.  

I have not used Automatix, and there is no such package (gaim version 1:2.0.2-0ubuntu1) in my Update Manager.  I use Gaim, and my Update Manager lists your currently installed version as the most recent.

I suspect the Automatix repo is off-line at the moment, so Ubuntu can't install the "update".

You don't need it (you don't use Gaim, and the update isn't necessary anyway) - so just unselect the update that isn't working.  Also - make sure you click the "Check" button before installing anything.

And I am assuming you have read the various (conflicting) posts about Automatix making a mess of Ubuntu installations...

---

### Post by isaacj87 on 2007-07-27
> **ugm6hr said:**
> I think this is something to do with Automatix.  

I have not used Automatix, and there is no such package (gaim version 1:2.0.2-0ubuntu1) in my Update Manager.  I use Gaim, and my Update Manager lists your currently installed version as the most recent.

I suspect the Automatix repo is off-line at the moment, so Ubuntu can't install the "update".

You don't need it (you don't use Gaim, and the update isn't necessary anyway) - so just unselect the update that isn't working.  Also - make sure you click the "Check" button before installing anything.

And I am assuming you have read the various (conflicting) posts about Automatix making a mess of Ubuntu installations...

Yeah, I agree...the repo must be down...I only use Automatix when I really have to (aka laziness)...

---

### Post by Vamp381 on 2007-07-27
H0w to clean it via root or via terminal (/var/lib/apt/lists).
Thanks.

---

### Post by ugm6hr on 2007-07-27
> **Vamp381 said:**
> H0w to clean it via root or via terminal (/var/lib/apt/lists).
Thanks.
Sorry, I don't understand this...  What are you trying to clean?  And what exactly do you mean by clean?

---

### Post by isaacj87 on 2007-07-27
I'm guessing he means to remove some of the sources that don't work or something??

---

### Post by Vamp381 on 2007-07-27
/var/lib/apt/lists That to clean from duplicated files

```
W: Duplicate sources.list entry http://www.getautomatix.com feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com feisty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntustudio.org feisty/main Packages (/var/lib/apt/lists/archive.ubuntustudio.org_ubuntustudio_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntustudio.org feisty/main Packages (/var/lib/apt/lists/archive.ubuntustudio.org_ubuntustudio_dists_feisty_main_binary-i386_Packages)
W: Duplicate sources.list entry http://hendrik.kaju.pri.ee feisty/screenlets Packages (/var/lib/apt/lists/hendrik.kaju.pri.ee_ubuntu_dists_feisty_screenlets_binary-i386_Packages)
```

---

### Post by Seisen on 2007-07-27
Post your source list by putting this in the terminal.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by isaacj87 on 2007-07-27
I would just go to terminal:

sudo gedit /etc/apt/sources.list

and locate the doubles and delete.

---

### Post by ugm6hr on 2007-07-27
> **Vamp381 said:**
> /var/lib/apt/lists That to clean from duplicated files
I think it is probably Automatix that has added unnecessary entries here... Have a look yourself:

```
gedit /etc/apt/sources.list
```

[COLOR="Red"]**Be very careful editing this manually - it can break Synaptic**[/COLOR]

Despite this, if you want to do it:

```
gksudo gedit /etc/apt/sources.list
```

EDIT: Post the output from the first command here, so that the community can advise on what to delete.

---

### Post by Seisen on 2007-07-27
That's why we are going to tell him what to remove so his source list doesn't get messed up.

---

### Post by Vamp381 on 2007-07-27
```
deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigatorp

deb http://gandalfn.club.fr/ubuntu edgy dev

deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator

deb http://ubuntu.beryl-project.org feisty main

deb http://wine.lowvoice.nl/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb http://packages.dfreer.org feisty main
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb http://www.getautomatix.com/apt feisty main
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb  http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse
```

That are my source list.

---

### Post by Seisen on 2007-07-27
You can remove these I put the one's to remove in bold

```
deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigatorp

deb http://gandalfn.club.fr/ubuntu edgy dev

deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator

deb http://ubuntu.beryl-project.org feisty main

deb http://wine.lowvoice.nl/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse 

#Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse 

#Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse 

#Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb http://packages.dfreer.org feisty main
[B]deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb http://www.getautomatix.com/apt feisty main[/B]
[B]deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://archive.ubuntustudio.org/ubuntustudio feisty main[/B]
deb  http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse
```

Once you remove those do a 
```
sudo apt-get update
``` and let us know what happened.

---

### Post by Vamp381 on 2007-07-27
```
pavle@pavlee:~$ sudo apt-get update
Get:1 http://wine.lowvoice.nl feisty Release.gpg [191B]                        
Ign http://wine.lowvoice.nl feisty/main Translation-en_US                      
Get:2 http://repository.debuntu.org feisty Release.gpg [189B]                  
Get:3 http://wine.budgetdedicated.com feisty Release.gpg [191B]                
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US              
Get:4 http://archive.canonical.com feisty-commercial Release.gpg [191B]        
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US      
Get:5 http://download.tuxfamily.org feisty Release.gpg [189B]                  
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Get:6 http://www.getautomatix.com feisty Release.gpg [189B]                    
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Get:7 http://archive.ubuntu.com feisty-backports Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US          
Ign http://ubuntu.beryl-project.org feisty Release.gpg                         
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_US              
Hit http://wine.lowvoice.nl feisty Release                                     
Ign http://ubuntu.beryl-project.org feisty Release                             
Get:8 http://hendrik.kaju.pri.ee feisty Release.gpg [189B]                     
Ign http://hendrik.kaju.pri.ee feisty/screenlets Translation-en_US             
Ign http://wine.lowvoice.nl feisty/main Packages                               
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US    
Get:9 http://archive.ubuntu.com feisty-updates Release.gpg [191B]              
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US            
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US      
Hit http://wine.budgetdedicated.com feisty Release                             
Ign http://ubuntu.beryl-project.org feisty/main Packages                       
Hit http://archive.canonical.com feisty-commercial Release                     
Hit http://download.tuxfamily.org feisty Release                               
Hit http://hendrik.kaju.pri.ee feisty Release                                  
Hit http://wine.lowvoice.nl feisty/main Packages                               
Err http://hendrik.kaju.pri.ee feisty Release                                  
  
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US      
Get:10 http://archive.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US           
Ign http://wine.budgetdedicated.com feisty/main Packages                       
Err http://ubuntu.beryl-project.org feisty/main Packages                       
  404 Not Found [IP: 80.77.247.17 80]
Get:11 http://hendrik.kaju.pri.ee feisty Release [6906B]                       
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US       
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US     
Hit http://www.getautomatix.com feisty Release                                 
Get:12 http://archive.ubuntu.com feisty Release.gpg [191B]                     
Ign http://archive.ubuntu.com feisty/main Translation-en_US                    
Ign http://archive.ubuntu.com feisty/restricted Translation-en_US              
Hit http://wine.budgetdedicated.com feisty/main Sources                        
Ign http://archive.ubuntu.com feisty/universe Translation-en_US                
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com feisty/main Translation-en_US                    
Hit http://archive.ubuntu.com feisty-backports Release                         
Hit http://archive.ubuntu.com feisty-updates Release                           
Hit http://archive.ubuntu.com feisty-security Release                          
Hit http://archive.canonical.com feisty-commercial/main Packages               
Hit http://wine.budgetdedicated.com feisty/main Packages                       
Get:13 http://gandalfn.club.fr edgy Release.gpg [189B]                         
Ign http://gandalfn.club.fr edgy/dev Translation-en_US                         
Hit http://archive.ubuntu.com feisty Release                                   
Get:14 http://packages.dfreer.org feisty Release.gpg [189B]                    
Ign http://packages.dfreer.org feisty/main Translation-en_US                   
Hit http://archive.ubuntu.com feisty-backports/main Packages                   
Hit http://archive.ubuntu.com feisty-backports/restricted Packages             
Hit http://archive.ubuntu.com feisty-backports/universe Packages               
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages             
Hit http://archive.ubuntu.com feisty-backports/main Sources                    
Ign http://repository.debuntu.org feisty/multiverse Translation-en_US          
Hit http://archive.ubuntu.com feisty-backports/restricted Sources              
Hit http://archive.ubuntu.com feisty-backports/universe Sources                
Get:15 http://www.getautomatix.com feisty/main Packages [10.6kB]               
99% [15 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Err http://www.getautomatix.com feisty/main Packages                           
  Sub-process bzip2 returned an error code (2)
Hit http://gandalfn.club.fr edgy Release                                       
Hit http://archive.ubuntu.com feisty-backports/multiverse Sources              
Hit http://archive.ubuntu.com feisty-updates/main Packages                     
Hit http://archive.ubuntu.com feisty-updates/restricted Packages               
Hit http://archive.ubuntu.com feisty-updates/universe Packages                 
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages               
Hit http://archive.ubuntu.com feisty-updates/main Sources                      
Hit http://archive.ubuntu.com feisty-updates/restricted Sources                
Hit http://archive.ubuntu.com feisty-updates/universe Sources                  
Hit http://repository.debuntu.org feisty Release                               
Err http://repository.debuntu.org feisty Release                               
  
Hit http://archive.ubuntu.com feisty-updates/multiverse Sources                
Hit http://archive.ubuntu.com feisty-security/main Packages                    
Hit http://archive.ubuntu.com feisty-security/restricted Packages              
Hit http://archive.ubuntu.com feisty-security/universe Packages                
Hit http://archive.ubuntu.com feisty-security/multiverse Packages              
Hit http://archive.ubuntu.com feisty-security/main Sources                     
Hit http://archive.ubuntu.com feisty-security/restricted Sources               
Hit http://gandalfn.club.fr edgy/dev Packages                                  
Hit http://archive.ubuntu.com feisty-security/universe Sources                 
Hit http://archive.ubuntu.com feisty-security/multiverse Sources               
Ign http://hendrik.kaju.pri.ee feisty Release                                  
Get:16 http://archive.ubuntustudio.org feisty Release.gpg [189B]               
Ign http://archive.ubuntustudio.org feisty/main Translation-en_US              
Get:17 http://repository.debuntu.org feisty Release [2176B]                    
Hit http://archive.ubuntu.com feisty/main Packages                             
Hit http://hendrik.kaju.pri.ee feisty/screenlets Packages                      
Hit http://archive.ubuntustudio.org feisty Release                             
Hit http://archive.ubuntustudio.org feisty/main Packages                       
Hit http://packages.dfreer.org feisty Release                                  
Err http://packages.dfreer.org feisty Release                                  
  
Hit http://archive.ubuntu.com feisty/restricted Packages                       
Hit http://archive.ubuntu.com feisty/universe Packages                         
Hit http://archive.ubuntu.com feisty/multiverse Packages                       
Hit http://archive.ubuntu.com feisty/main Sources                              
Hit http://archive.ubuntu.com feisty/restricted Sources                        
Hit http://archive.ubuntu.com feisty/universe Sources                          
Hit http://archive.ubuntu.com feisty/multiverse Sources                        
Hit http://archive.ubuntu.com feisty/main Packages                             
Get:18 http://packages.dfreer.org feisty Release [10.3kB]                      
Ign http://packages.dfreer.org feisty Release                                  
Ign http://repository.debuntu.org feisty Release                               
Hit http://packages.dfreer.org feisty/main Packages                            
Hit http://repository.debuntu.org feisty/multiverse Packages                   
Hit http://repository.debuntu.org feisty/multiverse Sources                    
Fetched 19.9kB in 15s (1261B/s)                                                
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/Release  Unable to find expected entry  avant-window-navigatorp/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz  404 Not Found [IP: 80.77.247.17 80]
Failed to fetch http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)
Reading package lists... Done
W: GPG error: http://hendrik.kaju.pri.ee feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7
W: GPG error: http://packages.dfreer.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D4C9CD8F7572013D
W: GPG error: http://repository.debuntu.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29
W: Duplicate sources.list entry http://archive.ubuntu.com feisty/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
pavle@pavlee:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

---

### Post by frodon on 2007-07-27
Please refer to the automatix forum for automatix issues, this is where you are more likely to get good automatix help, as we don't know what automatix did we can't help you in an efficient way :
[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

---

### Post by Seisen on 2007-07-27
Here are the gpg keys you neeed
```
wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add -
```

```
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add 
```

```
wget http://repository.debuntu.org/GPG-Key-chantra.txt -O- | sudo apt-key add - 
```

---

### Post by Seisen on 2007-07-27
> **frodon said:**
> Please refer to the automatix forum for automatix issues, this is where you are more likely to get good automatix help, as we don't know what automatix did we can't help you in an efficient way :
[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

This has nothing to do with Automatix, it has to do with his source list.

---

### Post by frodon on 2007-07-27
> **Seisen said:**
> This has nothing to do with Automatix, it has to do with his source list.And guess what automatix modifies ...

---

### Post by Seisen on 2007-07-27
I understand that ***_but_*** that was not what cause his problem.

---

### Post by Seisen on 2007-07-27
I noticed some other things also. Delete the "p" that is in bold and Comment out the lines i put in bold and the run ```
sudo apt-get update
```
```
[B]deb http://www.getautomatix.com/apt feisty main
[/B]
#AUTOMATIX REPOS START
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator**p**

deb http://gandalfn.club.fr/ubuntu edgy dev

deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator

deb http://ubuntu.beryl-project.org feisty main

deb http://wine.lowvoice.nl/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse 

#Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse 

#Added by software-properties

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse 

#Added by software-properties
[B]
deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse[/B]
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse #Added by software-properties
#AUTOMATIX REPOS END
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb http://packages.dfreer.org feisty main
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets
deb http://www.getautomatix.com/apt feisty main
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb  http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse
```

---

### Post by Vamp381 on 2007-07-27
When i enter this 
```
 wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add
```

i get ```
gpg: can't open `': No such file or directory
--15:59:31--  http://packages.dfreer.org/7572013D.gpg
           => `-'
Resolving packages.dfreer.org... 66.209.138.18
Connecting to packages.dfreer.org|66.209.138.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,718 (1.7K) [text/plain]

 0% [                                     ] 0             --.--K/s             


Cannot write to `7572013D.gpg' (Broken pipe).

```


this i get when i enter sudo apt-get update
```
pavle@pavlee:~$ sudo apt-get updateGet:1 http://wine.budgetdedicated.com feisty Release.gpg [191B]
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US
Get:2 http://repository.debuntu.org feisty Release.gpg [189B]                  
Ign http://ubuntu.beryl-project.org feisty Release.gpg                         
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_US              
Get:3 http://wine.lowvoice.nl feisty Release.gpg [191B]                        
Ign http://wine.lowvoice.nl feisty/main Translation-en_US                      
Get:4 http://archive.canonical.com feisty-commercial Release.gpg [191B]        
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US      
Get:5 http://gandalfn.club.fr edgy Release.gpg [189B]                          
Ign http://gandalfn.club.fr edgy/dev Translation-en_US                         
Get:6 http://hendrik.kaju.pri.ee feisty Release.gpg [189B]                     
Ign http://hendrik.kaju.pri.ee feisty/screenlets Translation-en_US             
Get:7 http://archive.ubuntu.com feisty-backports Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US          
Hit http://wine.budgetdedicated.com feisty Release                             
Ign http://ubuntu.beryl-project.org feisty Release                             
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US    
Get:8 http://archive.ubuntu.com feisty-updates Release.gpg [191B]              
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US            
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US      
Ign http://repository.debuntu.org feisty/multiverse Translation-en_US          
Ign http://ubuntu.beryl-project.org feisty/main Packages                       
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US      
Get:9 http://archive.ubuntu.com feisty-security Release.gpg [191B]             
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US           
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US     
Get:10 http://www.getautomatix.com feisty Release.gpg [189B]                   
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Hit http://wine.lowvoice.nl feisty Release                                     
Err http://ubuntu.beryl-project.org feisty/main Packages                       
  404 Not Found [IP: 80.77.247.17 80]
Hit http://hendrik.kaju.pri.ee feisty Release                                  
Hit http://repository.debuntu.org feisty Release                               
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US       
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US     
Get:11 http://archive.ubuntu.com feisty Release.gpg [191B]                     
Ign http://archive.ubuntu.com feisty/main Translation-en_US                    
Ign http://archive.ubuntu.com feisty/restricted Translation-en_US              
Ign http://archive.ubuntu.com feisty/universe Translation-en_US                
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com feisty/main Translation-en_US                    
Ign http://wine.lowvoice.nl feisty/main Packages                               
Hit http://hendrik.kaju.pri.ee feisty/screenlets Packages                      
Hit http://archive.ubuntu.com feisty-backports Release                         
Hit http://archive.ubuntu.com feisty-updates Release                           
Hit http://repository.debuntu.org feisty/multiverse Packages                   
Get:12 http://packages.dfreer.org feisty Release.gpg [189B]                    
Ign http://packages.dfreer.org feisty/main Translation-en_US                   
Hit http://archive.ubuntu.com feisty-security Release                          
Hit http://archive.ubuntu.com feisty Release                                   
Hit http://archive.ubuntu.com feisty-backports/main Packages                   
Hit http://archive.ubuntu.com feisty-backports/restricted Packages             
Hit http://archive.ubuntu.com feisty-backports/universe Packages               
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages             
Hit http://packages.dfreer.org feisty Release                                  
Err http://packages.dfreer.org feisty Release                                  
  
Hit http://repository.debuntu.org feisty/multiverse Sources                    
Hit http://archive.ubuntu.com feisty-backports/main Sources                    
Hit http://archive.ubuntu.com feisty-backports/restricted Sources              
Hit http://archive.ubuntu.com feisty-backports/universe Sources                
Hit http://archive.ubuntu.com feisty-backports/multiverse Sources              
Hit http://archive.ubuntu.com feisty-updates/main Packages                     
Hit http://archive.ubuntu.com feisty-updates/restricted Packages               
Get:13 http://packages.dfreer.org feisty Release [10.3kB]                      
Hit http://gandalfn.club.fr edgy Release                                       
Get:14 http://download.tuxfamily.org feisty Release.gpg [189B]                 
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Hit http://archive.ubuntu.com feisty-updates/universe Packages                 
Hit http://download.tuxfamily.org feisty Release                               
Hit http://archive.canonical.com feisty-commercial Release                     
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages               
Hit http://archive.ubuntu.com feisty-updates/main Sources                      
Hit http://archive.ubuntu.com feisty-updates/restricted Sources                
Hit http://archive.canonical.com feisty-commercial/main Packages               
Ign http://packages.dfreer.org feisty Release                                  
Hit http://packages.dfreer.org feisty/main Packages                            
Hit http://archive.ubuntu.com feisty-updates/universe Sources                  
Hit http://archive.ubuntu.com feisty-updates/multiverse Sources                
Hit http://archive.ubuntu.com feisty-security/main Packages                    
Hit http://archive.ubuntu.com feisty-security/restricted Packages              
Hit http://archive.ubuntu.com feisty-security/universe Packages                
Hit http://archive.ubuntu.com feisty-security/multiverse Packages              
Hit http://archive.ubuntu.com feisty-security/main Sources                     
Hit http://archive.ubuntu.com feisty-security/restricted Sources               
Hit http://archive.ubuntu.com feisty-security/universe Sources                 
Hit http://archive.ubuntu.com feisty-security/multiverse Sources               
Hit http://wine.lowvoice.nl feisty/main Packages                               
Hit http://archive.ubuntu.com feisty/main Packages                             
Hit http://archive.ubuntu.com feisty/restricted Packages                       
Hit http://archive.ubuntu.com feisty/universe Packages                         
Hit http://archive.ubuntu.com feisty/multiverse Packages                       
Hit http://archive.ubuntu.com feisty/main Sources                              
Hit http://archive.ubuntu.com feisty/restricted Sources                        
Hit http://archive.ubuntu.com feisty/universe Sources                          
Hit http://archive.ubuntu.com feisty/multiverse Sources                        
Hit http://archive.ubuntu.com feisty/main Packages                             
Get:15 http://archive.ubuntustudio.org feisty Release.gpg [189B]               
Ign http://archive.ubuntustudio.org feisty/main Translation-en_US              
Hit http://archive.ubuntustudio.org feisty Release                             
Ign http://wine.budgetdedicated.com feisty/main Packages                       
Hit http://www.getautomatix.com feisty Release                                 
Hit http://wine.budgetdedicated.com feisty/main Sources                        
Hit http://gandalfn.club.fr edgy/dev Packages                                  
Hit http://wine.budgetdedicated.com feisty/main Packages             
Hit http://archive.ubuntustudio.org feisty/main Packages                       
Hit http://www.getautomatix.com feisty/main Packages                           
Fetched 10.5kB in 7s (1312B/s)                                                 
Failed to fetch http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz  404 Not Found [IP: 80.77.247.17 80]
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/Release  Unable to find expected entry  avant-window-navigatorp/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
W: GPG error: http://packages.dfreer.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D4C9CD8F7572013D
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
I will delete that now deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

---

### Post by Seisen on 2007-07-27
> **Vamp381 said:**
> When i enter this 
```
 wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add
```

i get ```
gpg: can't open `': No such file or directory
--15:59:31--  http://packages.dfreer.org/7572013D.gpg
           => `-'
Resolving packages.dfreer.org... 66.209.138.18
Connecting to packages.dfreer.org|66.209.138.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,718 (1.7K) [text/plain]

 0% [                                     ] 0             --.--K/s             


Cannot write to `7572013D.gpg' (Broken pipe).

```


this i get when i enter sudo apt-get update
```
pavle@pavlee:~$ sudo apt-get updateGet:1 http://wine.budgetdedicated.com feisty Release.gpg [191B]
Ign http://wine.budgetdedicated.com feisty/main Translation-en_US
Get:2 http://repository.debuntu.org feisty Release.gpg [189B]                  
Ign http://ubuntu.beryl-project.org feisty Release.gpg                         
Ign http://ubuntu.beryl-project.org feisty/main Translation-en_US              
Get:3 http://wine.lowvoice.nl feisty Release.gpg [191B]                        
Ign http://wine.lowvoice.nl feisty/main Translation-en_US                      
Get:4 http://archive.canonical.com feisty-commercial Release.gpg [191B]        
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US      
Get:5 http://gandalfn.club.fr edgy Release.gpg [189B]                          
Ign http://gandalfn.club.fr edgy/dev Translation-en_US                         
Get:6 http://hendrik.kaju.pri.ee feisty Release.gpg [189B]                     
Ign http://hendrik.kaju.pri.ee feisty/screenlets Translation-en_US             
Get:7 http://archive.ubuntu.com feisty-backports Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US          
Hit http://wine.budgetdedicated.com feisty Release                             
Ign http://ubuntu.beryl-project.org feisty Release                             
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US    
Get:8 http://archive.ubuntu.com feisty-updates Release.gpg [191B]              
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US            
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US      
Ign http://repository.debuntu.org feisty/multiverse Translation-en_US          
Ign http://ubuntu.beryl-project.org feisty/main Packages                       
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US      
Get:9 http://archive.ubuntu.com feisty-security Release.gpg [191B]             
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US           
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US     
Get:10 http://www.getautomatix.com feisty Release.gpg [189B]                   
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Hit http://wine.lowvoice.nl feisty Release                                     
Err http://ubuntu.beryl-project.org feisty/main Packages                       
  404 Not Found [IP: 80.77.247.17 80]
Hit http://hendrik.kaju.pri.ee feisty Release                                  
Hit http://repository.debuntu.org feisty Release                               
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US       
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US     
Get:11 http://archive.ubuntu.com feisty Release.gpg [191B]                     
Ign http://archive.ubuntu.com feisty/main Translation-en_US                    
Ign http://archive.ubuntu.com feisty/restricted Translation-en_US              
Ign http://archive.ubuntu.com feisty/universe Translation-en_US                
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com feisty/main Translation-en_US                    
Ign http://wine.lowvoice.nl feisty/main Packages                               
Hit http://hendrik.kaju.pri.ee feisty/screenlets Packages                      
Hit http://archive.ubuntu.com feisty-backports Release                         
Hit http://archive.ubuntu.com feisty-updates Release                           
Hit http://repository.debuntu.org feisty/multiverse Packages                   
Get:12 http://packages.dfreer.org feisty Release.gpg [189B]                    
Ign http://packages.dfreer.org feisty/main Translation-en_US                   
Hit http://archive.ubuntu.com feisty-security Release                          
Hit http://archive.ubuntu.com feisty Release                                   
Hit http://archive.ubuntu.com feisty-backports/main Packages                   
Hit http://archive.ubuntu.com feisty-backports/restricted Packages             
Hit http://archive.ubuntu.com feisty-backports/universe Packages               
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages             
Hit http://packages.dfreer.org feisty Release                                  
Err http://packages.dfreer.org feisty Release                                  
  
Hit http://repository.debuntu.org feisty/multiverse Sources                    
Hit http://archive.ubuntu.com feisty-backports/main Sources                    
Hit http://archive.ubuntu.com feisty-backports/restricted Sources              
Hit http://archive.ubuntu.com feisty-backports/universe Sources                
Hit http://archive.ubuntu.com feisty-backports/multiverse Sources              
Hit http://archive.ubuntu.com feisty-updates/main Packages                     
Hit http://archive.ubuntu.com feisty-updates/restricted Packages               
Get:13 http://packages.dfreer.org feisty Release [10.3kB]                      
Hit http://gandalfn.club.fr edgy Release                                       
Get:14 http://download.tuxfamily.org feisty Release.gpg [189B]                 
Ign http://download.tuxfamily.org feisty/avant-window-navigator Translation-en_US
Hit http://archive.ubuntu.com feisty-updates/universe Packages                 
Hit http://download.tuxfamily.org feisty Release                               
Hit http://archive.canonical.com feisty-commercial Release                     
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages               
Hit http://archive.ubuntu.com feisty-updates/main Sources                      
Hit http://archive.ubuntu.com feisty-updates/restricted Sources                
Hit http://archive.canonical.com feisty-commercial/main Packages               
Ign http://packages.dfreer.org feisty Release                                  
Hit http://packages.dfreer.org feisty/main Packages                            
Hit http://archive.ubuntu.com feisty-updates/universe Sources                  
Hit http://archive.ubuntu.com feisty-updates/multiverse Sources                
Hit http://archive.ubuntu.com feisty-security/main Packages                    
Hit http://archive.ubuntu.com feisty-security/restricted Packages              
Hit http://archive.ubuntu.com feisty-security/universe Packages                
Hit http://archive.ubuntu.com feisty-security/multiverse Packages              
Hit http://archive.ubuntu.com feisty-security/main Sources                     
Hit http://archive.ubuntu.com feisty-security/restricted Sources               
Hit http://archive.ubuntu.com feisty-security/universe Sources                 
Hit http://archive.ubuntu.com feisty-security/multiverse Sources               
Hit http://wine.lowvoice.nl feisty/main Packages                               
Hit http://archive.ubuntu.com feisty/main Packages                             
Hit http://archive.ubuntu.com feisty/restricted Packages                       
Hit http://archive.ubuntu.com feisty/universe Packages                         
Hit http://archive.ubuntu.com feisty/multiverse Packages                       
Hit http://archive.ubuntu.com feisty/main Sources                              
Hit http://archive.ubuntu.com feisty/restricted Sources                        
Hit http://archive.ubuntu.com feisty/universe Sources                          
Hit http://archive.ubuntu.com feisty/multiverse Sources                        
Hit http://archive.ubuntu.com feisty/main Packages                             
Get:15 http://archive.ubuntustudio.org feisty Release.gpg [189B]               
Ign http://archive.ubuntustudio.org feisty/main Translation-en_US              
Hit http://archive.ubuntustudio.org feisty Release                             
Ign http://wine.budgetdedicated.com feisty/main Packages                       
Hit http://www.getautomatix.com feisty Release                                 
Hit http://wine.budgetdedicated.com feisty/main Sources                        
Hit http://gandalfn.club.fr edgy/dev Packages                                  
Hit http://wine.budgetdedicated.com feisty/main Packages             
Hit http://archive.ubuntustudio.org feisty/main Packages                       
Hit http://www.getautomatix.com feisty/main Packages                           
Fetched 10.5kB in 7s (1312B/s)                                                 
Failed to fetch http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz  404 Not Found [IP: 80.77.247.17 80]
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/Release  Unable to find expected entry  avant-window-navigatorp/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
W: GPG error: http://packages.dfreer.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D4C9CD8F7572013D
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```
I will delete that now deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

What I meant was to put a # in front of the repo so it looks like this that is what I meant by commenting out the repo.

```
#deb http://www.getautomatix.com/apt feisty main
```

try this for the key

```
 wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add - 
```

---

### Post by Vamp381 on 2007-07-27
Key worked now.

```
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/Release  Unable to find expected entry  avant-window-navigatorp/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch http://ubuntu.beryl-project.org/dists/feisty/main/binary-i386/Packages.gz  404 Not Found [IP: 80.77.247.17 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

That is what last get when i enter sudo apt-get update. BTW update-manager downloaded updates for wensoth,but not for gaim,now icon in tray dissapered

---

### Post by Seisen on 2007-07-27
Did you comment out this line?

```
deb http://ubuntu.beryl-project.org feisty main
``` and remove the 'p" from the end of this repo?

```
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigatorp
```

---

### Post by eentonig on 2007-07-27
> **Seisen said:**
> I understand that ***_but_*** that was not what cause his problem.

I haven't checked. But which repo is proposing the newer Gaim client to install?

Anyway, even if it's not automatix, that's why I don't use it. You're repo's get updated and you don't know what they are offering. (Same goes for most other *untrusted* repo's by the way.)

---

### Post by Seisen on 2007-07-27
> **eentonig said:**
> I haven't checked. But which repo is proposing the newer Gaim client to install?

Anyway, even if it's not automatix, that's why I don't use it. You're repo's get updated and you don't know what they are offering. (Same goes for most other *untrusted* repo's by the way.)

Whichever repo it was it was upgrading Gaim to Pidgen.

---

### Post by Vamp381 on 2007-07-27
i goth now when i enter apt-get update i goth this error.

```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

---

### Post by victor9098 on 2007-07-27
Hello All,

I do not want to go off topic, but I have a similar problem as listed earlier, I am getting the following error:

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A
W: You may want to run apt-get update to correct these problems

Could you please walk me through what I should next?

Thank you.

---

### Post by Seisen on 2007-07-27
You need to add the key, put this in the terminal

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

---

### Post by Seisen on 2007-07-27
> **Vamp381 said:**
> i goth now when i enter apt-get update i goth this error.

```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

Did you put it in as ```
sudo apt-get update
``` or do you have update-manager or synaptic open, if you do you need to close them down.

---

### Post by Vamp381 on 2007-07-27
Seisen thank you (-; problem fixed.

---

### Post by victor9098 on 2007-07-27
I got this in my terminal window:

keith@keith-laptop:~$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
Password:--17:38:36--  [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,180 (4.1K) [text/plain]

100%[====================================>] 4,180          4.08K/s             

17:38:38 (4.08 KB/s) - `-' saved [4180/4180]

Now the cursor is just blinking...do I just close?

---

### Post by Seisen on 2007-07-27
> **victor9098 said:**
> I got this in my terminal window:

keith@keith-laptop:~$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
Password:--17:38:36--  [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,180 (4.1K) [text/plain]

100%[====================================>] 4,180          4.08K/s             

17:38:38 (4.08 KB/s) - `-' saved [4180/4180]

Now the cursor is just blinking...do I just close?


It should close by it's self, hmm....Close it out and then run ```
sud apt-get update
``` and shouldn't have any more problems.

---

### Post by victor9098 on 2007-07-27
Closed the terminal window.

Ran the previous command again...this time it finished with "OK"

Closed window. Opened Terminal again, did sudo apt-get update, but the error appeared again.

Restarted computer.

Opened Terminal, sudo apt-get update...still end up with:

W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A
W: You may want to run apt-get update to correct these problems

Does it look terminal? :)

---

