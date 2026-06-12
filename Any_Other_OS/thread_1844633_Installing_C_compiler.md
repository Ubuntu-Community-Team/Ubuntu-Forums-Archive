---
title: "Installing C compiler"
date: 2011-09-15
forum: Any Other OS
---

### Post by chaituchill on 2011-09-15
Hi,

I am trying to compile C program  in linuxmint 10. I am getting the error below whenever i try to compile:
Its just a simple Hello world program.


ch@linuxmint ~ $ gcc a.c
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status

Can somebody pls tell me the solution.

---

### Post by haqking on 2011-09-15
> **chaituchill said:**
> Hi,

I am trying to compile C program  in linuxmint 10. I am getting the error below whenever i try to compile:
Its just a simple Hello world program.


ch@linuxmint ~ $ gcc a.c
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status

Can somebody pls tell me the solution.


probably 

```
sudo apt-get install build-essential
```but mint questions are probably better on a mint forum if you get no luck here.

---

### Post by uRock on 2011-09-15
Moved to *Other OS/Distro Talk*

---

### Post by chaituchill on 2011-09-15
Thanx for the quick reply. I am kind of new to linux...But i am getting an error that says:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by haqking on 2011-09-15
> **chaituchill said:**
> Thanx for the quick reply. I am kind of new to linux...But i am getting an error that says:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

do you have another app open such as synaptic or whatever it is in mint ?

also you can install using synpatic by searching for gcc.

But im guessing here as i am not famailiar with mint im afraid.

---

### Post by uRock on 2011-09-15
If the Software Center or Synaptic Package Manager are running, then you will not be able to run install commands.

---

### Post by chaituchill on 2011-09-15
There isn't much difference between mint and Ubuntu.You are right i had synaptic package manager running.   Mine is LiunuxMint 10(Julia) which is remake of Ubuntu (10). But anyway:I tried to install the google-talk plugin before and it didnt install correctly and i guess its the reason why im unable to install anything. I got an error saying it has some dependency problems.  
Please take a look at the attached file for the errors.

Is there a way to get rid of this google talk plugin so it doesnt cause more problems.

---

### Post by oldos2er on 2011-09-15
Please copy and paste the terminal text into a post here. Posting a PDF is not a good idea.

---

