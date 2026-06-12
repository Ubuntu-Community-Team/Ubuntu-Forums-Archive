---
title: "Gutsy won't let me add or remove programs"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-02-22
I've been trying to streamline my laptop installation and I'm getting this error message in Synaptic and also apt-get:

> (Reading database ... dpkg: error processing firestarter (--remove):
 files list file for package `libxcb-shm0' is missing final newline
Errors were encountered while processing:


So I try autoremove and get this:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libxcb-shm0 (1.0-3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libxcb-shm0 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-base:
 kmplayer-base depends on libxine1 (>= 1.1.4); however:
  Package libxine1 is not configured yet.
dpkg: error processing kmplayer-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-konq-plugins:
 kmplayer-konq-plugins depends on kmplayer-base (= 0.9.4a-0ubuntu2); however:
  Package kmplayer-base is not configured yet.
dpkg: error processing kmplayer-konq-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxcb-shm0
 libxine1
 kmplayer-base
 kmplayer-konq-plugins
E: Sub-process /usr/bin/dpkg returned an error code (1)


I'm assuming that I've got some corrupt files that work with the installer packages, however I'm not sure how to go about correcting/removing them. 

Any suggestions?

---

### Post by Anicka on 2008-02-22
Could you try (in the terminal)```
dpkg -C
```It should check for problems and possible solutions. Please, post the out-put.

---

### Post by NeonSamurai on 2008-02-22
Thanks for the quick reply Anicka. Here's the readout:

> splendid@ooboontoo:~$ dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 kmplayer-base        Base files for KMPlayer
 libxine1             the xine video/media player library, binary files
 kmplayer-konq-plugins KMPlayer plugin for KHTML/Konqueror

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 libxcb-shm0          X C Binding, shm extension


So am I right in assuming that I should run dpkg -c kmplayer-base (for each package) to fix the problem?

---

### Post by PmDematagoda on 2008-02-22
Do:-
```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a
```
That should fix your problem.

---

### Post by Anicka on 2008-02-22
dpkg -C (with capital C) only checks for problems. As PmDematagoda says, you need to run "sudo dpkg --configure -a" (configures all packages that are not yet configured and for that you need superuser powers, hence "sudo" before the command).

---

### Post by NeonSamurai on 2008-02-22
Bah! No good. Thanks for the suggestion, but Ubuntu came back with this:

> [SIZE="1"]**splendid@ooboontoo:~$ sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libxcb-shm0 (1.0-3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libxcb-shm0 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-base:
 kmplayer-base depends on libxine1 (>= 1.1.4); however:
  Package libxine1 is not configured yet.
dpkg: error processing kmplayer-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-konq-plugins:
 kmplayer-konq-plugins depends on kmplayer-base (= 0.9.4a-0ubuntu2); however:
  Package kmplayer-base is not configured yet.
dpkg: error processing kmplayer-konq-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxcb-shm0
 libxine1
 kmplayer-base
 kmplayer-konq-plugins
E: Sub-process /usr/bin/dpkg returned an error code (1)
**splendid@ooboontoo:~$ sudo dpkg --configure -a**
Setting up libxcb-shm0 (1.0-3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libxcb-shm0 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-base:
 kmplayer-base depends on libxine1 (>= 1.1.4); however:
  Package libxine1 is not configured yet.
dpkg: error processing kmplayer-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-konq-plugins:
 kmplayer-konq-plugins depends on kmplayer-base (= 0.9.4a-0ubuntu2); however:
  Package kmplayer-base is not configured yet.
dpkg: error processing kmplayer-konq-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxcb-shm0
 libxine1
 kmplayer-base
 kmplayer-konq-plugins[/SIZE]


Are the lib files part of the package management system and is it a corruption there that is causing this?

---

### Post by Anicka on 2008-02-22
Ok, this should be possible to fix, so don't worry. Could you try this command```
sudo apt-get -f remove --purge libxcb-shm0
```If it fails run```
sudo dpkg -P libxcb-shm0
```and if that doesn't work```
sudo dpkg -P --force-remove-reinstreq libxcb-shm0
```Last command is potentionally dangerous, but I think it would be effective in this case.

Edit: [COLOR="Red"]Before installing this libxcb-shm0 package, delete the cache of it.[/COLOR]```
sudo rm /var/cache/apt/archives/libxcb-shm0*
```After that you reinstall any packages that you want.

Edit 2: You will probably be told to run "dpkg --configure -a", if so do that, but don't forget to put a "sudo" in front of it.

---

### Post by NeonSamurai on 2008-02-22
Thanks Anicka, been away fixing a printer, but now I'm back. Here's what's happened:

> splendid@ooboontoo:~$ sudo apt-get -f remove --purge libxcb-shm0
[sudo] password for splendid:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kmplayer-base* kmplayer-konq-plugins* libxcb-shm0* libxine1*
0 upgraded, 0 newly installed, 4 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7483kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing kmplayer-konq-plugins (--purge):
 files list file for package `libxcb-shm0' is missing final newline
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly


So then I did:

> splendid@ooboontoo:~$ sudo dpkg -P libxcb-shm0
(Reading database ... dpkg: error processing libxcb-shm0 (--purge):
 files list file for package `libxcb-shm0' is missing final newline
Errors were encountered while processing:
 libxcb-shm0
Processing was halted because there were too many errors.
splendid@ooboontoo:~$ sudo dpkg -P --force-remove-reinstreq libxcb-shm0
(Reading database ... dpkg: error processing libxcb-shm0 (--purge):
 files list file for package `libxcb-shm0' is missing final newline
Errors were encountered while processing:
 libxcb-shm0
Processing was halted because there were too many errors.


After that I tried:

> splendid@ooboontoo:~$ sudo rm /var/cache/apt/archives/libxcb-shm0*
splendid@ooboontoo:~$ sudo dpkg -P --force-remove-reinstreq libxcb-shm0
(Reading database ... dpkg: error processing libxcb-shm0 (--purge):
 files list file for package `libxcb-shm0' is missing final newline
Errors were encountered while processing:
 libxcb-shm0
Processing was halted because there were too many errors.
splendid@ooboontoo:~$ sudo apt-get -f remove --purge libxcb-shm0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kmplayer-base* kmplayer-konq-plugins* libxcb-shm0* libxine1*
0 upgraded, 0 newly installed, 4 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 7483kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing kmplayer-konq-plugins (--purge):
 files list file for package `libxcb-shm0' is missing final newline
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly


Then I checked:

> 
splendid@ooboontoo:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
splendid@ooboontoo:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-base:
 kmplayer-base depends on libxine1 (>= 1.1.4); however:
  Package libxine1 is not configured yet.
dpkg: error processing kmplayer-base (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxine1
 kmplayer-base


So those pesky files still don't want to go anywhere. Any other ideas I could try, or is it time to open up the HDD and try to located the corrupted area with a magnifying glass?

Cheers


Mark

---

### Post by Anicka on 2008-02-22
And this: ```
sudo dpkg --configure -a --force-configure-any
```

---

### Post by NeonSamurai on 2008-02-22
This is what happened:

> [SIZE="1"]splendid@ooboontoo:~$ sudo dpkg --configure -a --force-configure-any
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `kmplayer-base')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `kmplayer-base')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `kmplayer-base')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `kmplayer-base')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `kmplayer-base')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: also configuring `libxine1' (required by `libxine1')
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)[/SIZE]


'Core dumped' sounds pretty ominous. Any suggestions on my next step? Also, is it okay to post such long readouts here?

Cheers


Mark

---

### Post by vinutux on 2008-02-22
I think the problem related to post or pre scripts associated with dpkg


**[COLOR="Red"]Caution | Try your own risk[/COLOR]**

From my experience ...........press Alt+F2  --> gksu nautilus --> give password for permission (itz now root mode)

go to[COLOR="Red"]** /var/lib/dpkg/info**[/COLOR]  and look for pakages related to ur problamtic pakage (here is kmplayer) 

[COLOR="Orange"]***misteken delete may cause ur system unusable***[/COLOR]

delete all of those pakage named kmplayer (with pre or post) 

uninstall pakages using add/remove or synaptic .....................

---

### Post by Anicka on 2008-02-22
That was the longest out-put from dpkg I've ever seen. Maybe you have to install this libxcb-shm0 manually with force, to get it to work.

Can you check if it downloads when you run "sudo apt-get install -f libxcb-shm0" or you can dowload it from [http://packages.ubuntu.com/gutsy/i386/libxcb-shm0/download](http://packages.ubuntu.com/gutsy/i386/libxcb-shm0/download) and run "sudo dpkg -i --force-all /path/to/file/libxcb-shm0*" (/path/to/file/ would be /var/cache/apt/archive/ from the first option and ~/ or ~/Desktop from the second version depending where you put the file)

---

### Post by NeonSamurai on 2008-02-25
Here's what i get when I run the first command:

> splendid@ooboontoo:~$ sudo apt-get install -f libxcb-shm0
[sudo] password for splendid:
Sorry, try again.
[sudo] password for splendid:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxcb-shm0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libxcb-shm0 (1.0-3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libxcb-shm0 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-base:
 kmplayer-base depends on libxine1 (>= 1.1.4); however:
  Package libxine1 is not configured yet.
dpkg: error processing kmplayer-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-konq-plugins:
 kmplayer-konq-plugins depends on kmplayer-base (= 0.9.4a-0ubuntu2); however:
  Package kmplayer-base is not configured yet.
dpkg: error processing kmplayer-konq-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxcb-shm0
 libxine1
 kmplayer-base
 kmplayer-konq-plugins
E: Sub-process /usr/bin/dpkg returned an error code (1)


And the second:

> splendid@ooboontoo:~$ sudo dpkg -i --force-all /home/splendid/Desktop/libxcb-shm0*
Selecting previously deselected package libxcb-shm0.
(Reading database ... dpkg: error processing /home/splendid/Desktop/libxcb-shm0_1.0-3_i386.deb (--install):
 files list file for package `libxcb-shm0' is missing final newline
Errors were encountered while processing:
 /home/splendid/Desktop/libxcb-shm0_1.0-3_i386.deb
Processing was halted because there were too many errors.
splendid@ooboontoo:~$ 


Is it time to start ripping chunks out of the package manager?

---

### Post by Anicka on 2008-02-25
Can you do what vintux suggested, but for libxcb-shm0?```
cd /var/lib/dpkg/info
sudo rm libxcb-shm0.list
```

When you run "sudo dpkg --configure -a" it complained about "files list file for package `libxcb-shm0' is missing final newline". Deleting it should fix that, but you will have to reinstall it again, and hope for success...

I'm sorry, this is not exactly a dream problem, but I found this solution in the forums here [http://ubuntuforums.org/showpost.php?p=3861919&postcount=13](http://ubuntuforums.org/showpost.php?p=3861919&postcount=13) [COLOR="Red"]Do not follow the advise in the post on the top of the page, only the one in #13!!![/COLOR]

---

### Post by kroustou on 2008-02-25
hey man,why dont you try:
system>administrator>software sources
then enable downloads.....:guitar:

---

### Post by NeonSamurai on 2008-02-25
Cheers for continuing to help me on this Anicka. Your help is greatly appreciated.

Here's what I did:

> splendid@ooboontoo:/var/lib/dpkg/info$ sudo rm libxcb-shm0.list
[sudo] password for splendid:
rm: cannot remove `libxcb-shm0.list': No such file or directory


(This is baring in mind I'd already run the rm command once before.)

Then I tried this to install the faulty file:

> splendid@ooboontoo:/var/lib/dpkg/info$ sudo apt-get install libxcb-shm0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libxcb-shm0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up libxcb-shm0 (1.0-3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libxcb-shm0 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libxine1:
 libxine1 depends on libxcb-shm0; however:
  Package libxcb-shm0 is not configured yet.
dpkg: error processing libxine1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-base:
 kmplayer-base depends on libxine1 (>= 1.1.4); however:
  Package libxine1 is not configured yet.
dpkg: error processing kmplayer-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kmplayer-konq-plugins:
 kmplayer-konq-plugins depends on kmplayer-base (= 0.9.4a-0ubuntu2); however:
  Package kmplayer-base is not configured yet.
dpkg: error processing kmplayer-konq-plugins (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libxcb-shm0
 libxine1
 kmplayer-base
 kmplayer-konq-plugins
E: Sub-process /usr/bin/dpkg returned an error code (1)
splendid@ooboontoo:/var/lib/dpkg/info$ 


Should I be running $ sudo apt-get install libxcb-shm0.list $ instead?

---

### Post by spiderbatdad on 2008-02-25
```
sudo apt-get update && sudo apt-get dist-upgrade
```

```
 sudo dpkg --purge -a
```

---

### Post by vinutux on 2008-02-26
TRY this plz


press Alt+F2 --> gksu nautilus --> give password for permission (itz now root mode)

go to /var/lib/dpkg/info and look for pakages related to ur problamtic pakage (here is libxcb-shm0) 

**[COLOR="Red"]misteken delete may cause ur system unusable[/COLOR]**

delete all of those pakage named libxcb-shm0 (with pre or post) 

reinstall pakage using add/remove or synaptic .....................


:guitar:

---

### Post by 5phinX on 2008-02-26
I had the same problem but this works for me: [http://ubuntuforums.org/showthread.php?t=654692](http://ubuntuforums.org/showthread.php?t=654692)

---

