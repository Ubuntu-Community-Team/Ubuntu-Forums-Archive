---
title: "Error when running Update Manager"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Scut_Farkus on 2008-02-15
Greetings!

I've run into a problem when running Update Manager.  It runs just fine, it grabs all the updates just fine, but when it starts to install the updates I get a message telling me about a corrupted file.  I tried getting the message again, but now it's telling me I can't remove or add anything because a software index is broken.  The error message tells me to run "sudo apt-get install -f" to fix it, but now I have a new error.  Please see screen shot.  I also took a screen shot of the terminal info on my original error message.  Any help would be greatly appreciated!  :)

---

### Post by Trail on 2008-02-15
Did you use synaptic? I seem to remember it has a "broken packages" filter on the left. It is intelligent enough to discover how to fix the dependancy issue. I had something similar once, and synaptic dealt with it successfully.

If it doesn't work maybe try to clean apt's cache, purge the offending package and retry... (I don't remember the command, search apt-cache's manual).

---

### Post by oedha on 2008-02-15
go to system - adinistration - synaptic
edit - fix broken packages
or
from terminal :==> sudo dpkg --reconfigure -a
then sudo apt-get update

---

### Post by kpkeerthi on 2008-02-15
Might want to clean the apt cache before trying "sudo apt-get install -f"
```
sudo aptitude clean
```

---

### Post by Scut_Farkus on 2008-02-15
Hey!

Thanks very much!

Broken package fixed!  I still have the original problem, though.  Can anyone help me with that?  

Thanks again for the help with the broken package.  Synaptic fixed it quickly with the edit broken packages option.

---

### Post by Golem XIV on 2008-02-15
The system is probably trying to read the downloaded file that has been corrupted for some reason.  I would first delete the cached file
```
sudo rm /var/cache/apt/archives/perl-modules_5.8.8-7ubuntu3.1_all.deb
```

and then either use the System Update app, Synaptic or terminal:
```
sudo apt-get update
```
to  refresh the repositories and
```
sudo apt-get update
```
to update the system.

<edit>Just in case, check you software sources (System -> Administration).  Maybe the mirror you're using is carrying a bad copy of the file.  Try using the Main Server </edit>

---

### Post by Scut_Farkus on 2008-02-15
*sigh*

Well, it seems I was premature in my joy at having fixed my broken package.  Every time I try to fix it, I get the same error message.  I have created another screen shot with more details.

Thanks, Golem....I did try to delete the cached file as you instructed.  I used copy and paste from your response so I wouldn't mistype anything.  Then I did the update and all seemed to go well.  When I tried to apply the updates I got the same error again.  I checked my software sources and MAIN is checked.  Did you want me to uncheck everything else and ONLY use MAIN?

Also, you gave me the same command twice.  Did you mean to do that?  I did it twice (just for grins), but perhaps you meant "sudo apt-get upgrade" as your other instruction?

---

### Post by Golem XIV on 2008-02-15
<slaps forehead>
Yes, it's** sudo apt-get update **to update the repositories list and **sudo apt-get upgrade** to upgrade the system.

---

### Post by Scut_Farkus on 2008-02-15
> **Golem XIV said:**
> <slaps forehead>
Yes, it's** sudo apt-get update **to update the repositories list and **sudo apt-get upgrade** to upgrade the system.

Thanks,  Tried that.  Here's what I get:

ed@ed-desktop:~$ sudo apt-get upgrade
[sudo] password for ed:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  perl: Depends: perl-modules (>= 5.8.8-7ubuntu3.1) but 5.8.8-7ubuntu3 is installed
E: Unmet dependencies. Try using -f.
ed@ed-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  perl-modules
The following packages will be upgraded:
  perl-modules
1 upgraded, 0 newly installed, 0 to remove and 176 not upgraded.
1 not fully installed or removed.
Need to get 0B/2310kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 88982 files and directories currently installed.)
Preparing to replace perl-modules 5.8.8-7ubuntu3 (using .../perl-modules_5.8.8-7ubuntu3.1_all.deb) ...
Unpacking replacement perl-modules ...
dpkg: error processing /var/cache/apt/archives/perl-modules_5.8.8-7ubuntu3.1_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/perl-modules_5.8.8-7ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ed@ed-desktop:~$ 

Any more ideas?  Anyone?  Bueller?  Bueller?

---

### Post by Scut_Farkus on 2008-02-15
> **oedha said:**
> go to system - adinistration - synaptic
edit - fix broken packages
or
from terminal :==> sudo dpkg --reconfigure -a
then sudo apt-get update

Also tried this, but no dice.  (Thanks anyway, dude.)

ed@ed-desktop:~$ sudo dpkg --reconfigure -a
[sudo] password for ed:
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
ed@ed-desktop:~$

---

### Post by vagrant on 2008-02-19
im having the same problem as the initial poster...tried the mentioned steps with no change in the result. I ran the update once after reinstalling and it worked but nothing after that. And when i search for packet names i know exist in the repository i get no hits, and for some i can find them but not install.

I have had this problem all of 7.10....

---

### Post by Scut_Farkus on 2008-02-19
Hey Vagrant,

You might do better to post your question as a separate problem.  My system ended up being REALLY unstable (not because of the suggestions here).  I was finally able to fix this (there's another post where I blow away the offending file in the archive folder...once that bad file is gone, Ubuntu grabs the good file and uses that)

After I fixed this error I got a slew of other nasty problems.  I don't know if my system is unstable, or if the ISO I grabbed has problems.  I tested the iso via instructions according to the sticky on the home page. I also tested my RAM and my Hard drive for errors and they're both okay.

The most stable version (for me) has been Dapper Drake.  I have since requested free disks directly from Canonical.  I know they might take a long time to get here, but I have a beginners book on Linux and it came with Dapper.  I'll learn using the book until the new version arrives and then I'll test it with the professional disks.

My sincere hope is that the new disks will solve my problems because I really like Ubuntu and I really like the Gutsy version.

Good luck!

---