### Post by chaituchill on 2011-09-15
> **oldos2er said:**
> Please copy and paste the terminal text into a post here. Posting a PDF is not a good idea.
```
chaitu@linuxmint ~ $ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.4 libalgorithm-diff-perl libalgorithm-merge-perl libdpkg-perl libstdc++6-4.4-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg libstdc++6-4.4-doc diffutils-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.4 libalgorithm-diff-perl libalgorithm-merge-perl libdpkg-perl libstdc++6-4.4-dev patch
0 upgraded, 10 newly installed, 0 to remove and 117 not upgraded.
11 not fully installed or removed.
Need to get 8,739kB of archives.
After this operation, 26.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libstdc++6-4.4-dev g++-4.4 g++ libdpkg-perl dpkg-dev build-essential
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libstdc++6-4.4-dev amd64 4.4.4-14ubuntu5
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Get:1 [http://repo.iitd.ernet.in/ubuntu/](http://repo.iitd.ernet.in/ubuntu/) lucid/main patch amd64 2.6-2ubuntu1 [121kB]
Get:2 [http://repo.iitd.ernet.in/ubuntu/](http://repo.iitd.ernet.in/ubuntu/) lucid/main fakeroot amd64 1.14.4-1ubuntu1 [101kB]
Get:3 [http://repo.iitd.ernet.in/ubuntu/](http://repo.iitd.ernet.in/ubuntu/) lucid/main libalgorithm-diff-perl all 1.19.02-1 [51.3kB]
Get:4 [http://repo.iitd.ernet.in/ubuntu/](http://repo.iitd.ernet.in/ubuntu/) lucid/universe libalgorithm-merge-perl all 0.08-1 [13.0kB]
Fetched 286kB in 0s (609kB/s)               
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 114677 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.4-14ubuntu5_amd64.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.4-14ubuntu5_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.4.4-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.15.8.4ubuntu3_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.8.4ubuntu3_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5_amd64.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-1_all.deb) ...
Selecting previously deselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-1_all.deb) ...
Processing triggers for man-db ...
Setting up python2.7-minimal (2.7.1-5ubuntu2) ...
Linking and byte-compiling packages for runtime python2.7...
E: pycompile:240: Requested versions are not installed
dpkg: error processing python2.7-minimal (--configure):
 subprocess installed post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of python2.7:
 python2.7 depends on python2.7-minimal (= 2.7.1-5ubuntu2); however:
  Package python2.7-minimal is not configured yet.
dpkg: error processing python2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython2.7:
 libpython2.7 depends on python2.7 (= 2.7.1-5ubuntu2); however:
  Package python2.7 is not configured yet.
dpkg: error processing libpython2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libasound2:
 libasound2 depends on libpython2.7 (>= 2.7); however:
  Package libpython2.7 is not configured yet.
dpkg: error processing libasound2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lib32asound2:
 lib32asounNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                     No apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because MaxReports is reached already
                                                                                                                                No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
                                                                                               No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
                                                                                           d2 depends on libasound2 (= 1.0.24.1-0ubuntu5); however:
  Package libasound2 is not configured yet.
dpkg: error processing lib32asound2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on lib32asound2; however:
  Package lib32asound2 is not configured yet.
dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libasound2 (>> 1.0.24.1); however:
  Package libasound2 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-branding:
 firefox-branding depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 5.0+build1+nobinonly-0ubuntu0.11.04.2); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of google-talkplugin:
 google-talkplugin depends on ia32-libs (>= 2.4); however:
  Package ia32-libs is not configured yet.
 google-talkplugin depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.
  Package ia32-libs which provides ia32-libs-gtk is not configured yet.
dpkg: error processing google-talkplugin (--configure):
 dependency problems - leaving unconfigured
Setting up libdpkg-perl (1.15.8.4ubuntu3) ...
Setting up patch (2.6-2ubuntu1) ...
Setting up dpkg-dev (1.15.8.4ubuntu3) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libalgorithm-diff-perl (1.19.02-1) ...
Setting up libalgorithm-merge-perl (0.08-1) ...
Setting up libstdc++6-4.4-dev (4.4.4-14ubuntu5) ...
Setting up g++-4.4 (4.4.4-14ubuntu5) ...
Setting up g++ (4:4.4.4-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5) ...
Errors were encountered while processing:
 python2.7-minimal
 python2.7
 libpython2.7
 libasound2
 lib32asound2
 ia32-libs
 firefox
 firefox-branding
 firefox-globalmenu
 firefox-gnome-support
 google-talkplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
chaitu@linuxmint ~ $ gcc a.c
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
```

---

