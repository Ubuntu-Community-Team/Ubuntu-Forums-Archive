---
title: "Triple Boot Attempt - Mavericks/Windows 8/Ubuntu 14.04"
date: 2014-04-21
forum: Apple Hardware Users
---

### Post by Xfilers on 2014-04-21
Hi all...

New Ubuntu user here and i am attempting to triple boot on a Macbook pro.  But, running into some problems using boot-repair.

I followed oldfred's fix for changing getting boot-repair to work by chaning trusty to saucy, but when boot-repair tells to please typer the following: in the popup window, i get an error. Unable to locate package linux


Now please type (or copy-paste) the following command in terminal:
sudo apt-get install -y --force-yes grub-pc linux

Thanks in advance!
Rob

```

rob@Northstar:~$ sudo apt-get install -y --force-yes grub-pc linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux

```

Changing trusty to saucy:

```



rob@Northstar:~$  sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
[sudo] password for rob: 
 Simple tool to repair frequent boot problems.

Website: https://launchpad.net/boot-repair
 More info: https://launchpad.net/~yannubuntu/+archive/boot-repair
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmptw2v9n84/secring.gpg' created
gpg: keyring `/tmp/tmptw2v9n84/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmptw2v9n84/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://us.archive.ubuntu.com trusty InRelease                                              
Ign http://us.archive.ubuntu.com trusty-updates InRelease                                       
Hit http://security.ubuntu.com trusty-security Release.gpg                                      
Ign http://extras.ubuntu.com trusty InRelease                        
Hit http://security.ubuntu.com trusty-security Release               
Ign http://us.archive.ubuntu.com trusty-backports InRelease          
Ign http://ppa.launchpad.net trusty InRelease  
Hit http://us.archive.ubuntu.com trusty Release.gpg                                         
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]                       
Hit http://security.ubuntu.com trusty-security/main Sources                                           
Hit http://extras.ubuntu.com trusty Release.gpg                      
Ign http://ppa.launchpad.net trusty Release.gpg                      
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg        
Hit http://security.ubuntu.com trusty-security/restricted Sources    
Hit http://security.ubuntu.com trusty-security/universe Sources      
Hit http://us.archive.ubuntu.com trusty Release                      
Hit http://extras.ubuntu.com trusty Release                                                                    
Ign http://ppa.launchpad.net trusty Release                                                                    
Get:2 http://us.archive.ubuntu.com trusty-updates Release [58.5 kB]  
Hit http://security.ubuntu.com trusty-security/multiverse Sources                                  
Hit http://security.ubuntu.com trusty-security/main amd64 Packages                                 
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com trusty-backports Release                                                      
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages                      
Hit http://extras.ubuntu.com trusty/main amd64 Packages                                                        
Hit http://us.archive.ubuntu.com trusty/main Sources                                        
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted Sources                                  
Hit http://security.ubuntu.com trusty-security/main i386 Packages                           
Hit http://extras.ubuntu.com trusty/main i386 Packages                
Hit http://us.archive.ubuntu.com trusty/universe Sources              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse Sources            
Hit http://security.ubuntu.com trusty-security/universe i386 Packages 
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                                 
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages     
Hit http://security.ubuntu.com trusty-security/main Translation-en    
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages       
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com trusty/main i386 Packages            
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages      
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages        
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages      
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://us.archive.ubuntu.com trusty/main Translation-en           
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en     
Ign http://extras.ubuntu.com trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty/universe Translation-en       
Get:3 http://us.archive.ubuntu.com trusty-updates/main Sources [2,774 B]
Ign http://extras.ubuntu.com trusty/main Translation-en                                               
Get:4 http://us.archive.ubuntu.com trusty-updates/restricted Sources [14 B]                 
Get:5 http://us.archive.ubuntu.com trusty-updates/universe Sources [648 B]                  
Get:6 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [1,790 B]              
Get:7 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [9,544 B]             
Ign http://security.ubuntu.com trusty-security/main Translation-en_US                        
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Get:9 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [1,602 B]          
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US                  
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [6,362 B]
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US                     
Get:11 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [8,160 B]
Err http://ppa.launchpad.net trusty/main amd64 Packages                 
  404  Not Found
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Err http://ppa.launchpad.net trusty/main i386 Packages                  
  404  Not Found
