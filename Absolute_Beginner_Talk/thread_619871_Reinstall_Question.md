---
title: "Reinstall Question"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Locutus_of_Borg on 2007-11-21
Since my system is basically fscked and I am no longer able to install any packages, or upgrade at all, I've decided to just fresh install...again. :|

My question is, what is the bare minimum you'd suggest backing up?  Of course my /home directory, but is there another directory where all my programs I have previously installed are stored? I would really rather not spend several days reinstalling every application i have been accumulating over the last several months.

Also, is it possible to just export these directories to another partition on the same hard dive, then copy them over once i have the new install?

I'll continue trying to find a solution to 
```
(Reading database ... dpkg: error processing /var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb (--unpack):
failed in buffer_read(fd): files list for package `openoffice.org-common': Input/output error
Errors were encountered while processing:
/var/cache/apt/archives/libcupsys2_1.2.8-0ubuntu8.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
But no one anywhere seems to be able to fix this. :(

---

### Post by fastTalker on 2007-11-22
/etc is a good directory to back up.  it contains most of your config files.

if you have another partition available, just mount it and copy over the files you want to backup.

---

### Post by banewman on 2007-11-22
Some progs install to /opt. :)
In your /home/you folder will be dot files - hidden config files.
If you back them up and put them in your new /home/you folder you settings for different progs will be saved. :)

---

### Post by forestpixie on 2007-11-22
have you tried to do a dpkg audit - you might need sudo not sure

```
dpkg -C
```

it might tell you what to do to get rid of it, but I'm only guessing

also if you don't want to be downloading packages again you could try [aptoncd]("http://aptoncd.sourceforge.net/")

---

### Post by Locutus_of_Borg on 2007-11-23
dpkg -C didn't seem to do anything...

thanks for that link, but i cannot install anything at all on my computer without getting that buffer_read(fd) error.

I'll try backing up /etc and /opt if I can.

Thanks

---

### Post by erginemr on 2007-11-23
Hello,

If you Google the "failed in buffer_read(fd)" string, you will see that this error is very common in the Debian universe. Many threads point to the possibility that this may be a hard disk problem and suggest using "fsck" on your hard drive from the fail-safe terminal or from the Live CD.