### Post by chaituchill on 2011-09-15
> **chaituchill said:**
> ```
chaitu@linuxmint ~ $ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.4 libalgorithm-diff-perl libalgorithm-merge-perl libdpkg-perl libstdc++6-4.4-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.4-multilib gcc-4.4-doc libstdc++6-4.4-dbg libstdc++6-4.4-doc diffutils-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.4 libalgorithm-diff-perl libalgorithm-merge-perl libdpkg-perl libstdc++6-4.4-dev patch
0 upgraded, 10 newly installed, 0 to remove and 117 not upgraded.
11 not fully installed or removed.
Need to get 8,739kB of archives.
After this operation, 26.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libstdc++6-4.4-dev g++-4.4 g++ libdpkg-perl dpkg-dev build-essential
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main libstdc++6-4.4-dev amd64 4.4.4-14ubuntu5
  Could not connect to archive.ubuntu.com:80 (91.189.88.40). - connect (111: Connection refused) [IP: 91.189.88.40 80]
Get:1 [http://repo.iitd.ernet.in/ubuntu/](http://repo.iitd.ernet.in/ubuntu/) lucid/main patch amd64 2.6-2ubuntu1 [121kB]
Get:2 [http://repo.iitd.ernet.in/ubuntu/](http://repo.iitd.ernet.in/ubuntu/) lucid/main fakeroot amd64 1.14.4-1ubuntu1 [101kB]
Get:3 [http://repo.iitd.ernet.in/ubuntu/](http://repo.iitd.ernet.in/ubuntu/) lucid/main libalgorithm-diff-perl all 1.19.02-1 [51.3kB]
Get:4 [http://repo.iitd.ernet.in/ubuntu/](http://repo.iitd.ernet.in/ubuntu/) lucid/universe libalgorithm-merge-perl all 0.08-1 [13.0kB]
Fetched 286kB in 0s (609kB/s)               
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 114677 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.4-14ubuntu5_amd64.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.4-14ubuntu5_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4.4.4-1ubuntu2_amd64.deb) ...
Selecting previously deselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.15.8.4ubuntu3_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.8.4ubuntu3_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5_amd64.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_amd64.deb) ...
Selecting previously deselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-1_all.deb) ...
Selecting previously deselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-1_all.deb) ...
Processing triggers for man-db ...
Setting up python2.7-minimal (2.7.1-5ubuntu2) ...
Linking and byte-compiling packages for runtime python2.7...
E: pycompile:240: Requested versions are not installed
dpkg: error processing python2.7-minimal (--configure):
 subprocess installed post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of python2.7:
 python2.7 depends on python2.7-minimal (= 2.7.1-5ubuntu2); however:
  Package python2.7-minimal is not configured yet.
dpkg: error processing python2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython2.7:
 libpython2.7 depends on python2.7 (= 2.7.1-5ubuntu2); however:
  Package python2.7 is not configured yet.
dpkg: error processing libpython2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libasound2:
 libasound2 depends on libpython2.7 (>= 2.7); however:
  Package libpython2.7 is not configured yet.
dpkg: error processing libasound2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lib32asound2:
 lib32asounNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                     No apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because MaxReports is reached already
                                                                                                                                No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
                                                                                               No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
                                                                                           d2 depends on libasound2 (= 1.0.24.1-0ubuntu5); however:
  Package libasound2 is not configured yet.
dpkg: error processing lib32asound2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on lib32asound2; however:
  Package lib32asound2 is not configured yet.
dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libasound2 (>> 1.0.24.1); however:
  Package libasound2 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-branding:
 firefox-branding depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 5.0+build1+nobinonly-0ubuntu0.11.04.2); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of google-talkplugin:
 google-talkplugin depends on ia32-libs (>= 2.4); however:
  Package ia32-libs is not configured yet.
 google-talkplugin depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.
  Package ia32-libs which provides ia32-libs-gtk is not configured yet.
dpkg: error processing google-talkplugin (--configure):
 dependency problems - leaving unconfigured
Setting up libdpkg-perl (1.15.8.4ubuntu3) ...
Setting up patch (2.6-2ubuntu1) ...
Setting up dpkg-dev (1.15.8.4ubuntu3) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up libalgorithm-diff-perl (1.19.02-1) ...
Setting up libalgorithm-merge-perl (0.08-1) ...
Setting up libstdc++6-4.4-dev (4.4.4-14ubuntu5) ...
Setting up g++-4.4 (4.4.4-14ubuntu5) ...
Setting up g++ (4:4.4.4-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5) ...
Errors were encountered while processing:
 python2.7-minimal
 python2.7
 libpython2.7
 libasound2
 lib32asound2
 ia32-libs
 firefox
 firefox-branding
 firefox-globalmenu
 firefox-gnome-support
 google-talkplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
chaitu@linuxmint ~ $ gcc a.c
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
```
is there a way to reinstall gc compiler again and avoid this error

---

### Post by NightwishFan on 2011-09-16
Try running:
> sudo apt-get -f install