Get:13 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [1,601 B]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [6,386 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en     
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                                                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US                                           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US                                           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US                                             
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US                                         
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US                                   
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US                                   
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US                                     
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US                                       
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US                                 
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US                                 
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US                                   
Fetched 98.4 kB in 8s (11.4 kB/s)                                                                              
W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
rob@Northstar:~$ sudo apt-get install -y boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair
rob@Northstar:~$ gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu
rob@Northstar:~$ ^C
rob@Northstar:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libgksu2-0
The following NEW packages will be installed:
  gksu libgksu2-0
0 upgraded, 2 newly installed, 0 to remove and 5 not upgraded.
Need to get 99.6 kB of archives.
After this operation, 740 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 amd64 2.0.13~pre1-6ubuntu4 [71.8 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/universe gksu amd64 2.0.2-6ubuntu2 [27.8 kB]
Fetched 99.6 kB in 1s (97.7 kB/s)
Selecting previously unselected package libgksu2-0.
(Reading database ... 164758 files and directories currently installed.)
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_amd64.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_amd64.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
rob@Northstar:~$ gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list

(gksudo:3598): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed

(gedit:3649): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
rob@Northstar:~$ 
rob@Northstar:~$ 
rob@Northstar:~$  sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://us.archive.ubuntu.com trusty-updates InRelease           
Ign http://security.ubuntu.com trusty-security InRelease             
Ign http://extras.ubuntu.com trusty InRelease                        
Ign http://ppa.launchpad.net saucy InRelease                         
Ign http://us.archive.ubuntu.com trusty-backports InRelease          
Hit http://us.archive.ubuntu.com trusty Release.gpg                  
Hit http://security.ubuntu.com trusty-security Release.gpg           
Hit http://extras.ubuntu.com trusty Release.gpg                      
Get:1 http://ppa.launchpad.net saucy Release.gpg [316 B]             
Get:2 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]                                 
Hit http://security.ubuntu.com trusty-security Release                                                 
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                                  
Get:3 http://ppa.launchpad.net saucy Release [11.9 kB]                 
Hit http://us.archive.ubuntu.com trusty Release                                                      
Hit http://security.ubuntu.com trusty-security/main Sources                                    
Hit http://extras.ubuntu.com trusty/main Sources                                            
Get:4 http://us.archive.ubuntu.com trusty-updates Release [58.5 kB]   
Get:5 http://ppa.launchpad.net saucy/main amd64 Packages [3,126 B]                                  
Hit http://security.ubuntu.com trusty-security/restricted Sources                                              
Hit http://extras.ubuntu.com trusty/main amd64 Packages                                                        
Hit http://security.ubuntu.com trusty-security/universe Sources                                                
Get:6 http://ppa.launchpad.net saucy/main i386 Packages [3,126 B]                                              
Hit http://extras.ubuntu.com trusty/main i386 Packages                                                         
Hit http://us.archive.ubuntu.com trusty-backports Release                                   
Hit http://security.ubuntu.com trusty-security/multiverse Sources                                              
Hit http://us.archive.ubuntu.com trusty/main Sources                                        
Hit http://us.archive.ubuntu.com trusty/restricted Sources            
Hit http://security.ubuntu.com trusty-security/main amd64 Packages    
Hit http://us.archive.ubuntu.com trusty/universe Sources              
Hit http://us.archive.ubuntu.com trusty/multiverse Sources            
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages           
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages     
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages       
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com trusty/main i386 Packages            
Hit http://security.ubuntu.com trusty-security/main i386 Packages     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages      
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages                            
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/main Translation-en           
Ign http://extras.ubuntu.com trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en     
Ign http://ppa.launchpad.net saucy/main Translation-en_US             
Hit http://security.ubuntu.com trusty-security/main Translation-en    
Ign http://extras.ubuntu.com trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en     
Ign http://ppa.launchpad.net saucy/main Translation-en                
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:7 http://us.archive.ubuntu.com trusty-updates/main Sources [2,774 B]
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted Sources [14 B]
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Get:9 http://us.archive.ubuntu.com trusty-updates/universe Sources [648 B]
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [1,790 B]
Get:11 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [9,544 B]
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [1,602 B]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [6,362 B]
Get:15 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [8,160 B]
Hit http://security.ubuntu.com trusty-security/universe Translation-en  
Get:16 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Get:17 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [1,601 B]
Get:18 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [6,386 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en     
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                                                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US                                           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US                                           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US                                             
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US                                         
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US                                   
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US                                   
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US                                     
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US                                       
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US
Fetched 117 kB in 12s (9,303 B/s)
Reading package lists... Done
rob@Northstar:~$ sudo apt-get install -y boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav boot-sav-extra gawk glade2script libsigsegv2 pastebinit
Suggested packages:
  dmraid lvm2 mbr mdadm clean-ubiquity os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra gawk glade2script libsigsegv2 pastebinit
0 upgraded, 7 newly installed, 0 to remove and 5 not upgraded.
Need to get 1,473 kB of archives.
After this operation, 5,025 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/main libsigsegv2 amd64 2.10-2 [15.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ saucy/main glade2script all 3.2.2~ppa47~saucy [42.3 kB]
Get:4 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ saucy/main boot-sav all 3.199~ppa40~saucy [430 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty/main pastebinit all 1.4-3 [14.9 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ saucy/main boot-repair all 3.199~ppa40~saucy [47.2 kB]
Get:7 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/ saucy/main boot-sav-extra all 3.199~ppa40~saucy [142 kB]
Fetched 1,473 kB in 2s (542 kB/s)       
Selecting previously unselected package libsigsegv2:amd64.
(Reading database ... 164814 files and directories currently installed.)
Preparing to unpack .../libsigsegv2_2.10-2_amd64.deb ...
Unpacking libsigsegv2:amd64 (2.10-2) ...
Setting up libsigsegv2:amd64 (2.10-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Selecting previously unselected package gawk.
(Reading database ... 164822 files and directories currently installed.)
Preparing to unpack .../gawk_1%3a4.0.1+dfsg-2.1ubuntu2_amd64.deb ...
Unpacking gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Selecting previously unselected package glade2script.
Preparing to unpack .../glade2script_3.2.2~ppa47~saucy_all.deb ...
Unpacking glade2script (3.2.2~ppa47~saucy) ...
Selecting previously unselected package boot-sav.
Preparing to unpack .../boot-sav_3.199~ppa40~saucy_all.deb ...
Unpacking boot-sav (3.199~ppa40~saucy) ...
Selecting previously unselected package boot-repair.
Preparing to unpack .../boot-repair_3.199~ppa40~saucy_all.deb ...
Unpacking boot-repair (3.199~ppa40~saucy) ...
Selecting previously unselected package boot-sav-extra.
Preparing to unpack .../boot-sav-extra_3.199~ppa40~saucy_all.deb ...
Unpacking boot-sav-extra (3.199~ppa40~saucy) ...
Selecting previously unselected package pastebinit.
Preparing to unpack .../pastebinit_1.4-3_all.deb ...
Unpacking pastebinit (1.4-3) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up gawk (1:4.0.1+dfsg-2.1ubuntu2) ...
Setting up glade2script (3.2.2~ppa47~saucy) ...
Setting up boot-sav (3.199~ppa40~saucy) ...
Setting up boot-repair (3.199~ppa40~saucy) ...
Setting up boot-sav-extra (3.199~ppa40~saucy) ...
Setting up pastebinit (1.4-3) ...
rob@Northstar:~$ 
rob@Northstar:~$ 
rob@Northstar:~$ boot-repair



rob@Northstar:~$ sudo dpkg --configure -a
[sudo] password for rob: 
rob@Northstar:~$ sudo apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
rob@Northstar:~$ sudo apt-get purge -y --force-yes grub* shim-signed linux-signed*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'grub-gfxpayload-lists' for regex 'grub*'
Note, selecting 'pv-grub-menu' for regex 'grub*'
Note, selecting 'grub-efi-amd64-bin' for regex 'grub*'
Note, selecting 'grub-doc' for regex 'grub*'
Note, selecting 'grub-coreboot' for regex 'grub*'
Note, selecting 'grub-efi-ia32' for regex 'grub*'
Note, selecting 'grub-efi-amd64' for regex 'grub*'
Note, selecting 'grub-invaders' for regex 'grub*'
Note, selecting 'congruity' for regex 'grub*'
Note, selecting 'grub-efi-ia64' for regex 'grub*'
Note, selecting 'grub-pc-dbg' for regex 'grub*'
Note, selecting 'sabily-grub-artwork' for regex 'grub*'
Note, selecting 'ruby-rspec-longrun' for regex 'grub*'
Note, selecting 'grub-xen-dbg' for regex 'grub*'
Note, selecting 'espresso-grub' for regex 'grub*'
Note, selecting 'grub-efi-i386' for regex 'grub*'
Note, selecting 'grub-imageboot' for regex 'grub*'
Note, selecting 'grub-firmware-qemu' for regex 'grub*'
Note, selecting 'grub-common' for regex 'grub*'
Note, selecting 'kde-config-grub2' for regex 'grub*'
Note, selecting 'grub-ieee1275' for regex 'grub*'
Note, selecting 'grub-efi-ia32-dbg' for regex 'grub*'
Note, selecting 'grub-coreboot-bin' for regex 'grub*'
Note, selecting 'grub2-common' for regex 'grub*'
Note, selecting 'grub-linuxbios' for regex 'grub*'
Note, selecting 'grub-ieee1275-bin' for regex 'grub*'
Note, selecting 'grub-efi-amd64-dbg' for regex 'grub*'
Note, selecting 'grub-legacy-ec2' for regex 'grub*'
Note, selecting 'grub-theme-starfield' for regex 'grub*'
Note, selecting 'grub2-splashimages' for regex 'grub*'
Note, selecting 'wmlongrun' for regex 'grub*'
Note, selecting 'grub-efi-amd64-signed' for regex 'grub*'
Note, selecting 'grub-emu-dbg' for regex 'grub*'
Note, selecting 'grub' for regex 'grub*'
Note, selecting 'grun' for regex 'grub*'
Note, selecting 'grub-legacy' for regex 'grub*'
Note, selecting 'grub2' for regex 'grub*'
Note, selecting 'grub-pc-bin' for regex 'grub*'
Note, selecting 'grub-yeeloong' for regex 'grub*'
Note, selecting 'grub-efi' for regex 'grub*'
Note, selecting 'grub-pc' for regex 'grub*'
Note, selecting 'grub-disk' for regex 'grub*'
Note, selecting 'grub-splashimages' for regex 'grub*'
Note, selecting 'grub-xen-bin' for regex 'grub*'
Note, selecting 'fgrun' for regex 'grub*'
Note, selecting 'grub-emu' for regex 'grub*'
Note, selecting 'grub-ipxe' for regex 'grub*'
Note, selecting 'grub-rescue-pc' for regex 'grub*'
Note, selecting 'ruby-gruff' for regex 'grub*'
Note, selecting 'grub-coreboot-dbg' for regex 'grub*'
Note, selecting 'grub-xen' for regex 'grub*'
Note, selecting 'grub-efi-ia32-bin' for regex 'grub*'
Note, selecting 'grub-ieee1275-dbg' for regex 'grub*'
Note, selecting 'grub-legacy-doc' for regex 'grub*'
Package 'grub-efi-ia64' is not installed, so not removed
Package 'grub-yeeloong' is not installed, so not removed
Package 'grub-legacy' is not installed, so not removed
Package 'espresso-grub' is not installed, so not removed
Package 'grub-efi-i386' is not installed, so not removed
Note, selecting 'linux-signed-image-3.13.0-24-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-raring-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-trusty' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-raring' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-saucy-eol-upgrade' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-saucy' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-saucy' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-quantal' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-quantal' for regex 'linux-signed*'
Note, selecting 'efilinux-signed' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic-lts-trusty' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-raring' for regex 'linux-signed*'
Note, selecting 'linux-signed-image-generic' for regex 'linux-signed*'
Note, selecting 'linux-signed-generic-lts-quantal-eol-upgrade' for regex 'linux-signed*'
Package 'grub' is not installed, so not removed
Package 'grub-doc' is not installed, so not removed
Package 'grub-efi' is not installed, so not removed
Package 'grub-efi-amd64-dbg' is not installed, so not removed
Package 'grub-efi-ia32' is not installed, so not removed
Package 'grub-efi-ia32-bin' is not installed, so not removed
Package 'grub-efi-ia32-dbg' is not installed, so not removed
Package 'grub-gfxpayload-lists' is not installed, so not removed
Package 'grub-ieee1275' is not installed, so not removed
Package 'grub-ieee1275-bin' is not installed, so not removed
Package 'grub-ieee1275-dbg' is not installed, so not removed
Package 'grub-ipxe' is not installed, so not removed
Package 'grub-legacy-doc' is not installed, so not removed
Package 'grub-legacy-ec2' is not installed, so not removed
Package 'grub-pc' is not installed, so not removed
Package 'grub-pc-bin' is not installed, so not removed
Package 'grub-pc-dbg' is not installed, so not removed
Package 'grub-xen' is not installed, so not removed
Package 'grub-xen-bin' is not installed, so not removed
Package 'grub-xen-dbg' is not installed, so not removed
Package 'congruity' is not installed, so not removed
Package 'efilinux-signed' is not installed, so not removed
Package 'fgrun' is not installed, so not removed
Package 'grub-coreboot' is not installed, so not removed
Package 'grub-coreboot-bin' is not installed, so not removed
Package 'grub-coreboot-dbg' is not installed, so not removed
Package 'grub-disk' is not installed, so not removed
Package 'grub-emu' is not installed, so not removed
Package 'grub-emu-dbg' is not installed, so not removed
Package 'grub-firmware-qemu' is not installed, so not removed
Package 'grub-imageboot' is not installed, so not removed
Package 'grub-invaders' is not installed, so not removed
Package 'grub-linuxbios' is not installed, so not removed
Package 'grub-rescue-pc' is not installed, so not removed
Package 'grub-splashimages' is not installed, so not removed
Package 'grub-theme-starfield' is not installed, so not removed
Package 'grub2' is not installed, so not removed
Package 'grub2-splashimages' is not installed, so not removed
Package 'grun' is not installed, so not removed
Package 'kde-config-grub2' is not installed, so not removed
Package 'pv-grub-menu' is not installed, so not removed
Package 'ruby-gruff' is not installed, so not removed
Package 'ruby-rspec-longrun' is not installed, so not removed
Package 'sabily-grub-artwork' is not installed, so not removed
Package 'wmlongrun' is not installed, so not removed
Package 'linux-signed-generic-lts-quantal' is not installed, so not removed
Package 'linux-signed-generic-lts-quantal-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-raring' is not installed, so not removed
Package 'linux-signed-generic-lts-raring-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-saucy' is not installed, so not removed
Package 'linux-signed-generic-lts-saucy-eol-upgrade' is not installed, so not removed
Package 'linux-signed-generic-lts-trusty' is not installed, so not removed
Package 'linux-signed-image-generic-lts-quantal' is not installed, so not removed
Package 'linux-signed-image-generic-lts-raring' is not installed, so not removed
Package 'linux-signed-image-generic-lts-saucy' is not installed, so not removed
Package 'linux-signed-image-generic-lts-trusty' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  secureboot-db shim
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-common* grub-efi-amd64* grub-efi-amd64-bin* grub-efi-amd64-signed*
  grub2-common* linux-signed-generic* linux-signed-image-3.13.0-24-generic*
  linux-signed-image-generic* shim-signed*
0 upgraded, 0 newly installed, 9 to remove and 5 not upgraded.
After this operation, 20.3 MB disk space will be freed.
(Reading database ... 165084 files and directories currently installed.)
Removing shim-signed (1.6+0.4-0ubuntu4) ...
Removing grub-efi-amd64-signed (1.34+2.02~beta2-9) ...
Removing grub-efi-amd64 (2.02~beta2-9) ...
Purging configuration files for grub-efi-amd64 (2.02~beta2-9) ...
Removing grub2-common (2.02~beta2-9) ...
Removing grub-efi-amd64-bin (2.02~beta2-9) ...
Removing grub-common (2.02~beta2-9) ...
Purging configuration files for grub-common (2.02~beta2-9) ...
Removing linux-signed-generic (3.13.0.24.29) ...
Removing linux-signed-image-generic (3.13.0.24.29) ...
Removing linux-signed-image-3.13.0-24-generic (3.13.0-24.46) ...
Purging configuration files for linux-signed-image-3.13.0-24-generic (3.13.0-24.46) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
rob@Northstar:~$

```

---

### Post by oldfred on 2014-04-21
Moved to Apple sub-forum.

I do not know Macs.

But I thought you had to have the not really recommended hybrid MBR/gpt partitioning to boot Windows as with a Mac you boot Windows in BIOS mode. And Windows only boots from gpt with UEFI but is not working with Apples UEFI.
But some have reported success using UEFI with Ubuntu and a Mac. And Ubuntu works from gpt partitions to boot in BIOS mode.
Many seem to use rEFInd.

       [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)


 Triple Boot MacbookPro (Lion, Win7, Ubuntu) Ubuntu in BIOS mode
[http://ubuntuforums.org/showthread.php?t=1908210](http://ubuntuforums.org/showthread.php?t=1908210)

      
 Alternative to grub using refind or gummiboot
[https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards](https://wiki.archlinux.org/index.php/Beginners%27_Guide#For_UEFI_motherboards)
Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by Xfilers on 2014-04-22
Couldn't get boot-repair to work under 14.04 using any of the workarounds.  Ended up trying 13.10, works flawlessly.  Triple boot between all 3 is working.  Now to get them in vmware fusion too! :guitar:

---

