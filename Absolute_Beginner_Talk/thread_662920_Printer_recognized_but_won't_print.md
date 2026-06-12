---
title: "Printer recognized but won't print"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by boobahzone on 2008-01-09
I recently installed Ubuntu 7.10 on a Dell Dimension 4550 and have been having some printer problems.  Namely, my printer configuration recognizes my Canon Pixma MP160 as being connected to the computer, but when I go print a test page I get an error message on my screen reading "CUPS server error.  There was an error during the CUPS operation: 'client-error-document-format-not-supported'."

Now, from reading other posts and online articles from people who have experienced similar problems, it seems that the answers they've pointed to are that I need to install the correct printer drivers (e.g., [http://ubuntuforums.org/showthread.php?t=602883](http://ubuntuforums.org/showthread.php?t=602883)).

I found an article ([https://answers.launchpad.net/ubuntu/+question/3742](https://answers.launchpad.net/ubuntu/+question/3742)) that instructed me to download the proper drivers for the MP160 and install them.  The files were available from the site [http://www.canon-asia.com/index.jsp?fuseaction=support&prod_type=bj_aio](http://www.canon-asia.com/index.jsp?fuseaction=support&prod_type=bj_aio) .  I followed the instructions (listed at [http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/](http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/)) to convert the rpm files (the drivers were as .rpm, not .deb) to .deb using alien, and then install them on my system.  Specifically, the code that I used to achieve this, after installing alien, was:
```
$sudo alien -k name-of-rpm-file.rpm
$sudo dpkg -i name-of-deb-file.deb
```.

The answers.launchpad site told me that I would need to download four .rpm driver files called cnijfilter-common_2.70-2, cnijfilter-mp160_2.70-2, scangearmp-common_1.00 and scangearmp-mp160_1.00.  I downloaded each file and converted it to .deb and installed it using the code listed above, but the printer still acts the same.  The printer configuration recognizes that I have a Canon Pixma MP160 but cannot print from any applications nor print a test page.

I saved the terminal output from when I attempted to correctly install the printer drivers, which is posted at the end of this post.  Is there something I am not doing correctly to install the drivers?  Could there be another reason my printer is recognized as being connected to the computer but will not function properly?

Thanks for any help!


The code/output from when I installed alien and tried to install the printer drivers:
```

kevin@ubuntu:~$ sudo apt-get update
[sudo] password for kevin:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_US
Get:1 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:2 http://us.archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Get:3 http://security.ubuntu.com gutsy-security Release [51.2kB]
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Get:5 http://us.archive.ubuntu.com gutsy-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com gutsy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release       
Hit http://us.archive.ubuntu.com gutsy-updates Release
Get:6 http://us.archive.ubuntu.com gutsy-backports Release [44.0kB]        
Get:7 http://security.ubuntu.com gutsy-security/main Packages [53.0kB]
Hit http://us.archive.ubuntu.com gutsy/main Packages                          
Hit http://us.archive.ubuntu.com gutsy/restricted Packages          
Hit http://us.archive.ubuntu.com gutsy/main Sources                 
Get:8 http://security.ubuntu.com gutsy-security/restricted Packages [14B]
Get:9 http://security.ubuntu.com gutsy-security/main Sources [9175B]
Get:10 http://security.ubuntu.com gutsy-security/restricted Sources [14B]
Get:11 http://security.ubuntu.com gutsy-security/universe Packages [29.9kB]
Hit http://us.archive.ubuntu.com gutsy/restricted Sources                 
Hit http://us.archive.ubuntu.com gutsy/universe Packages                  
Hit http://us.archive.ubuntu.com gutsy/universe Sources                   
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages                
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources                 
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages              
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages        
Get:12 http://security.ubuntu.com gutsy-security/universe Sources [4609B]      
Get:13 http://security.ubuntu.com gutsy-security/multiverse Packages [2903B]
Get:14 http://security.ubuntu.com gutsy-security/multiverse Sources [833B] 
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Get:15 http://us.archive.ubuntu.com gutsy-backports/main Packages [14.8kB]
Get:16 http://us.archive.ubuntu.com gutsy-backports/restricted Packages [14B]
Get:17 http://us.archive.ubuntu.com gutsy-backports/universe Packages [55.5kB]
Get:18 http://us.archive.ubuntu.com gutsy-backports/multiverse Packages [3175B]
Get:19 http://us.archive.ubuntu.com gutsy-backports/main Sources [5651B]
Get:20 http://us.archive.ubuntu.com gutsy-backports/restricted Sources [14B]
Get:21 http://us.archive.ubuntu.com gutsy-backports/universe Sources [11.1kB]
Get:22 http://us.archive.ubuntu.com gutsy-backports/multiverse Sources [1379B]
Fetched 288kB in 2s (133kB/s)   
Reading package lists... Done
kevin@ubuntu:~$ sudo apt-get install alien
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  debhelper gettext html2text intltool-debian libbeecrypt6 libneon25 librpm4
  po-debconf rpm
Suggested packages:
  lsb-rpm lintian dh-make cvs gettext-doc
Recommended packages:
  libmail-sendmail-perl libcompress-zlib-perl
The following NEW packages will be installed:
  alien debhelper gettext html2text intltool-debian libbeecrypt6 libneon25
  librpm4 po-debconf rpm
0 upgraded, 10 newly installed, 0 to remove and 20 not upgraded.
2 not fully installed or removed.
Need to get 0B/4228kB of archives.
After unpacking 15.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)'
in the drive '/cdrom/' and press enter

Err cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main html2text 1.3.2a-3build1
  Unable to unmount the CD-ROM in /cdrom/, it may still be in use.
Get:1 http://us.archive.ubuntu.com gutsy/main html2text 1.3.2a-3build1 [90.6kB]
Get:2 http://us.archive.ubuntu.com gutsy/main gettext 0.16.1-2ubuntu3 [1552kB]
Get:3 http://us.archive.ubuntu.com gutsy/main intltool-debian 0.35.0+20060710.1 [31.6kB]
Get:4 http://us.archive.ubuntu.com gutsy/main po-debconf 1.0.9 [117kB]
Get:5 http://us.archive.ubuntu.com gutsy/main debhelper 5.0.51ubuntu3 [526kB]
Get:6 http://us.archive.ubuntu.com gutsy/main libbeecrypt6 4.1.2-6build1 [108kB]
Get:7 http://us.archive.ubuntu.com gutsy/main libneon25 0.25.5.dfsg-6build1 [103kB]
Get:8 http://us.archive.ubuntu.com gutsy/main librpm4 4.4.1-14.1ubuntu2 [991kB]
Get:9 http://us.archive.ubuntu.com gutsy/main rpm 4.4.1-14.1ubuntu2 [603kB]
Get:10 http://us.archive.ubuntu.com gutsy/main alien 8.68 [104kB]
Fetched 4228kB in 2m11s (32.0kB/s)                                             
Selecting previously deselected package html2text.
(Reading database ... 95650 files and directories currently installed.)
Unpacking html2text (from .../html2text_1.3.2a-3build1_i386.deb) ...
Selecting previously deselected package gettext.
Unpacking gettext (from .../gettext_0.16.1-2ubuntu3_i386.deb) ...
Selecting previously deselected package intltool-debian.
Unpacking intltool-debian (from .../intltool-debian_0.35.0+20060710.1_all.deb) ...
Selecting previously deselected package po-debconf.
Unpacking po-debconf (from .../po-debconf_1.0.9_all.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.51ubuntu3_all.deb) ...
Selecting previously deselected package libbeecrypt6.
Unpacking libbeecrypt6 (from .../libbeecrypt6_4.1.2-6build1_i386.deb) ...
Selecting previously deselected package libneon25.
Unpacking libneon25 (from .../libneon25_0.25.5.dfsg-6build1_i386.deb) ...
Selecting previously deselected package librpm4.
Unpacking librpm4 (from .../librpm4_4.4.1-14.1ubuntu2_i386.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../rpm_4.4.1-14.1ubuntu2_i386.deb) ...
Selecting previously deselected package alien.
Unpacking alien (from .../archives/alien_8.68_all.deb) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.5ubuntu16) ...
Setting up html2text (1.3.2a-3build1) ...

Setting up gettext (0.16.1-2ubuntu3) ...

Setting up intltool-debian (0.35.0+20060710.1) ...
Setting up po-debconf (1.0.9) ...
Setting up debhelper (5.0.51ubuntu3) ...
Setting up libbeecrypt6 (4.1.2-6build1) ...

Setting up libneon25 (0.25.5.dfsg-6build1) ...

Setting up librpm4 (4.4.1-14.1ubuntu2) ...

Setting up rpm (4.4.1-14.1ubuntu2) ...

Setting up alien (8.68) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kevin@ubuntu:~$ cd ~/root
bash: cd: /home/kevin/root: No such file or directory
kevin@ubuntu:~$ ls
Desktop    Downloads  Music     Public     Videos
Documents  Examples   Pictures  Templates
kevin@ubuntu:~$ cd Downloads
kevin@ubuntu:~/Downloads$ ls
cnijfilter-common-2.70-1.i386.rpm
cnijfilter-mp160-2.70-1.i386.rpm
install_flash_player_9_linux
OOOP-templates-separated-en-US-2.3.1.2.oxt
OOOP-templates-unified-en-US-2.3.1.2.oxt
scangearmp-common-1.00-2.i386.rpm
scangearmp-mp160-1.00-1.i386.rpm
TabBrowse.oxt
kevin@ubuntu:~/Downloads$ sudo alien -k cnijfilter-common-2.70-1.i386.rpm
cnijfilter-common_2.70-1_i386.deb generated
kevin@ubuntu:~/Downloads$ sudo alien -k snijfilter-mp160-2.70-1.i386.rpm
File "snijfilter-mp160-2.70-1.i386.rpm" not found.
kevin@ubuntu:~/Downloads$ sudo alien -k cnijfilter-mp160-2.70-1.i386.rpm
Warning: Skipping conversion of scripts in package cnijfilter-mp160: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
cnijfilter-mp160_2.70-1_i386.deb generated
kevin@ubuntu:~/Downloads$ sudo alien -k scangearmp-common-1.00-2.i386.rpm
Warning: Skipping conversion of scripts in package scangearmp-common: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
scangearmp-common_1.00-2_i386.deb generated
kevin@ubuntu:~/Downloads$ sudo alien -k scangermp-mp160-1.00-1.i386.rpm
File "scangermp-mp160-1.00-1.i386.rpm" not found.
kevin@ubuntu:~/Downloads$ sudo alien -k scangearmp-mp160-1.00-1.i386.rpm
scangearmp-mp160_1.00-1_i386.deb generated
kevin@ubuntu:~/Downloads$ sudo dpkg -i cnijfilter-common_2.70-1_i386.deb 
Selecting previously deselected package cnijfilter-common.
(Reading database ... 96405 files and directories currently installed.)
Unpacking cnijfilter-common (from cnijfilter-common_2.70-1_i386.deb) ...
Setting up cnijfilter-common (2.70-1) ...
kevin@ubuntu:~/Downloads$ sudo alien  -k cnijfilter-mp160-2.70-1.i386.deb
File "cnijfilter-mp160-2.70-1.i386.deb" not found.
kevin@ubuntu:~/Downloads$ ls
cnijfilter-common_2.70-1_i386.deb
cnijfilter-common-2.70-1.i386.rpm
cnijfilter-mp160_2.70-1_i386.deb
cnijfilter-mp160-2.70-1.i386.rpm
install_flash_player_9_linux
OOOP-templates-separated-en-US-2.3.1.2.oxt
OOOP-templates-unified-en-US-2.3.1.2.oxt
scangearmp-common_1.00-2_i386.deb
scangearmp-common-1.00-2.i386.rpm
scangearmp-mp160_1.00-1_i386.deb
scangearmp-mp160-1.00-1.i386.rpm
TabBrowse.oxt
kevin@ubuntu:~/Downloads$ sudo alien -k cnijfilter-mp160_2.70-1_i386.deb 
kevin@ubuntu:~/Downloads$ sudo dpkg -i cnijfilter-mp160_2.70-1_i386.deb 
Selecting previously deselected package cnijfilter-mp160.
(Reading database ... 96416 files and directories currently installed.)
Unpacking cnijfilter-mp160 (from cnijfilter-mp160_2.70-1_i386.deb) ...
Setting up cnijfilter-mp160 (2.70-1) ...
kevin@ubuntu:~/Downloads$ sudo dpkg -i scangearmp-common_1.00-2_i386.deb 
Selecting previously deselected package scangearmp-common.
(Reading database ... 96639 files and directories currently installed.)
Unpacking scangearmp-common (from scangearmp-common_1.00-2_i386.deb) ...
Setting up scangearmp-common (1.00-2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kevin@ubuntu:~/Downloads$ sudo dpkg - scangearmp-mp160_1.00-1_i386.deb 
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
kevin@ubuntu:~/Downloads$ sudo dpkg -i scangearmp-mp160_1.00-1_i386.deb 
Selecting previously deselected package scangearmp-mp160.
(Reading database ... 96682 files and directories currently installed.)
Unpacking scangearmp-mp160 (from scangearmp-mp160_1.00-1_i386.deb) ...
Setting up scangearmp-mp160 (1.00-1) ...

```

---

### Post by kyphi on 2008-01-09
As far as I know, the MP150 driver works with the Canon Pixma MP170 in Feisty - select HQI (Gutenprint).

Try it.

---

### Post by boobahzone on 2008-01-10
Thanks kyphi.  Here's I tried to use the MP150 driver but still can't get my printer to work.  When I finished the steps to use the MP150 driver (which are listed below), the "Print Test Page" option is disabled completely in my Printer Configuration application.

Maybe I went about using the MP150 driver wrong.  To install the MP150 driver, here is what I did:

1. I deleted the old printers in the "Printer Configuration" application.
2. I then clicked on the New Printer button
3. I then selected the device called "Canon MP160 USB#1"
4. Then, rather than selecting the make of my printer, I ticked the "provide PPD file" radio button and supplied the file called stp-bjc-MULTIPASS-MP150.5.1.ppd which I downloaded from the internet
5. Then, when I applied the settings, the printer showed up as a local printer, but now the test print button is disabled and I still cannot print from any other applications.


Also, when I select the make of my printer rather than "provide PPD file" the MP160 2.70 driver option does show up, and when I apply these settings the "Print test page" option is enabled.  However, when I go to print a test page, I get a confirmation message saying "Submitted. Test page submitted as job 1" (job 2, job 3, etc.) but nothing actually prints and my printer doesn't seem to react at all.  The printer is on, has paper, and works on another windows machine.

Is there a way that I can get my printer to properly work under Ubuntu?



Thanks!
Kevin

---

### Post by kyphi on 2008-01-10
There is quite a lot published on the net about these printers and perhaps one solution, since you have already accessed the Asian Canon website for the MP150 and MP160 drivers, is to access Turboprint for a driver.

[http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)

Unfortunately the scanner will probably give you similar problems.

I have a Canon scanner that is recognised in Ubuntu but will not function.  Canon provides very little support for its products for Linux users.

---

### Post by kyphi on 2008-01-10
About that link to Turboprint, I just realised that they want an outrageous amount of money for that driver.  You would be better off to buy another printer.

---

### Post by fcorourke on 2008-01-11
Hi -- I have a Canon MP160 and it was working and quit -- I installed  Gutenprint [from thread]  and then went went to print and still nothing. I then opened the printer looked for drivers and set it as  MP 150 --- but I copied old information from the MP 160 as well and it prints out [slowly] a full color page showing from 10% to 100 % with no trouble and the scanner still works. Thanks -- I have to have a printer & you as a group solved my problem!  

            
Fred:KS

---

### Post by boobahzone on 2008-01-13
Well, I managed to figure out a way to get Ubuntu to recognize my printer, just in case anybody stumbles upon this post later on.  

What I did was I put in the Ubuntu Live CD and went through the steps to setup printers.  I used the driver for the MP150, which worked for my MP160.  When I saw that this worked, I simply reinstalled Ubuntu (I didn't have any important data on this hard drive) and went through the same steps and the printer worked.  For some reason, the same steps would not work until I reinstalled Ubuntu, perhaps I changed a file somewhere that prevented its proper use.

---

