---
title: "Java6 Issue: Click OK?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by ambi.dexterous on 2007-11-13
I was following the instructions on [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Add-on_Applications](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Add-on_Applications) to try adding the Java plug-in mentioned by way of the Konsole application (sudo apt-get install sun-java6-plugin).  The Konsole came back with a window that requested I click OK but would not allow me to select that option.  I told the system to Edit, Send Signal, Continue, and there was no response.  I looked around to see if there were any ways to fix this issue presented and couldn't find anything.  I tried to get the thing to stop or cancel and that did nothing so I closed the Konsole.  Bad idea.  Now whenever I try to install anything it comes back with a message denying my request.

Example 1:
"Administrator"@galeofceres-desktop:~$ sudo apt-get install p7zip-full
[sudo] password for "Administrator":
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
"Administrator"@galeofceres-desktop:~$

Example 2:
"Administrator"@galeofceres-desktop:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 4B in 4s (1B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
"Administrator"@galeofceres-desktop:~$

I know I got myself into this mischief and it is possible I will not be able to correct the issue without re-installing Ubuntu.  It took days to rip most of an extensive music collection and figure out how to get the movies on You Tube to work (can't figure out which thing I did worked), so I am searching for an alternative.  E-mailing it to myself like I did the regular files so I can download it at a later time takes so long it would be pointless.  Help me, please. ](*,)

---

### Post by FuturePilot on 2007-11-13
It seems apt is still running in the background. If it doesn't go away you might want to give it a reboot. When you are asked to accept the license, you need to scroll all the down to the bottom of the license. There will be a check box you need to check.

---

### Post by ambi.dexterous on 2007-11-14
When is it supposed to ask me to accept the license, please?  I shut down and rebooted as suggested.  Same problems.

Attempt to upload updates through the Update Manager:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Attempt to Add/Remove programs with A/R application:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I opened Konsole to see if it would pop up there and found nothing, so I tried to do what the system was telling me to:
"Administrator"@galeofceres-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
"Administrator"@galeofceres-desktop:~$ sudo dpkg --configure -a
[sudo] password for "Administrator":
Setting up odbcinst1debian1 (2.2.11-16) ...
Setting up unixodbc (2.2.11-16) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
"Administrator"@galeofceres-desktop:~$

To test and see if the issue had been fixed I opened another Konsole window and started working on trying to get Google Earth to see if the issue had been corrected and the response was:
"Administrator"@galeofceres-desktop:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 4B in 4s (1B/s)
Reading package lists... Done
"Administrator"@galeofceres-desktop:~$ sudo aptitude install googleearth
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  googleearth-data
The following packages have been kept back:
  libpoppler-glib2 libpoppler2 poppler-utils sun-java6-bin
The following NEW packages will be installed:
  googleearth googleearth-data
0 packages upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 68.0MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)
"Administrator"@galeofceres-desktop:~$

I attempted to download the updates again and I got:
Software Index is Broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I'm not certain what this package manager "Synaptic" is exactly and the last time this happened I tried the "sudo apt-get install -f" in a Konsole terminal and it did not fix the issue.  I gave up after trying to use the boot disk last time to find the missing file f and simply re-loaded Ubuntu and started fresh again.  I would prefer not having to do that again but I will if there is no other alternative.  It I have to re-load Ubuntu, this will be my fourth load of Ubuntu in two weeks.  I suppose that happens when you're new to an OS and decide to fiddle with it, though.  Gotta find my limitations somehow... ;)

---

### Post by FuturePilot on 2007-11-14
Hmmm
E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)
I'm kind of lost on this one.

Ah, try reinstalling Java
```
sudo apt-get install --reinstall sun-java6-bin
```

---

### Post by ambi.dexterous on 2007-11-14
I tried it and it told me I needed to "apt-get install -f" so I tried that and it didn't work.  I figured using the Super User DO on it might get it going, so I did it and it came back to the original page from whence all my problems arose:

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474;
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;
 &#9474;                                                                           &#9646;
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;
 &#9474;                                                                           &#9618;
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;
 &#9474;                                                                           &#9618;
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;
 &#9474;     form, any other machine readable materials including, but not         &#9618;
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;
 &#9474;
 &#9474;                                  <Ok>
 &#9474;                                                                           &#9474;
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;


None of the directional buttons work on it with my mouse but when I pressed the down arrow on my keyboard I was able to reach the end of the licensing agreement.  No box to click on still and it won't allow my to use my mouse to click "OK."  This reminds me of some of the DOS programs I would use when I was small.  Sadly I have forgotten how to click OK in DOS.  I tried the Enter key without any response, I tried to click on it with my mouse, I tried the Edit => Send Signal => Continue Task, and I'm out of ideas now. :(

---

### Post by FuturePilot on 2007-11-14
Hit Tab, or Space. Can't remember which. It should highlight the <OK> then hit Enter

---

### Post by ambi.dexterous on 2007-11-14
I hit Tab first and it highlighted OK so I hit Enter and it went forward to a page with a Yes or No option so I used the arrow keys to get to the Yes so it would continue.  Now it seems to be fine since the system allowed me to install the updates and the screen is now showing:

[sudo] password for "Administrator":
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-bin: Depends: sun-java6-jre (= 6-03-0ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
"Administrator"@galeofceres-desktop:~$ agp-get -f install
bash: agp-get: command not found
"Administrator"@galeofceres-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts
The following NEW packages will be installed:
  sun-java6-jre
The following packages will be upgraded:
  sun-java6-bin
1 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
Need to get 0B/32.7MB of archives.
After unpacking 93.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jre.
(Reading database ...
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
103171 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-03-0ubuntu2_all.deb) ...
Preparing to replace sun-java6-bin 6-03-0ubuntu2 (using .../sun-java6-bin_6-03-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
Setting up sun-java6-jre (6-03-0ubuntu2) ...
Setting up sun-java6-bin (6-03-0ubuntu2) ...
No theme index file in '/usr/share/icons/sun-java6.png'.
If you really want to create an icon cache here, use --ignore-theme-index.
"Administrator"@galeofceres-desktop:~$

**Thank you very very much!** :biggrin:

---

### Post by FuturePilot on 2007-11-14
You're welcome! :)

---

