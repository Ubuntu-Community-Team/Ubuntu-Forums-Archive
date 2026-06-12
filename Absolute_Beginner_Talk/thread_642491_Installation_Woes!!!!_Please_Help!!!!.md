---
title: "Installation Woes!!!! Please Help!!!!"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by tmcginn5 on 2007-12-16
I attempted to upgrade from Feisty to Gutsy via Update Manager.  The update froze about 2/3 through the installation process.  I had to turn off my laptop and reboot.  I was able to reboot to the desktop.  At this point, pretty much nothing is working except for internet(F.F.) and Thunderbird.  On the desktop the update manager icon pops up and tells me that I need to run the Update Manager.  When I do I get the following Error Message:

SOFTWARE INDEX BROKEN
It is impossible to install or remove any software.  Please use the package manager "Synaptic" or run "sudo apt-get install-f" in a terminal to fix this issue first.

When I try to open "Synaptic" I get the following message:
AN ERROR OCCURRED
The following details are provided:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache->open()failed, please report

When I try to run "sudo apt-get install-f" in the terminal I get the following message:
E: Invalid operation install-f

When I try running 'dpkg --configure -a' in the terminal I get the following message:
Requested operation requires superuser privilege

Laptop is Dell Inspiron 1150

PLEASE HELP!!!!!

---

### Post by Seisen on 2007-12-16
You need to run the command in the terminal with sudo in front of it. Sudo will give you temporary root privileges. Also its not sudo apt-get install-f its 

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a 
```

---

### Post by SteveHoffmanUK on 2007-12-16
tmcginn5 wrote:
> When I try running 'dpkg --configure -a' in the terminal I get the following message:
Requested operation requires superuser privilege

Try:
**sudo **dpkg --configure -a

---

### Post by tmcginn5 on 2007-12-16
I ran both commands in the terminal.  Here are the results:

mark@mark-laptop:~$ sudo apt-get -f install
[sudo] password for mark:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
mark@mark-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libdeskbar-tracker:
 libdeskbar-tracker depends on tracker; however:
  Package tracker is not installed.
dpkg: error processing libdeskbar-tracker (--configure):
 dependency problems - leaving unconfigured
Setting up mdadm (2.5.6-7ubuntu5) ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-386
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-386
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
update-initramfs: Generating /boot/initrd.img-2.6.17-11-386
W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.
update-initramfs: Generating /boot/initrd.img-2.6.15-28-386
W: udev hook script requires at least kernel version 2.6.17
W: not generating requested initramfs for kernel 2.6.15-28-386
update-initramfs: Generating /boot/initrd.img-2.6.15-23-386
W: udev hook script requires at least kernel version 2.6.17
W: not generating requested initramfs for kernel 2.6.15-23-386
 * Starting MD monitoring service mdadm --monitor                               /sbin/mdadm already running.
                                                                         [fail]

Errors were encountered while processing:
 libdeskbar-tracker
mark@mark-laptop:~$

---

### Post by tmcginn5 on 2007-12-16
Please Help!!!!

---

### Post by tmcginn5 on 2007-12-17
Any help would be appreciated

---

### Post by Anicka on 2007-12-17
I'm slightly in the dark, but I would try:```
sudo apt-get install --reinstall -f libdeskbar-tracker
```Then I would cycle```
sudo apt-get update
sudo apt-get dist-upgrade
```If necessary run```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by tmcginn5 on 2007-12-17
After running sudo apt-get install --reinstall -f libdeskbar-tracker then sudo apt-get -f install in the terminal, here are the results:

mark@mark-laptop:~$ sudo apt-get install --reinstall -f libdeskbar-tracker
[sudo] password for mark:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libdeskbar-tracker: Depends: tracker but it is not going to be installed
  tracker-search-tool: Depends: tracker (= 0.6.3-0ubuntu3) but it is not going to be installed
  tracker-utils: Depends: tracker (= 0.6.3-0ubuntu3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
mark@mark-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gs-esp-x evolution-common libmono2.0-cil libmono-data-tds2.0-cil
  libmono-system-data2.0-cil feisty-wallpapers desktop-effects
  libjack0.100.0-0 command-not-found-data libndesk-dbus1.0-cil
  linux-headers-2.6.20-16-generic libmono-security2.0-cil libslab0
  libegroupwise1.2-13 libmono-sqlite2.0-cil libmono-system-web2.0-cil
  libmono-sharpzip2.84-cil libmono-corlib2.0-cil linux-headers-2.6.20-16
  feisty-session-splashes myspell-en-za libndesk-dbus-glib1.0-cil libgs-esp8
  libquicktime0 python2.5-examples libmono-system2.0-cil libgdiplus libungif4g
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  tracker
Suggested packages:
  imagemagick djvulibre-bin gnumeric
The following NEW packages will be installed:
  tracker
0 upgraded, 1 newly installed, 0 to remove and 206 not upgraded.
2 not fully installed or removed.
Need to get 0B/278kB of archives.
After unpacking 1679kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 132686 files and directories currently installed.)
Unpacking tracker (from .../tracker_0.6.3-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb (--unpack):
 unable to stat `./usr/share/man/man7/tracker-services.7.gz' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@mark-laptop:~$ 

Any suggestions for help.  By the way, after running this I now can open synaptic package manager.
Please Help!!!!

---

### Post by Anicka on 2007-12-18
Now you can see that apt-get is giving an other error-message than before, so something good has happened. Look in you source-file (gksudo gedit /etc/apt/sources.list) and check that all your repos are marked with gutsy and not feisty. After that you can either try in synaptic with reload and upgrade, but I think that you should try with apt-get (more possibilities) ```
sudo apt-get update
sudo apt-get -f install tracker tracker-search-tool tracker-utils libdeskbar-tracker
sudo apt-get dist-upgrade
```If you don't get any error messages, run "sudo apt-get update && sudo apt-get dist-upgrade" until there are no more packages to be installed.

If you after this still get message: "broken dependencies" run "sudo apt-get - install" of if you get something like "dpkg: error processing (--configure)" run "sudo dpkg --configure -a" or "sudo dpkg --configure name_of_package_that_is_complained_about" and try again.

Edit: I reread you post. There might be a problem with your cache (bad downloads during the failed upgrade), so first of all run "sudo apt-get clean". It will delete all downloaded packages in your cache. Or if you really want to have an intact cache for future purposes "sudo rm /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb" (I hope I got the filename right)

---

### Post by tmcginn5 on 2007-12-18
I ran "sudo apt-get clean" and "sudo rm /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb" in the terminal and got the following results:

mark@mark-laptop:~$ sudo apt-get clean
[sudo] password for mark:
mark@mark-laptop:~$ sudo apt-get clean
mark@mark-laptop:~$ sudo rm /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb
rm: cannot remove `/var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb': No such file or directory
mark@mark-laptop:~$ gksudo gedit /etc/apt/sources.list

mark@mark-laptop:~$ 

I also ran (gksudo gedit /etc/apt/sources.list) and here are the results:

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse universe main restricted

I am not sure what to do with these results.
Please advise.

---

### Post by Anicka on 2007-12-18
Looks good! What happens now when you run "sudo apt-get update" and "sudo apt-get dist-upgrade"? Do you still get errormessages or it seems to be running fine?

The "sudo rm" thing failed only because you had removed that file with the first command.

---

### Post by tmcginn5 on 2007-12-18
Here are the results when running sudo apt-get update" and "sudo apt-get dist-upgrade:

mark@mark-laptop:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US     
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]          
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Fetched 4B in 1s (2B/s)  
Reading package lists... Done
mark@mark-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libdeskbar-tracker: Depends: tracker but it is not installed
  tracker-search-tool: Depends: tracker (= 0.6.3-0ubuntu3) but it is not installed
  tracker-utils: Depends: tracker (= 0.6.3-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.
mark@mark-laptop:~$

---

### Post by Anicka on 2007-12-18
Have you tried to do all the commands that I gave you earlier?
> ```
sudo apt-get update
sudo apt-get -f install tracker tracker-search-tool tracker-utils libdeskbar-tracker
sudo apt-get dist-upgrade
```If you don't get any error messages, run "sudo apt-get update && sudo apt-get dist-upgrade" until there are no more packages to be installed.

If you after this still get message: "broken dependencies" run "sudo apt-get - install" of if you get something like "dpkg: error processing (--configure)" run "sudo dpkg --configure -a" or "sudo dpkg --configure name_of_package_that_is_complained_about" and try again.
Post the messages that you get.

On one of the last line of your last post the error message it says "run 'apt-get -f install'". It means "every time you see this message run 'sudo apt-get -f install'".

---

### Post by tmcginn5 on 2007-12-18
I have run all of the following commands in the terminal:

sudo apt-get update
sudo apt-get -f install tracker tracker-search-tool tracker-utils libdeskbar-tracker
sudo apt-get dist-upgrade

"sudo apt-get - install" 
"sudo dpkg --configure -a" and
 "sudo dpkg --configure name_of_package_that_is_complained_about"

Here are the results:

mark@mark-laptop:~$ sudo apt-get update
[sudo] password for mark:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Fetched 4B in 2s (2B/s)  
Reading package lists... Done
mark@mark-laptop:~$ sudo apt-get -f install tracker tracker-search-tool tracker-utils libdeskbar-tracker
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tracker-search-tool is already the newest version.
tracker-utils is already the newest version.
libdeskbar-tracker is already the newest version.
The following packages were automatically installed and are no longer required:
  gs-esp-x evolution-common libmono2.0-cil libmono-data-tds2.0-cil
  libmono-system-data2.0-cil feisty-wallpapers desktop-effects
  libjack0.100.0-0 command-not-found-data libndesk-dbus1.0-cil
  linux-headers-2.6.20-16-generic libmono-security2.0-cil libslab0
  libegroupwise1.2-13 libmono-sqlite2.0-cil libmono-system-web2.0-cil
  libmono-sharpzip2.84-cil libmono-corlib2.0-cil linux-headers-2.6.20-16
  feisty-session-splashes myspell-en-za libndesk-dbus-glib1.0-cil libgs-esp8
  libquicktime0 python2.5-examples libmono-system2.0-cil libgdiplus libungif4g
Use 'apt-get autoremove' to remove them.
Suggested packages:
  imagemagick djvulibre-bin gnumeric
The following NEW packages will be installed:
  tracker
0 upgraded, 1 newly installed, 0 to remove and 206 not upgraded.
3 not fully installed or removed.
Need to get 278kB of archives.
After unpacking 1679kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main tracker 0.6.3-0ubuntu3 [278kB]
Fetched 278kB in 7s (34.9kB/s)                                                 
(Reading database ... 132695 files and directories currently installed.)
Unpacking tracker (from .../tracker_0.6.3-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb (--unpack):
 unable to stat `./usr/share/man/man7/tracker-services.7.gz' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@mark-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libdeskbar-tracker: Depends: tracker but it is not installed
  tracker-search-tool: Depends: tracker (= 0.6.3-0ubuntu3) but it is not installed
  tracker-utils: Depends: tracker (= 0.6.3-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.
mark@mark-laptop:~$ sudo apt-get - install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libdeskbar-tracker: Depends: tracker but it is not installed
  tracker-search-tool: Depends: tracker (= 0.6.3-0ubuntu3) but it is not installed
  tracker-utils: Depends: tracker (= 0.6.3-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.
mark@mark-laptop:~$ sudo dpkg --configure name_of_package_that_is_complained_about
dpkg: error processing name_of_package_that_is_complained_about (--configure):
 no package named `name_of_package_that_is_complained_about' is installed, cannot configure
Errors were encountered while processing:
 name_of_package_that_is_complained_about
mark@mark-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libdeskbar-tracker:
 libdeskbar-tracker depends on tracker; however:
  Package tracker is not installed.
dpkg: error processing libdeskbar-tracker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tracker-utils:
 tracker-utils depends on tracker (= 0.6.3-0ubuntu3); however:
  Package tracker is not installed.
dpkg: error processing tracker-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tracker-search-tool:
 tracker-search-tool depends on tracker (= 0.6.3-0ubuntu3); however:
  Package tracker is not installed.
dpkg: error processing tracker-search-tool (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdeskbar-tracker
 tracker-utils
 tracker-search-tool

---

### Post by Anicka on 2007-12-18
I'm sorry, but in the code when i wrote "name_of_package_that_is_complained_about", I meant "if there is any problem with a package, paste the name here and run the command".

Apparently you are stuck somewhere, so I'm going to give you a potentionally dangerous command```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb
```After that you run"sudo dpkg --configure -a", "sudo apt-get update", sudo apt-get dist-upgrade" and if necessary "sudo apt-get -f install"

Good luck!

---

### Post by tmcginn5 on 2007-12-18
I have run the following commands in the terminal:

Code:

sudo dpkg -i --force-overwrite /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb

"sudo dpkg --configure -a"
"sudo apt-get update"
sudo apt-get dist-upgrade" 
"sudo apt-get -f install"

Here are the results:

mark@mark-laptop:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb
[sudo] password for mark:
(Reading database ... 132695 files and directories currently installed.)
Unpacking tracker (from .../tracker_0.6.3-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb (--install):
 unable to stat `./usr/share/man/man7/tracker-services.7.gz' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb
mark@mark-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libdeskbar-tracker:
 libdeskbar-tracker depends on tracker; however:
  Package tracker is not installed.
dpkg: error processing libdeskbar-tracker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tracker-utils:
 tracker-utils depends on tracker (= 0.6.3-0ubuntu3); however:
  Package tracker is not installed.
dpkg: error processing tracker-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tracker-search-tool:
 tracker-search-tool depends on tracker (= 0.6.3-0ubuntu3); however:
  Package tracker is not installed.
dpkg: error processing tracker-search-tool (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libdeskbar-tracker
 tracker-utils
 tracker-search-tool
mark@mark-laptop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Fetched 4B in 9s (0B/s)                                                        
Reading package lists... Done
mark@mark-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libdeskbar-tracker: Depends: tracker but it is not installed
  tracker-search-tool: Depends: tracker (= 0.6.3-0ubuntu3) but it is not installed
  tracker-utils: Depends: tracker (= 0.6.3-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.
mark@mark-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gs-esp-x evolution-common libmono2.0-cil libmono-data-tds2.0-cil
  libmono-system-data2.0-cil feisty-wallpapers desktop-effects
  libjack0.100.0-0 command-not-found-data libndesk-dbus1.0-cil
  linux-headers-2.6.20-16-generic libmono-security2.0-cil libslab0
  libegroupwise1.2-13 libmono-sqlite2.0-cil libmono-system-web2.0-cil
  libmono-sharpzip2.84-cil libmono-corlib2.0-cil linux-headers-2.6.20-16
  feisty-session-splashes myspell-en-za libndesk-dbus-glib1.0-cil libgs-esp8
  libquicktime0 python2.5-examples libmono-system2.0-cil libgdiplus libungif4g
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  tracker
Suggested packages:
  imagemagick djvulibre-bin gnumeric
The following NEW packages will be installed:
  tracker
0 upgraded, 1 newly installed, 0 to remove and 206 not upgraded.
3 not fully installed or removed.
Need to get 0B/278kB of archives.
After unpacking 1679kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 132695 files and directories currently installed.)
Unpacking tracker (from .../tracker_0.6.3-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb (--unpack):
 unable to stat `./usr/share/man/man7/tracker-services.7.gz' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mark@mark-laptop:~$ 

Not sure what to do now

---

### Post by Anicka on 2007-12-18
Try this: "sudo dpkg -i --force-all /var/cache/apt/archives/*tracker*.deb"
It will force install all packages from your cache that contains the word tracker. After that try: "sudo apt-get dist-upgrade"

---

### Post by tmcginn5 on 2007-12-19
I ran sudo dpkg -i --force-all /var/cache/apt/archives/*tracker*.deb" then
sudo apt-get dist-upgrade" in the terminal and got the following results:

mark@mark-laptop:~$ sudo dpkg -i --force-all /var/cache/apt/archives/*tracker*.deb
[sudo] password for mark:
(Reading database ... 132695 files and directories currently installed.)
Preparing to replace libdeskbar-tracker 0.6.3-0ubuntu3 (using .../libdeskbar-tracker_0.6.3-0ubuntu3_all.deb) ...
Unpacking replacement libdeskbar-tracker ...
Unpacking tracker (from .../tracker_0.6.3-0ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb (--install):
 unable to stat `./usr/share/man/man7/tracker-services.7.gz' (which I was about to install): Input/output error
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: libdeskbar-tracker: dependency problems, but configuring anyway as you request:
 libdeskbar-tracker depends on tracker; however:
  Package tracker is not installed.
Setting up libdeskbar-tracker (0.6.3-0ubuntu3) ...

Errors were encountered while processing:
 /var/cache/apt/archives/tracker_0.6.3-0ubuntu3_i386.deb
mark@mark-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libdeskbar-tracker: Depends: tracker but it is not installed
  tracker-search-tool: Depends: tracker (= 0.6.3-0ubuntu3) but it is not installed
  tracker-utils: Depends: tracker (= 0.6.3-0ubuntu3) but it is not installed
E: Unmet dependencies. Try using -f.
mark@mark-laptop:~$ 

Any Advice?

---

### Post by tmcginn5 on 2007-12-20
Still need help!!!!

---

### Post by tmcginn5 on 2007-12-26
I still have not been able to get my problems resolved.  Is there anybody out there who can review the history of this thread and be willing to give some advice.  Any help would be greatly appreciated!!!!  Thanks!!!!!

---

### Post by tmcginn5 on 2007-12-28
This is my last request for help.  If I get no responses, unfortunately I will have to trash Ubuntu and permanently return to Windows.  Too bad, I really enjoyed it up until now.  Just can't seem to get any help.

---

### Post by rkd on 2007-12-28
I don't know how your package manager database got so badly messed up, but it did. In a quick scan through this thread, I didn't see anyone suggesting that you backup your data files, then do a fresh install of gutsy, rather than try to salvage the upgrade. If I were in your shoes, that is what I would do.

---

### Post by tmcginn5 on 2007-12-29
How do I go about backing up my data files, then do a fresh install of gutsy.

---

### Post by ugm6hr on 2007-12-29
> **tmcginn5 said:**
> How do I go about backing up my data files, then do a fresh install of gutsy.

Not sure what you are asking here...  If all your files are in /home - then just copy /home to an external HD (or another partition).

Then download the Gutsy LiveCD, and boot from it.

From the LiveCD - run GParted, and delete the existing messed up partition, and then re-install.

---

### Post by tmcginn5 on 2007-12-29
Problem.  With all of these upgrade problems. most of my hardware, including usb and cd drive are not being recognized.  That's why I am trying to fix it internally through the terminal.

---

### Post by rkd on 2007-12-29
If you boot from the live CD, it will contain a consistent Ubuntu system that should mount your devices okay. Then you can copy any files you don't want to lose onto whatever external storage you have available -- USB flash drive, USB hard drive, or even floppy disks if your computer has a floppy drive and you don't have a large amount to save.

If you have trouble getting the live CD to give you access to a device you want to use to save your data, post a description of what is happening and we'll help you get it working.

---

### Post by Michl on 2008-01-19
Yes, boot from a live cd of any version of linux and copy
your files.  Then do a fresh install.

Basically, if you interrupt upgrade and after you are installing
packages, you are screwed because you
now have broken operating systems.  AT that point
all you can do is a fresh install.  You must not interrupt
an upgrade.  There is a reminder of this before you
start.  This happened to me once when I forgot to
plug into AC and was using a battery that was low.

As far as freezing is concerned, are you sure it
froze?  The upgrade takes a long time.

And one more comment about solving problems with dpkg.
 From my experience running dpkg has never solved anything
but only created more problems.

---

