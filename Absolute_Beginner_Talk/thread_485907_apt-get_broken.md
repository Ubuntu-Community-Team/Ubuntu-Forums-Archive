---
title: "apt-get broken"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by KriZo on 2007-06-27
Hi i've tried to install compiz fusion from this guide [http://ubuntuforums.org/showthread.php?t=481314&highlight=ubuntu+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=ubuntu+fusion)

but when i come to the part where i'm suposed to install compiz-gnome every thing goes wrong, here's what i've done:

krizo@krizo:~$ sudo apt-get install compiz # compiz-gnome
Reading package lists... Done
Building dependency tree
Reading state information... Done
compiz is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
compiz: Depends: compiz-decorator
compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


krizo@krizo:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
compiz-gnome
The following packages will be upgraded:
compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1294kB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
LANGUAGE = (unset),
LC_ALL = (unset),
LANG = "en_DK"
are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 135410 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb (--unpack):
trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
/var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


please help me i can't install any other applications now.

---

### Post by overdrank on 2007-06-27
> **KriZo said:**
> Hi i've tried to install compiz fusion from this guide [http://ubuntuforums.org/showthread.php?t=481314&highlight=ubuntu+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=ubuntu+fusion)

but when i come to the part where i'm suposed to install compiz-gnome every thing goes wrong, here's what i've done:

krizo@krizo:~$ sudo apt-get install compiz # compiz-gnome
Reading package lists... Done
Building dependency tree
Reading state information... Done
compiz is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
compiz: Depends: compiz-decorator
compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


krizo@krizo:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
compiz-gnome
The following packages will be upgraded:
compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
1 not fully installed or removed.
Need to get 0B/165kB of archives.
After unpacking 1294kB of additional disk space will be used.
Do you want to continue [Y/n]? y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
LANGUAGE = (unset),
LC_ALL = (unset),
LANG = "en_DK"
are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 135410 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb (--unpack):
trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
/var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070626~3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


please help me i can't install any other applications now.

Hi you might have done the same that I did which was bypassed the first command
*sudo apt-get remove compiz-core desktop-effects*
I did that thinking that compiz wasn't installed but in fact it comes with feisty!:p

---

### Post by KriZo on 2007-06-27
#1

Yes i did the excactly same fault as you but stil, i can't install any thing:

krizo@krizo:~$ sudo apt-get remove compiz-core desktop-effects
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package desktop-effects is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  compiz-plugins: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by overdrank on 2007-06-27
> **KriZo said:**
> #1

Yes i did the excactly same fault as you but stil, i can't install any thing:

krizo@krizo:~$ sudo apt-get remove compiz-core desktop-effects
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package desktop-effects is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  compiz: Depends: compiz-core but it is not going to be installed
          Depends: compiz-decorator
  compiz-gnome: Depends: compiz-gtk (= 1:0.3.6-1ubuntu13) but it is not going to be installed
  compiz-plugins: Depends: compiz-core (= 1:0.3.6-1ubuntu13) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Ok have you tried sudo apt-get -f install?:(

---

### Post by KriZo on 2007-06-27
#4

Yes i've tried sudo apt-get -f install, output is in my first post.

---

### Post by overdrank on 2007-06-27
> **KriZo said:**
> #4

Yes i've tried sudo apt-get -f install, output is in my first post.

Ok I did this the other night so it is by memory. I did have to go to Synaptic manager and repair some broken packages. So try that and you might have to search for the packages ( that is the message I got when I opened synaptic) Hope that works!:(

---

### Post by KriZo on 2007-06-27
#6

Thank you now I can use apt-get again.

---

### Post by overdrank on 2007-06-27
> **KriZo said:**
> #6

Thank you now I can use apt-get again.

Whew #-o glad it worked!

---

