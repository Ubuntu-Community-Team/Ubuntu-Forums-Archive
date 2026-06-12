---
title: "Help with Adept"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Kolfinna on 2007-09-01
Good afternoon!
 
 I'm having some issues with certain packages within Adept and I'm not sure how to fix them...
 
 The two packages in question are sun-java6-bin and sun-java6-jre. It seems like every time I upgrade/install them, I get an error saying that the files are in a very bad/inconsistent state. When it tries to install anyway, the entire application hangs. I have to exit, go back to terminal, and run the dpkg --configure -a to be able to run Adept again.
 
 How can I get rid of the sun-java6 packages? They prevent me from updating anything else... I can't remove them because they're not installed yet, and can't quite get it to cancel the upgrade. 
 
 Thank you for your time and consideration,
 
 ~K

---

### Post by iamhugeinjapan on 2007-09-01
I don't have Adept installed myself, but is there any option in its menus to cancel all upgrades or can you search for the java packages and deselect them manually?

---

### Post by Kolfinna on 2007-09-01
I've tried... it still likes to re-select those two packages and try to install.

Here's the output of apt-get:

root@kolfinna-laptop:/home/kolfinna# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-sazanami-gothic
  ttf-sazanami-mincho
Recommended packages:
  gsfonts-x11
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded, 0 newly installed, 0 to remove and 158 not upgraded.
2 not fully installed or removed.
Need to get 0B/32.5MB of archives.
After unpacking 93.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
79929 files and directories currently installed.)
Preparing to replace sun-java6-bin 6-00-0ubuntu1~edgy1 (using .../sun-java6-bin_6-00-0ubuntu1~edgy1_i386.deb) ...

dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-00-0ubuntu1~edgy1_i386.deb (--unpack):
 subprocess pre-installation script killed by signal (Interrupt)
Selecting previously deselected package sun-java6-jre.
Preparing to replace sun-java6-jre 6-00-0ubuntu1~edgy1 (using .../sun-java6-jre_6-00-0ubuntu1~edgy1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-00-0ubuntu1~edgy1_all.deb (--unpack):
 subprocess pre-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-bin_6-00-0ubuntu1~edgy1_i386.deb
 /var/cache/apt/archives/sun-java6-jre_6-00-0ubuntu1~edgy1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by iamhugeinjapan on 2007-09-01
If download traffic is not an issue, you could try deleting the two deb files out of the /var/cache/apt/archives/ folder and redownloading after doing an apt-get update.

---

