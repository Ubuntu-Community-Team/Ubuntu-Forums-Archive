---
title: "Huuuuuuge Problem now"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by ma_prism on 2007-12-25
When trying to acess the update manager:

[B]Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/B]


With Add/Remove

[B]
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/B]

---

### Post by Capricori on 2007-12-25
Ok, did you try running 'sudo apt-get install -f' in a terminal?

---

### Post by SOULRiDER on 2007-12-25
Run those two commands the error message told you to right at the end and post results.

---

### Post by ma_prism on 2007-12-25
Yes.

---

### Post by Capricori on 2007-12-25
I'm guessing you still get the same error then?

Try running 'sudo dpkg --configure -a' in a terminal, and let us know what happens.

---

### Post by ma_prism on 2007-12-25
> marina@marina-desktop:~$ sudo apt-get install
[sudo] password for marina:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-games: Depends: gnome-games-data (= 1:2.20.1-0ubuntu1) but 1:2.20.0.1-0ubuntu2 is installed
  gnome-games-data: Depends: gnome-cards-data (= 1:2.20.0.1-0ubuntu2) but 1:2.20.1-0ubuntu1 is installed
  openoffice.org: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
  openoffice.org-base: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
  openoffice.org-calc: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
  openoffice.org-evolution: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
  openoffice.org-gnome: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
  openoffice.org-gtk: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
  openoffice.org-impress: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
                          Depends: openoffice.org-draw (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
  openoffice.org-math: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
  openoffice.org-writer: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
  python-uno: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed
E: Unmet dependencies. Try using -f.
marina@marina-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_CA     
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA     
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                  
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_CA             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_CA   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_CA    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [14B]
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [8655B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources [937B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources [27.5kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [833B]    
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources [1702B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages [7664B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages [1075kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources [1226kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources [306kB]   
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources [56.8kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources [2120B]
Fetched 2713kB in 5s (466kB/s)                            
Reading package lists... Done
marina@marina-desktop:~$ 




I just copy and pasted everything that happened... I never would have thought this would have been so technical or I wouldn't have switched :(

---

### Post by shareMenaPeace on 2007-12-25
Did it worked?
Because you didnt typed

```
sudo apt-get install -f
```

---

### Post by Capricori on 2007-12-25
Don't worry, it gets easier, and its usually worth it :)

In that screenshot, you havn't run the other command. Try 'sudo apt-get install -f', with the '-f' at the end.

---

### Post by ma_prism on 2007-12-25
> **Capricori said:**
> I'm guessing you still get the same error then?

Try running 'sudo dpkg --configure -a' in a terminal, and let us know what happens.

I still get the same errors.

---

### Post by ma_prism on 2007-12-25
> **Capricori said:**
> Don't worry, it gets easier, and its usually worth it :)

In that screenshot, you havn't run the other command. Try 'sudo apt-get install -f', with the '-f' at the end.

Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-draw_1%3a2.3.0-1ubuntu5.3_i386.deb
 /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

What happened.

---

### Post by Capricori on 2007-12-25
Hmm...
If it were me, I would try 'sudo dpkg --configure -a' again, for good luck :)

---

### Post by ma_prism on 2007-12-25
> **Capricori said:**
> Hmm...
If it were me, I would try 'sudo dpkg --configure -a' again, for good luck :)

Same errors.


Could this be a computer problem instead?


Also:


```
marina@marina-desktop:~$ sudo dpkg --configure -a
[sudo] password for marina:
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-draw on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-games-data (1:2.20.1-0ubuntu1) ...

Setting up evolution (2.12.1-0ubuntu1) ...
/usr/share/gconf/schemas/apps_evolution_shell.schemas:83: parser error : Entity 'quow' not defined
n version of Evolution, with major/minor/configuration level (for example &quow;
                                                                               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:89: parser error : Opening and ending tag mismatch: locale line 86 and locane
      </locane>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:92: parser error : Opening and ending tag mismatch: short line 92 and shorw
        <short>Versión de la configuración</shorw>
                                                    ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:101: parser error : attributes construct error
      <locale name="eu"?
                       ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:101: parser error : Couldn't find end of Start Tag locale line 101
      <locale name="eu"?
                       ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:104: parser error : Opening and ending tag mismatch: schema line 6 and locale
      </locale>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:136: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xE1 0x6D 0x65 0x3D
      <locale n&#65533;me="hi">
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : Specification mandate value for attribute name
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : attributes construct error
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : Couldn't find end of Start Tag locale line 181
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:184: parser error : Opening and ending tag mismatch: schemalist line 2 and locale
      </locale>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:310: parser error : Opening and ending tag mismatch: gconfschemafile line 1 and schema
    </schema>
             ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:314: parser error : Extra content at the end of the document
    <schema>
    ^
dpkg: error processing evolution (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
Setting up gnome-games (1:2.20.1-0ubuntu1) ...

dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math
 openoffice.org-gtk
 openoffice.org-calc
 evolution
 openoffice.org-writer
 python-uno
 evolution-plugins

```

---

### Post by Capricori on 2007-12-25
Whoa... that's a pretty long list of errors :S

I've had something similar before, I *think* it could be resolved by uninstalling the offending packages, using the --purge flag, to get rid of all the configuration files for those packages, and then reinstalling them.
However, this could be a pain... particularly evolution. If you have been using that for your email, then removing it with the --purge flag would mean losing your email, so you'd best have a backup.
I'd wait it out, see if anyone else comes up with a better solution first. Sorry :(

---

### Post by ma_prism on 2007-12-25
Well this really sucks!

Thanks for all the help anyways.

---

### Post by SOULRiDER on 2007-12-25
Try with these two commands
```
sudo aptitude update
sudo aptitude dist-upgrade
```

Please post results.

---

### Post by JillSwift on 2007-12-25
Try this sequence of commands:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install -f
```

---

### Post by ma_prism on 2007-12-25
> **SOULRiDER said:**
> Try with these two commands
```
sudo aptitude update
sudo aptitude dist-upgrade
```

Please post results.

Done.

```
marina@marina-desktop:~$ sudo aptitude update
[sudo] password for marina:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]                
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_CA        
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]           
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_CA   
Get:3 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_CA             
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_CA
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_CA
Get:4 http://archive.ubuntu.com gutsy Release.gpg [191B]
Ign http://archive.ubuntu.com gutsy/universe Translation-en_CA               
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_CA
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_CA
Ign http://security.ubuntu.com gutsy-security/main Translation-en_CA
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com gutsy-security Release
Hit http://archive.canonical.com gutsy Release                      
Ign http://archive.ubuntu.com gutsy/main Translation-en_CA         
Hit http://archive.ubuntu.com gutsy-updates Release
Hit http://security.ubuntu.com gutsy-security/restricted Packages               
Hit http://archive.ubuntu.com gutsy Release                          
Hit http://archive.canonical.com gutsy/partner Packages              
Hit http://security.ubuntu.com gutsy-security/main Packages          
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/restricted Sources     
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages      
Hit http://archive.ubuntu.com gutsy-updates/main Packages
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://archive.canonical.com gutsy/partner Sources
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://archive.ubuntu.com gutsy-updates/main Sources
Hit http://archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://archive.ubuntu.com gutsy/universe Packages
Hit http://archive.ubuntu.com gutsy/multiverse Packages
Hit http://archive.ubuntu.com gutsy/restricted Packages
Hit http://archive.ubuntu.com gutsy/main Packages
Hit http://archive.ubuntu.com gutsy/universe Sources
Hit http://archive.ubuntu.com gutsy/main Sources
Hit http://archive.ubuntu.com gutsy/multiverse Sources
Hit http://archive.ubuntu.com gutsy/restricted Sources
Fetched 4B in 0s (5B/s)
Reading package lists... Done
marina@marina-desktop:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be upgraded:
  openoffice.org-core openoffice.org-draw 
The following partially installed packages will be configured:
  evolution evolution-plugins openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-math 
  openoffice.org-writer python-uno 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/40.3MB of archives. After unpacking 2179kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 88935 files and directories currently installed.)
Preparing to replace openoffice.org-draw 1:2.3.0-1ubuntu5 (using .../openoffice.org-draw_1%3a2.3.0-1ubuntu5.3_i386.deb) ...
Unpacking replacement openoffice.org-draw ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-draw_1%3a2.3.0-1ubuntu5.3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: regarding .../openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb containing openoffice.org-core:
 openoffice.org-core conflicts with openoffice.org-draw (<< 1:2.3.0-1ubuntu5.3)
  openoffice.org-draw (version 1:2.3.0-1ubuntu5) is present and installed.
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb (--unpack):
 conflicting packages - not installing openoffice.org-core
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-draw_1%3a2.3.0-1ubuntu5.3_i386.deb
 /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
 openoffice.org-impress depends on openoffice.org-draw (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-draw on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
Setting up evolution (2.12.1-0ubuntu1) ...
/usr/share/gconf/schemas/apps_evolution_shell.schemas:83: parser error : Entity 'quow' not defined
n version of Evolution, with major/minor/configuration level (for example &quow;
                                                                               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:89: parser error : Opening and ending tag mismatch: locale line 86 and locane
      </locane>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:92: parser error : Opening and ending tag mismatch: short line 92 and shorw
        <short>Versión de la configuración</shorw>
                                                    ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:101: parser error : attributes construct error
      <locale name="eu"?
                       ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:101: parser error : Couldn't find end of Start Tag locale line 101
      <locale name="eu"?
                       ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:104: parser error : Opening and ending tag mismatch: schema line 6 and locale
      </locale>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:136: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xE1 0x6D 0x65 0x3D
      <locale n&#65533;me="hi">
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : Specification mandate value for attribute name
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : attributes construct error
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : Couldn't find end of Start Tag locale line 181
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:184: parser error : Opening and ending tag mismatch: schemalist line 2 and locale
      </locale>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:310: parser error : Opening and ending tag mismatch: gconfschemafile line 1 and schema
    </schema>
             ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:314: parser error : Extra content at the end of the document
    <schema>
    ^
dpkg: error processing evolution (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:2.3.0-1ubuntu5.3); however:
  Version of openoffice.org-core on system is 1:2.3.0-1ubuntu5.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org
 openoffice.org-evolution
 openoffice.org-gnome
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math
 openoffice.org-gtk
 openoffice.org-calc
 evolution
 openoffice.org-writer
 python-uno
 evolution-plugins
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done 
```

---

### Post by SOULRiDER on 2007-12-25
After doing those commands i Posted above try doing
```
 sudo aptitude install openoffice.org evolution evolution-plugins python-uno
``` that HAS to fix it...

---

### Post by ma_prism on 2007-12-25
> **SOULRiDER said:**
> After doing those commands i Posted above try doing
```
 sudo aptitude install openoffice.org evolution evolution-plugins python-uno
``` that HAS to fix it...

Wow.
It's fixed...

No more errors when trying to Add/Remove.

THANK YOU

```
marina@marina-desktop:~$ sudo aptitude install openoffice.org evolution evolution-plugins python-uno
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  openoffice.org-core openoffice.org-draw openoffice.org-impress 
The following partially installed packages will be configured:
  evolution evolution-plugins openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-math openoffice.org-writer python-uno 
1 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 37.8MB of archives. After unpacking 2179kB will be used.
The following packages have unmet dependencies:
  openoffice.org-core: Conflicts: openoffice.org-draw (< 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed and it is kept back.
  openoffice.org-impress: Depends: openoffice.org-draw (= 1:2.3.0-1ubuntu5.3) but 1:2.3.0-1ubuntu5 is installed and it is kept back.
  openoffice.org-draw: Depends: openoffice.org-core (= 1:2.3.0-1ubuntu5) but 1:2.3.0-1ubuntu5.3 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Upgrade the following packages:
openoffice.org-draw [1:2.3.0-1ubuntu5 (gutsy, now) -> 1:2.3.0-1ubuntu5.3
(gutsy-updates)]

Score is 120

Accept this solution? [Y/n/q/?] y
The following packages will be upgraded:
  openoffice.org-core openoffice.org-draw 
The following partially installed packages will be configured:
  evolution evolution-plugins openoffice.org openoffice.org-base 
  openoffice.org-calc openoffice.org-evolution openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-impress openoffice.org-math 
  openoffice.org-writer python-uno 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 40.3MB of archives. After unpacking 2179kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com gutsy-updates/main openoffice.org-draw 1:2.3.0-1ubuntu5.3 [2500kB]
Get:2 http://archive.ubuntu.com gutsy-updates/main openoffice.org-core 1:2.3.0-1ubuntu5.3 [37.8MB]
Fetched 40.3MB in 37s (1067kB/s)                                                
(Reading database ... 88935 files and directories currently installed.)
Preparing to replace openoffice.org-draw 1:2.3.0-1ubuntu5 (using .../openoffice.org-draw_1%3a2.3.0-1ubuntu5.3_i386.deb) ...
Unpacking replacement openoffice.org-draw ...
Preparing to replace openoffice.org-core 1:2.3.0-1ubuntu5 (using .../openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb) ...
Unpacking replacement openoffice.org-core ...
Setting up evolution (2.12.1-0ubuntu1) ...
/usr/share/gconf/schemas/apps_evolution_shell.schemas:83: parser error : Entity 'quow' not defined
n version of Evolution, with major/minor/configuration level (for example &quow;
                                                                               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:89: parser error : Opening and ending tag mismatch: locale line 86 and locane
      </locane>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:92: parser error : Opening and ending tag mismatch: short line 92 and shorw
        <short>Versión de la configuración</shorw>
                                                    ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:101: parser error : attributes construct error
      <locale name="eu"?
                       ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:101: parser error : Couldn't find end of Start Tag locale line 101
      <locale name="eu"?
                       ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:104: parser error : Opening and ending tag mismatch: schema line 6 and locale
      </locale>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:136: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xE1 0x6D 0x65 0x3D
      <locale n&#65533;me="hi">
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : Specification mandate value for attribute name
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : attributes construct error
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : Couldn't find end of Start Tag locale line 181
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:184: parser error : Opening and ending tag mismatch: schemalist line 2 and locale
      </locale>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:310: parser error : Opening and ending tag mismatch: gconfschemafile line 1 and schema
    </schema>
             ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:314: parser error : Extra content at the end of the document
    <schema>
    ^
dpkg: error processing evolution (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up openoffice.org-core (1:2.3.0-1ubuntu5.3) ...
Setting up openoffice.org-draw (1:2.3.0-1ubuntu5.3) ...

Setting up python-uno (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-writer (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-calc (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-impress (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-math (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-base (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-evolution (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-gtk (1:2.3.0-1ubuntu5.3) ...

Setting up openoffice.org-gnome (1:2.3.0-1ubuntu5.3) ...

Errors were encountered while processing:
 evolution
 evolution-plugins
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up evolution (2.12.1-0ubuntu1) ...
/usr/share/gconf/schemas/apps_evolution_shell.schemas:83: parser error : Entity 'quow' not defined
n version of Evolution, with major/minor/configuration level (for example &quow;
                                                                               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:89: parser error : Opening and ending tag mismatch: locale line 86 and locane
      </locane>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:92: parser error : Opening and ending tag mismatch: short line 92 and shorw
        <short>Versión de la configuración</shorw>
                                                    ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:101: parser error : attributes construct error
      <locale name="eu"?
                       ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:101: parser error : Couldn't find end of Start Tag locale line 101
      <locale name="eu"?
                       ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:104: parser error : Opening and ending tag mismatch: schema line 6 and locale
      </locale>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:136: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xE1 0x6D 0x65 0x3D
      <locale n&#65533;me="hi">
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : Specification mandate value for attribute name
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : attributes construct error
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:181: parser error : Couldn't find end of Start Tag locale line 181
      <locale name?"mk">
                  ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:184: parser error : Opening and ending tag mismatch: schemalist line 2 and locale
      </locale>
               ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:310: parser error : Opening and ending tag mismatch: gconfschemafile line 1 and schema
    </schema>
             ^
/usr/share/gconf/schemas/apps_evolution_shell.schemas:314: parser error : Extra content at the end of the document
    <schema>
    ^
dpkg: error processing evolution (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.12.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 evolution
 evolution-plugins
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done  
```

---

### Post by SOULRiDER on 2007-12-25
Awesome, now do this again, just in case
```
sudo aptitude dist-upgrade
```

---

### Post by ma_prism on 2007-12-25
> **SOULRiDER said:**
> Awesome, now do this again, just in case
```
sudo aptitude dist-upgrade
```

I still have errors, but instead of a whole list it's only 2 things :

Errors were encountered while processing:
 evolution
 evolution-plugins

---

### Post by SOULRiDER on 2007-12-25
Try
```
sudo aptitude clean
sudo aptitude update
sudo aptitude install evolution evolution-plugins
```

---

### Post by ma_prism on 2007-12-25
> **SOULRiDER said:**
> Try
```
sudo aptitude clean
sudo aptitude update
sudo aptitude install evolution evolution-plugins
```

Done, then I ran sudo aptitude dist-upgrade once again and it's still the same errors. 

Everything else is working, except images in Applications and such.

---

### Post by SOULRiDER on 2007-12-25
Sorru, but i cant help you further. Why dont you get on IRC and ask for help there? Im sure someone will be able to help you.
Check this out on how to connect if you dont know already [https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

---