The following sites point to fsck:
[http://ubuntuforums.org/archive/index.php/t-254528.html](http://ubuntuforums.org/archive/index.php/t-254528.html)
[https://answers.launchpad.net/ubuntu/+source/dpkg/+question/15287](https://answers.launchpad.net/ubuntu/+source/dpkg/+question/15287)

And the following site (esp. last post) has an iteresting idea:
[http://ubuntuforums.org/archive/index.php/t-352766.html](http://ubuntuforums.org/archive/index.php/t-352766.html)

---

### Post by Locutus_of_Borg on 2007-11-23
i tried ```
e2fsck -cc -C stdout /dev/sda2
``` from a live disk, and while it found a lot of errors, didnt fix this particular problem, 

that last link sounds promising though, i will try and implement that, as i am putting off a reinstall as much as possible.

thanks

---

### Post by erginemr on 2007-11-24
> **Locutus_of_Borg said:**
> i tried ```
e2fsck -cc -C stdout /dev/sda2
``` from a live disk, and while it found a lot of errors, didnt fix this particular problem, 

that last link sounds promising though, i will try and implement that, as i am putting off a reinstall as much as possible.

thanks

While you are on it, I am also suspecting the "openoffice.org-common" package. There is a database file, in which all installed Debian package details are stored. Could you please find the file:
/var/lib/dpkg/status

in your system and check the section for the package "openoffice.org-common". You may post that section (the one starts with Package: openoffice.org-common or something), so that I can compare it with my own. 

There should also be a backup file: /var/lib/dpkg/status-old

The following thread also discusses this issue:
[http://linuxmafia.com/faq/Debian/package-database-rebuild.html](http://linuxmafia.com/faq/Debian/package-database-rebuild.html)

Sorry for tossing in all those links, but I believe they may be somewhat related to your problem.

---

### Post by Locutus_of_Borg on 2007-11-24
Thank you for the help

This is from my status file:
```
Package: openoffice.org-common
Status: deinstall ok installed
Priority: optional
Section: editors
Installed-Size: 34932
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: openoffice.org
Version: 2.2.0-1ubuntu5
Replaces: openoffice.org-debian-files, openoffice.org-mimelnk, openoffice.org (<< 1.9), openoffice.org2-common, openoffice.org-l10n-en-us, openoffice.org-l10n-en, openoffice.org-calc (<< 2.0.4~rc1), openoffice.org-base (<< 2.0.4~rc1), openoffice.org-math (<< 2.0.4~rc1)
Provides: openoffice.org2-common, openoffice.org-l10n-en-us
Depends: dictionaries-common (>= 0.10) | openoffice.org-updatedicts, openoffice.org-core (>> 2.2.0) | openoffice.org-core-experimental (>> 2.2.0), desktop-file-utils, xml-core, openoffice.org-style-human | openoffice.org-style-crystal | openoffice.org-style-andromeda
Pre-Depends: dpkg (>= 1.10.24)
Recommends: openoffice.org-style-industrial, openoffice.org-style-human, openoffice.org-style-tango, openoffice.org-style-crystal, openoffice.org-style-andromeda, openoffice.org-style-hicontrast
Conflicts: openoffice.org-debian-files, openoffice.org-mimelnk, openoffice.org2-common, openclipart-openoffice.org (<= 0.17+dfsg-4), openoffice.org-debian-menus, openoffice.org-core (= 2.0.4~rc3-1), openoffice.org-base (= 2.0.4-4)
Conffiles:
 /etc/bash_completion.d/ooffice.sh 8846b111b72001ecf496e11bbf9507d7
 /etc/openoffice/psprint.conf 5b20eeaab16271ff318828608b981063
 /etc/openoffice/sofficerc f28f717e6ed37bfe95c6ccaee826a9cb
 /etc/openoffice/soffice.sh f91dcb8197ed32cabe5b43186e98fbd1
Description: OpenOffice.org office suite architecture independent files
 OpenOffice.org is a full-featured office productivity suite that provides
 a near drop-in replacement for Microsoft(R) Office.
 .
 This package contains the architecture-independent files of
 OpenOffice.org.
Original-Maintainer: Debian OpenOffice Team <debian-openoffice@lists.debian.org>
```

I appreciate all help I can get.  I will try and figure out what that link is telling me to do, but I am still quite new at Ubuntu and Linux in general.  But thanks again. :KS

---

### Post by erginemr on 2007-11-25
And mine is as follows:

```

Package: openoffice.org-common
Status: install ok installed
Priority: optional
Section: editors
Installed-Size: 35908
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: openoffice.org
Version: 1:2.3.0-1ubuntu5.1
Replaces: openoffice.org-debian-files, openoffice.org-mimelnk, openoffice.org (<< 1.9), openoffice.org2-common, openoffice.org-l10n-en-us, openoffice.org-l10n-en, openoffice.org-calc (<< 2.0.4~rc1), openoffice.org-base (<< 2.0.4~rc1), openoffice.org-math (<< 2.0.4~rc1), broffice.org (<< 2.2.1~rc1-1)
Provides: openoffice.org2-common, openoffice.org-l10n-en-us
Depends: dictionaries-common (>= 0.10) | openoffice.org-updatedicts, openoffice.org-core (>> 1:2.3.0), desktop-file-utils, xml-core, openoffice.org-style-human | openoffice.org-style-crystal | openoffice.org-style-andromeda
Recommends: openoffice.org-style-industrial, openoffice.org-style-human, openoffice.org-style-tango, openoffice.org-style-crystal, openoffice.org-style-andromeda, openoffice.org-style-hicontrast
Conflicts: openoffice.org-debian-files, openoffice.org-mimelnk, openoffice.org2-common, openclipart-openoffice.org (<= 0.17+dfsg-4), openoffice.org-debian-menus, openoffice.org-core (= 2.0.4~rc3-1), openoffice.org-base (<< 2.2.0-1), openoffice.org-writer (<< 2.2.0-1), openoffice.org-calc (<< 2.2.0-1), openoffice.org-impress (<< 2.2.0-1), openoffice.org-draw (<< 2.2.0-1), openoffice.org-math (<< 2.2.0-1)
Conffiles:
 /etc/bash_completion.d/ooffice.sh ae531b7299a760bc7e3961d9852fd10f
 /etc/openoffice/psprint.conf 5b20eeaab16271ff318828608b981063
 /etc/openoffice/sofficerc f28f717e6ed37bfe95c6ccaee826a9cb
 /etc/openoffice/soffice.sh b14448e3aacfeb3b1966568158b434fd
Description: OpenOffice.org office suite architecture independent files
 OpenOffice.org is a full-featured office productivity suite that provides
 a near drop-in replacement for Microsoft(R) Office.
 .
 This package contains the architecture-independent files of
 OpenOffice.org.
Original-Maintainer: Debian OpenOffice Team <debian-openoffice@lists.debian.org>

```

The only thing I can notice is that the version number is different (I am using OpenOffice ver. 2.3) and line:
Status: install ok installed
whereas yours say:
Status: deinstall ok installed

And I do not have the word "deinstall" anywhere in my "status" file.

Obviously we are looking at a wrong place in trying to find the source of the error. This is strange because the error message exactly says:

failed in buffer_read(fd): files list for package `openoffice.org-common': Input/output error

But we can also understand from this message that the package manager cannot read the real files given in the conffiles section, which brings us back to the idea of a hard drive error...

---

### Post by erginemr on 2007-11-25
There is a command in the apt-get system:
sudo apt-get install -f

that tries to find and fix the errors in the installed packages. Could you please also try this?

---

### Post by Locutus_of_Borg on 2007-11-25
I have tried -f install and just as when installing any package, it gets to "reading database ..." hangs there for a long time, then spits out that error message: "error processing <package.deb> failed in buffer_read(fd) files for package 'openoffice.org-common': Input/output error...." etc.

As per your link on the last page, do I just type the uncommented lines in terminal? I read through it a few times, but I'm not sure if it's exactly the same issue I am having, and with the warnings at the beginning, I didn't want to just jump right into it and try it out.

---

### Post by erginemr on 2007-11-25
Hello again,

Here is a link to a forum thread in Spanish:

[http://lists.debian.org/debian-user/2007/03/msg02505.html](http://lists.debian.org/debian-user/2007/03/msg02505.html)

and here is a "rough" translation of it via Google Translate:

> 
Automatically translated text:
Hello friends after a week with the problem at the end I settled on the forum debian-es, to remember the mistake boiled down to this:
Failed in buffer_read (fd): files list for package `libvisual0.2 ': Input / output error

Well, this error refers to the file libvisual0.2.list that he was corrupt and therefore gave me an error of input / output error read it. This file was corrupt poque referred to some files in a directorioa also was corrupt and hence the problem.
Solution:
1. Repairing the directory corrupt.
2. Get the file libvisual0.2.list another distribution like mine and copy it onto my maquína.

To solve the step 1. We use the fsck, started in single user mode and he spent fsck the partition in question, and it appeared that everything was fine, he spent the directory in question and it turned out that fsck not fixed anything, so I started in normal mode the machine and nautilus explored the directory corrupt, to do something that was activated because when I rebooted the machine will check the partition in question and now they find fault and managed. Well finally the filesystem was ok.

To solve the step 2. I went to the machine that has instalaro the same district. I copy the file in question and then copied to my machine into its corresponding directory, then I get update, upgrade aptitude, I crossed fingers and it worked! Finally after almost a week I was able to see how the aptitude upgrade finally worked!. Then to make sure that things esbata well desinstalé a package to see if they did not get the new bugs, and good everything will be alright.

Now I can continue to work on what it was.


I tried everything to manually corrupt the "/var/lib/dpkg/status" file but I could not get any arror of that sort. There is definitely something wrong in your file system. 

Therefore, you should focus on how to use "fsck" before mounting your hard drive and fix all the errors in it.

---

### Post by philinux on 2007-11-25
someone had a similar problem

[http://www.linuxforums.org/forum/ubuntu-help/108966-cannot-install-any-packages-updates.html](http://www.linuxforums.org/forum/ubuntu-help/108966-cannot-install-any-packages-updates.html)

At the bottom of the thread is a link to a script to rebuild the package database.

[http://linuxmafia.com/faq/Debian/package-database-rebuild.html](http://linuxmafia.com/faq/Debian/package-database-rebuild.html)

Have you looked in var/log messages to see if any disk read write errors?

---

### Post by Locutus_of_Borg on 2007-11-25
i can try downloading it through a live disk and copying it over maybe?

But I will also try fsck some more.




Phil: that's actually my thread, I thought perhaps someone that reads that forum who doesnt read this one, might come across it and have a solution ;p

---