---

### Post by chaituchill on 2011-09-16
The same errors occuring something about dependency problems..

Is there a way to bypass these errors?

---

### Post by NightwishFan on 2011-09-16
That is what apt-get -f install should had done. I will check it out.

Edit: Why do you have lucid _and_ maverick repositories enabled?

---

### Post by chaituchill on 2011-09-17
i'll remove them but i dont think linux is going to use any of those repositories..

---

### Post by NightwishFan on 2011-09-17
I didn't say that was the problem, but it might be.

---

### Post by chaituchill on 2011-09-17
my original linux mint is using maverick repos ...so i guess i added the wrong repos i changed it to maveric now...but anyway..how to get rid of these dependency problems

---

### Post by chaituchill on 2011-09-17
also all i want to do is make my gcc work properly..my original errors were 
```
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
```

---

### Post by NightwishFan on 2011-09-17
Ensure you are using the correct repositories, then run:
```
sudo apt-get update
```
Then run:
```
sudo apt-get -f install && sudo apt-get install build-essential
```

If this does not work you will have to manually reinstall some packages, perhaps post the output so I can see what is up.

---

### Post by chaituchill on 2011-09-17
Hi,

Finally got my C compiler working i had a bad link :/lib/libgcc_s.so its pointing to /lib/libgcc_s.so.1 
but my libgcc_s.so.1 file is in /lib/x86_64-linux-gnu directory ...i just copied and pasted this file at the correct target site :lolflag:

However sudo apt-get update is showing following errors:
```
Err http://archive.getdeb.net maverick-getdeb Release.gpg
  Could not connect to archive.getdeb.net:80 (209.105.191.78). - connect (111: Connection refused)
Err http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net/ubuntu/ maverick-getdeb/apps Translation-en_US
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net/ubuntu/ maverick-getdeb/games Translation-en
  Unable to connect to archive.getdeb.net:http:
Err http://archive.getdeb.net/ubuntu/ maverick-getdeb/games Translation-en_US
  Unable to connect to archive.getdeb.net:http:
Hit http://repo.iitd.ernet.in maverick Release.gpg                             
Err http://packages.linuxmint.com julia Release.gpg                            
  Could not connect to packages.linuxmint.com:80 (204.45.82.194). - connect (111: Connection refused)
Err http://packages.linuxmint.com/ julia/backport Translation-en               
  Unable to connect to packages.linuxmint.com:http:
Err http://packages.linuxmint.com/ julia/backport Translation-en_US            
  Unable to connect to packages.linuxmint.com:http:
Err http://packages.linuxmint.com/ julia/import Translation-en                 
  Unable to connect to packages.linuxmint.com:http:
Err http://packages.linuxmint.com/ julia/import Translation-en_US              
  Unable to connect to packages.linuxmint.com:http:
Err http://packages.linuxmint.com/ julia/main Translation-en                   
  Unable to connect to packages.linuxmint.com:http:
Err http://packages.linuxmint.com/ julia/main Translation-en_US                
  Unable to connect to packages.linuxmint.com:http:
Err http://packages.linuxmint.com/ julia/upstream Translation-en               
  Unable to connect to packages.linuxmint.com:http:
Err http://packages.linuxmint.com/ julia/upstream Translation-en_US            
  Unable to connect to packages.linuxmint.com:http:
Ign http://repo.iitd.ernet.in/ubuntu/ maverick/main Translation-en             
Ign http://repo.iitd.ernet.in/ubuntu/ maverick/main Translation-en_US          
Ign http://repo.iitd.ernet.in/ubuntu/ maverick/multiverse Translation-en       
Ign http://repo.iitd.ernet.in/ubuntu/ maverick/multiverse Translation-en_US    
Ign http://repo.iitd.ernet.in/ubuntu/ maverick/restricted Translation-en       
Ign http://repo.iitd.ernet.in/ubuntu/ maverick/restricted Translation-en_US    
Ign http://repo.iitd.ernet.in/ubuntu/ maverick/universe Translation-en         
Ign http://repo.iitd.ernet.in/ubuntu/ maverick/universe Translation-en_US      
Hit http://repo.iitd.ernet.in maverick-proposed Release.gpg                    
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-proposed/main Translation-en    
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-proposed/main Translation-en_US 
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-proposed/multiverse Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-proposed/multiverse Translation-en_US
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-proposed/restricted Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-proposed/restricted Translation-en_US
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-proposed/universe Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-proposed/universe Translation-en_US
Hit http://repo.iitd.ernet.in maverick-updates Release.gpg                     
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-updates/main Translation-en     
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-updates/main Translation-en_US  
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-updates/restricted Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-updates/universe Translation-en 
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://repo.iitd.ernet.in maverick-security Release.gpg                    
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-security/main Translation-en    
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-security/main Translation-en_US 
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-security/multiverse Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-security/restricted Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-security/universe Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-security/universe Translation-en_US
Hit http://repo.iitd.ernet.in maverick-backports Release.gpg                   
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-backports/main Translation-en   
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-backports/main Translation-en_US
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-backports/multiverse Translation-en_US
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-backports/restricted Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-backports/universe Translation-en
Ign http://repo.iitd.ernet.in/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://repo.iitd.ernet.in maverick Release                                 
Hit http://repo.iitd.ernet.in maverick-proposed Release                        
Hit http://repo.iitd.ernet.in maverick-updates Release                         
Hit http://repo.iitd.ernet.in maverick-security Release                        
Hit http://repo.iitd.ernet.in maverick-backports Release                       
Hit http://repo.iitd.ernet.in maverick/main Sources                            
Hit http://repo.iitd.ernet.in maverick/restricted Sources                      
Hit http://repo.iitd.ernet.in maverick/universe Sources                        
Hit http://repo.iitd.ernet.in maverick/multiverse Sources                      
Hit http://repo.iitd.ernet.in maverick/main amd64 Packages                     
Hit http://repo.iitd.ernet.in maverick/restricted amd64 Packages               
Hit http://repo.iitd.ernet.in maverick/universe amd64 Packages                 
Hit http://repo.iitd.ernet.in maverick/multiverse amd64 Packages               
Hit http://repo.iitd.ernet.in maverick-proposed/main Sources                   
Hit http://repo.iitd.ernet.in maverick-proposed/restricted Sources             
Hit http://repo.iitd.ernet.in maverick-proposed/universe Sources               
Hit http://repo.iitd.ernet.in maverick-proposed/multiverse Sources             
Hit http://repo.iitd.ernet.in maverick-proposed/main amd64 Packages            
Hit http://repo.iitd.ernet.in maverick-proposed/restricted amd64 Packages      
Hit http://repo.iitd.ernet.in maverick-proposed/universe amd64 Packages        
Hit http://repo.iitd.ernet.in maverick-proposed/multiverse amd64 Packages      
Hit http://repo.iitd.ernet.in maverick-updates/main Sources                    
Hit http://repo.iitd.ernet.in maverick-updates/restricted Sources              
Hit http://repo.iitd.ernet.in maverick-updates/universe Sources                
Hit http://repo.iitd.ernet.in maverick-updates/multiverse Sources              
Hit http://repo.iitd.ernet.in maverick-updates/main amd64 Packages             
Hit http://repo.iitd.ernet.in maverick-updates/restricted amd64 Packages       
Hit http://repo.iitd.ernet.in maverick-updates/universe amd64 Packages         
Hit http://repo.iitd.ernet.in maverick-updates/multiverse amd64 Packages       
Hit http://repo.iitd.ernet.in maverick-security/main Sources                   
Hit http://repo.iitd.ernet.in maverick-security/restricted Sources             
Hit http://repo.iitd.ernet.in maverick-security/universe Sources               
Hit http://repo.iitd.ernet.in maverick-security/multiverse Sources             
Hit http://repo.iitd.ernet.in maverick-security/main amd64 Packages            
Hit http://repo.iitd.ernet.in maverick-security/restricted amd64 Packages      
Hit http://repo.iitd.ernet.in maverick-security/universe amd64 Packages        
Hit http://repo.iitd.ernet.in maverick-security/multiverse amd64 Packages      
Hit http://repo.iitd.ernet.in maverick-backports/main Sources                  
Hit http://repo.iitd.ernet.in maverick-backports/restricted Sources            
Hit http://repo.iitd.ernet.in maverick-backports/universe Sources              
Hit http://repo.iitd.ernet.in maverick-backports/multiverse Sources            
Hit http://repo.iitd.ernet.in maverick-backports/main amd64 Packages           
Hit http://repo.iitd.ernet.in maverick-backports/restricted amd64 Packages     
Hit http://repo.iitd.ernet.in maverick-backports/universe amd64 Packages       
Hit http://repo.iitd.ernet.in maverick-backports/multiverse amd64 Packages     
Err http://security.ubuntu.com maverick-security Release.gpg                   
  Could not connect to security.ubuntu.com:80 (91.189.92.166). - connect (111: Connection refused) [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err http://archive.canonical.com maverick Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (111: Connection refused)
Err http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
  Unable to connect to archive.canonical.com:http:
Err http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
  Unable to connect to archive.canonical.com:http:
Err http://archive.ubuntu.com maverick Release.gpg                             
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US          
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US    
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US    
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US      
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com maverick-updates Release.gpg                     
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]
Err http://packages.medibuntu.org maverick Release.gpg
  Could not connect to packages.medibuntu.org:80 (88.191.127.22). - connect (111: Connection refused)
Err http://packages.medibuntu.org/ maverick/free Translation-en
  Unable to connect to packages.medibuntu.org:http:
Err http://packages.medibuntu.org/ maverick/free Translation-en_US
  Unable to connect to packages.medibuntu.org:http:
Err http://packages.medibuntu.org/ maverick/non-free Translation-en
  Unable to connect to packages.medibuntu.org:http:
Err http://packages.medibuntu.org/ maverick/non-free Translation-en_US
  Unable to connect to packages.medibuntu.org:http:
Reading package lists... Done             
W: Failed to fetch http://packages.linuxmint.com/dists/julia/Release.gpg  Could not connect to packages.linuxmint.com:80 (204.45.82.194). - connect (111: Connection refused)

W: Failed to fetch http://packages.linuxmint.com/dists/julia/backport/i18n/Translation-en.bz2  Unable to connect to packages.linuxmint.com:http:

W: Failed to fetch http://packages.linuxmint.com/dists/julia/backport/i18n/Translation-en_US.bz2  Unable to connect to packages.linuxmint.com:http:

W: Failed to fetch http://packages.linuxmint.com/dists/julia/import/i18n/Translation-en.bz2  Unable to connect to packages.linuxmint.com:http:

W: Failed to fetch http://packages.linuxmint.com/dists/julia/import/i18n/Translation-en_US.bz2  Unable to connect to packages.linuxmint.com:http:

W: Failed to fetch http://packages.linuxmint.com/dists/julia/main/i18n/Translation-en.bz2  Unable to connect to packages.linuxmint.com:http:

W: Failed to fetch http://packages.linuxmint.com/dists/julia/main/i18n/Translation-en_US.bz2  Unable to connect to packages.linuxmint.com:http:

W: Failed to fetch http://packages.linuxmint.com/dists/julia/upstream/i18n/Translation-en.bz2  Unable to connect to packages.linuxmint.com:http:

W: Failed to fetch http://packages.linuxmint.com/dists/julia/upstream/i18n/Translation-en_US.bz2  Unable to connect to packages.linuxmint.com:http:

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111: Connection refused) [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.31 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.92.166). - connect (111: Connection refused) [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (111: Connection refused)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_US.bz2  Unable to connect to archive.canonical.com:http:

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/Release.gpg  Could not connect to packages.medibuntu.org:80 (88.191.127.22). - connect (111: Connection refused)

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en.bz2  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/free/i18n/Translation-en_US.bz2  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en.bz2  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch http://packages.medibuntu.org/dists/maverick/non-free/i18n/Translation-en_US.bz2  Unable to connect to packages.medibuntu.org:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/Release.gpg  Could not connect to archive.getdeb.net:80 (209.105.191.78). - connect (111: Connection refused)

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/i18n/Translation-en.bz2  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/apps/i18n/Translation-en_US.bz2  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/games/i18n/Translation-en.bz2  Unable to connect to archive.getdeb.net:http:

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/maverick-getdeb/games/i18n/Translation-en_US.bz2  Unable to connect to archive.getdeb.net:http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```is there any problem with my current sources?

