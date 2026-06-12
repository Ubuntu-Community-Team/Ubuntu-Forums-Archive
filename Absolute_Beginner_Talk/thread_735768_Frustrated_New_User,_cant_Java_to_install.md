---
title: "Frustrated New User, cant Java to install"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by bigbossjohnny on 2008-03-26
So I'm new here, figured I would install ubunto 6.06.1 on my Dell Inspirion 8100, 1Ghz, 512mb ram, 80gig HD.

That was completed successfully, now the fun part... JAVA !!! ggrrrrrr...
I downloaded to the desktop... did the whole chmod thing to make it into an executable. that seemed to work, then I ran the executable... ./jre-6u5-linux-i586.rpm.bin.... I get the Java Lic. agreement, I enter to the bottom and type in "YES", it starts and Im like oh yeaahhh, and then BAM, line 437, rpm.. Command not found.  tried several times and nothing.

Then I search on here and tried the apt-get install sun-java6-bin and I get the following, "E:  couldn't find package sun-java7-bin and im at the command line again.

So anyone got any ideas what is the problem, other than maybe user error :)

---

### Post by warp99 on 2008-03-26
You can get the sun-java libraries from the multiverse repositories, but you have to enable them. Open the Synaptic package manager then choose Settings > Repositories then tick the boxes "Universe", "Multiverse" and "Restricted". Close then "Reload". The package sun-java5-bin will be available for download with all of the correct dependencies. ;)

---

### Post by kalesh7 on 2008-03-26
the first problem could be anything, but most likely a missing dependency,
the second problem seems to be that you have not added the repositories,

ok now the easy way go to
system->administration->sypnatic package manager
enter password
go to
settings->repositories
in ubuntu software tab check the first 4, then close, it will ask to update, let it
serach for sun-java6-jre click on the package and select mark for installation, it will want to install some more stuff, let it
click apply, follow prompts
enjoy.

P.S. make sure you are connected to internet when following the above procedure(It may be self evident but I did make this mistake when I was just starting)

---

### Post by brownknight on 2008-03-26
> **bigbossjohnny said:**
> ...That was completed successfully, now the fun part... JAVA !!! ggrrrrrr...
I downloaded to the desktop... did the whole chmod thing to make it into an executable. that seemed to work, then I ran the executable... ./jre-6u5-linux-i586.rpm.bin....

Hi. Is your problem solved? You mentioned above that you are trying to install a .rpm package. Please note ubuntu uses .deb packages or packages in .tar.gz

Follow the suggestions above and post again if your problem is not solved. Also, you should upgrade ubuntu to the next version 7.04 as your version of ubuntu is  nearing the end for support. In >Systems >Administration>Upgrade Manager click on Distribution Upgrade

---

### Post by bigbossjohnny on 2008-03-26
ok thanks for the replies, when I get home from work I will try this all out and post back up.

---

### Post by bigbossjohnny on 2008-03-27
Ok so I tried repositories and that didnt help me either... in fact they were all 4 already checked. So I did a search sun, and Java.... I saw a few things there but nothing that even came close to what I need,  :confused:

---

### Post by bigbossjohnny on 2008-03-27
This is what I get below when I attempt to install the latest Java from Java's website. 
Notice the stupid command not found, bleeehhh !!!

I guess tmrw is another night.



Do you agree to the above license terms? [yes or no]
yes

Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-6u5-linux-i586.rpm
./jre-6u5-linux-i586-rpm.bin: line 437: rpm: command not found

---

### Post by brownknight on 2008-03-27
You are trying to install the wrong package. You are trying to install a .rpm package. Please use Linux self extracting file - not the Linux RPM. Then just follow the installation instructions and you should be ok.

---