---

### Post by NightwishFan on 2011-09-17
Yes, I would remove any sources lines that have error in the output such as getdeb.

Also please note proposed updates are not intended for normal use but for testing and actually break quite often. I would remove those as well. It might be best just to trim down to a smaller sources.list with only what your vendor intended. (Mint).

Though the connection refused errors confuse me. It either means you have network problems or apt is trying to connect to the wrong places?

---

### Post by chaituchill on 2011-09-20
This is so irritating i cant install anything now. I tried to install picasa and it gets added to the error list now...somebody please tell me how to remove these errors.

```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 329 not upgraded.
12 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python2.7-minimal (2.7.1-5ubuntu2) ...
Linking and byte-compiling packages for runtime python2.7...
E: pycompile:240: Requested versions are not installed
dpkg: error processing python2.7-minimal (--configure):
 subprocess installed post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of python2.7:
 python2.7 depends on python2.7-minimal (= 2.7.1-5ubuntu2); however:
  Package python2.7-minimal is not configured yet.
dpkg: error processing python2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpython2.7:
 libpython2.7 depends on python2.7 (= 2.7.1-5ubuntu2); however:
  Package python2.7 is not configured yet.
dpkg: error processing libpython2.7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libasound2:
 libasound2 depends on libpython2.7 (>= 2.7); however:
  Package libpython2.7 is not configured yet.
dpkg: error processing libasound2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lib32asound2:
 lib32asounNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                     No apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because MaxReports is reached already
                                                                                                                                No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
                                                                                               No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
                                                                                           No apport report written because MaxReports is reached already
                                                                                                                                                         d2 depends on libasound2 (= 1.0.24.1-0ubuntu5); however:
  Package libasound2 is not configured yet.
dpkg: error processing lib32asound2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ia32-libs:
 ia32-libs depends on lib32asound2; however:
  Package lib32asound2 is not configured yet.
dpkg: error processing ia32-libs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on libasound2 (>> 1.0.24.1); however:
  Package libasound2 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-branding:
 firefox-branding depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 5.0+build1+nobinonly-0ubuntu0.11.04.2); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox; however:
  Package firefox is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of google-talkplugin:
 google-talkplugin depends on ia32-libs (>= 2.4); however:
  Package ia32-libs is not configured yet.
 google-talkplugin depends on ia32-libs-gtk; however:
  Package ia32-libs-gtk is not installed.
  Package ia32-libs which provides ia32-libs-gtk is not configured yet.
dpkg: error processing google-talkplugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of picasa:
 picasa depends on ia32-libs; however:
  Package ia32-libs is not configured yet.
 picasa depends on lib32asound2; however:
  Package lib32asound2 is not configured yet.
dpkg: error processing picasa (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python2.7-minimal
 python2.7
 libpython2.7
 libasound2
 lib32asound2
 ia32-libs
 firefox
 firefox-branding
 firefox-globalmenu
 firefox-gnome-support
 google-talkplugin
 picasa
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Thanks!

---

### Post by NightwishFan on 2011-09-20
Try removing python 2.7 if possible, though this is not a normal error, you must have added incompatible repositories. You probably should just back up data and reinstall.

---

