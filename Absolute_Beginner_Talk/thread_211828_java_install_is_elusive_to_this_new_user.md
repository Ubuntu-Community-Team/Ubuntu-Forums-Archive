---
title: "java install is elusive to this new user"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2006-07-08
I guess I am surprised at the trouble I'm having while attempting to install Java.

I use Firefox as distributed to the new user of Dapper Drake.

(1)  The 'click here to install' through the FireFox-activated button prompt does not work.

(2)  I downloaded the latest linux IA32 version from java.com to install manually.  It's version 1.5.0.07 and it's tagged as i586.  I managed to install it into Home, but I think it really needs to install into /usr/java or something like that.  It seems I do not have permissions for creating a new folder in, or in fact anything but read-only operations, in the /usr folder.

(3)  I have all multiverse and universal repositories enabled, but nothing going there either which isn't already supposedly installed.

(4)  I searched the forums and found a java development thread, tried the instructions in that thread, and still no luck.

Help?

Thank you.

---

### Post by BarfBag on 2006-07-08
I've had this happen to me before in another distro (*cough*SUSE*cough), but not in Ubuntu.  I could never get it fixed.  Have you tried installing it through apt-get or Automatix?

---

### Post by Average_Joe on 2006-07-09
I was eventually able to install Java (though not the latest version) using the instructions here:

[http://tinyurl.com/mwtnf](http://tinyurl.com/mwtnf)

Thanks!

---

### Post by catlett on 2006-07-09
It couldn't be easier to install. Just issue this command 
```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

---

### Post by Perfect Storm on 2006-07-09
If you want the latest version:

Download Java Runtime Environment (JRE) 5.0 Update 7: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick **Linux self-extracting file**. Download it to your **Desktop**.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
sudo update-alternatives --config java

```
When asking for which version you want to choose pick;
```
  3        /usr/lib/j2sdk1.5-sun/bin/java
```

Testing;
```
java -version
```


Making a Launcher for Java Control Center;
```
sudo gedit /usr/share/applications/java.desktop
```

fill in;

[b]
[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;
[/b]

Save and exit.
You can find it now under Applications tab ---> System Tools.

---

### Post by Average_Joe on 2006-07-09
WOW!!!  Thank you, AI !!!

---

### Post by nosam on 2006-07-10
Hey thanks alot A.I., that was painless! =D>

---

### Post by Epperly on 2006-07-11
Thank you A.I! :)

---

### Post by catlett on 2006-07-11
First, thanks for the launcher and the update. The repository install I used only had Java 1.5 update 6
The only issue ocurred when I ran the comands as an  update from 6 to 7. At the point where you select an alternative provider for java. Your selection  
```
3        /usr/lib/j2sdk1.5-sun/bin/java
```Wasn't listed as a choice for me. The choice that did give me 1.50_07 was this one
```
 4        /usr/lib/j2re1.5-sun/bin/java
```
Just thought I'd share the experience in case someone ends up on the thread and runs your commands to update from 1.50_06 to 1.50_07

Thanks again.

---

### Post by Perfect Storm on 2006-07-12
Ah, yes. Forgot to correct it from my SDK installation. My bad, but it seems people can figure it out by themself. That's good :KS

---

### Post by va3uxb on 2006-07-12
This doesn't seem to work on Dapper server for PPC architecture... I'm still new to Ubuntu but am not new to linux or computers.  It seems that the jre....i586.bin files aren't available in ppc version.  Any suggestions?  They have sources for jdk but I didn't see any sources for compiling jre.

Thanks!

---

### Post by catlett on 2006-07-12
The command I listed earlier, installs JRE 1.50_06. I used A.I.'s how to to update to 7 but you should be able to install the java runtime edition 1.5 update 6 with those comands.
The command came from the Dapper Guide. It doesn't say anything about it not being compatable with PPC (it doesn't say it is compatable either, but I'd rather think the glass is half full :D )
The guide uses extra repositories so I don't know what repository it is in. I would try it first and se what happens. The Dapper Guide link is in my signature.

```
sudo apt-get install sun-java5-jre sun-java5-plugin
```
This is how the guide describes this section
>  How to install J2SE Runtime Environment (JRE) with Plug-in for Mozilla Firefox

---

### Post by va3uxb on 2006-07-14
I tried those first but apt fails, it seems those java packages don't fully exist or something, for ppc.  I eventually got it installed using an ibm build.  It's apallingly slow, though.

Just doing java -version takes about 2 seconds to return a result.

The apt errors for those two packages were:
```
The following packages have unmet dependencies:
  sun-java5-jre: Depends: sun-java5-bin (= 1.5.0-06-1) but it is not installable or
                          ia32-sun-java5-bin (= 1.5.0-06-1) but it is not installable
E: Broken packages

Package sun-java5-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-plugin has no installation candidate
```

Thanks anyhow!

-Stephanie

---

### Post by Handyman's Special on 2006-07-25
[QUOTE=Artificial Intelligence;1231275]If you want the latest version:

Download Java Runtime Environment (JRE) 5.0 Update 7: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick **Linux self-extracting file**. Download it to your **Desktop**.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
sudo update-alternatives --config java

```
When asking for which version you want to choose pick;
```
  3        /usr/lib/j2sdk1.5-sun/bin/java
```

_________________
Here is what I see in my terminal:
After unpacking 29.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
hs@hs-ubuntu:~/Desktop$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libstdc++6-4.0-dev
  make
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales debian-keyring gcc-4.0-doc lib64stdc++6
  manpages-dev autoconf automake1.9 libtool flex bison gcc-doc libc6-dev-amd64
  lib64gcc1 libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libstdc++6-4.0-dev make
0 upgraded, 11 newly installed, 0 to remove and 106 not upgraded.
Need to get 8141kB of archives.
After unpacking 29.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
hs@hs-ubuntu:~/Desktop$

Good grief! It took me almost all day to download the file (/home/hs/Desktop/jdk-1_5_0_07-linux-i586.bin)


Now what is wrong? Please, someone help me.

HS

---

### Post by catlett on 2006-07-25
Java runtime edition 1.5 update 6 is in the repositories. It is 1 update behind the latest, which A.I.'s how to will give you but it is better than nothing.
To install it you need to enabel extra repositories. If you haven't , here is a how to.[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
Then run this command ```
sudo apt-get install sun-java5-jre sun-java5-plugin
```That gives you 1.5 update 6 with a plugin for firefox.

If you w2ant to go ahead and try A.I's method again, I would suggest updating your system first. It looks like you just installed and didn't update your system with the latest updates.
Update with these commands and then give it another try. If it stil gives an error, install 1.5-6
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

### Post by Handyman's Special on 2006-07-26
[QUOTE=catlett;1300745]Java runtime edition 1.5 update 6 is in the repositories. It is 1 update behind the latest, which A.I.'s how to will give you but it is better than nothing.
To install it you need to enabel extra repositories. If you haven't , here is a how to.[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)
______
I did that, then ran ```
sudo aptitude update
```
______
When I tried to run this code ```
sudo apt-get install sun-java5-jre sun-java5-plugin
``` I get this:

hs@hs-ubuntu:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre

I have been prepared  for this to be a little more difficult than Windows but I am feeling way in over my head.

What is wrong now?

By the way, I was able to run the jdk-1_5_0_07-linux-i586.bin (don't know why it did not accomplish what I needed - be able to run java applets in Firefox). This is making me crazy.

Thanks for the reply,
HS

---

### Post by Sef on 2006-07-26
> hs@hs-ubuntu:~$ sudo apt-get install sun-java5-jre sun-java5-plugin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre

Have you added multiverse to your repositories?  To check that, [click here]("https://help.ubuntu.com/community/Repositories/Ubuntu") for a howto on it.

---

### Post by lime4x4 on 2006-08-02
This is the error i'm getting and i'm guessing cause i can't install java-package when i try to install that package it says it can't find that name

john@ubuntu:~/Desktop$ sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
Package java-package is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package java-package has no installation candidate


john@ubuntu:~/Desktop$ fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
/usr/bin/fakeroot: line 150: make-jpkg: command not found

---

### Post by lime4x4 on 2006-08-02
ok went to debian package site and found a deb of java-package and installed it now when i run the following command i get a new error

john@ubuntu:~/Desktop$ fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.XXXX4XBnn7
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

---

### Post by catlett on 2006-08-02
Did you run the first command ```
sudo apt-get install build-essential
```That installs the compilers. They are used when you run
```
./configure
make 
sudo make install
```I say this because it looks like make is not installed on your system
```
make-jpkg: command not found
```If you did and there is still an error you can do this.
Backup your source list with this
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```Now you need to install the Dapper Guide source list.
Open the source list with 
```
sudo gedit /etc/apt/sources.list 
```Erase everything and put this in
```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free
```Update your repository cache
```
sudo apt-get update
```Then re-run this command 
```
sudo apt-get install sun-java5-jre sun-java5-plugin
```The source list is perfectly fine and has all the needed repos enabled but if you don't want this list and you want your old list back, then run
```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```

---

### Post by lime4x4 on 2006-08-02
yes i did and here is the output of it

john@ubuntu:~$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 43 not upgraded.

---

### Post by action09 on 2006-08-24
Hi,

The first thing i do after installing my Ubuntu (no, the second one) because the first one is to install firestater and make some fw rules :)

THe second thing is to backup the original sources.list files:
"sudo cp /etc/apt/sources.list  /etc/apt/sources.list.bak"
 

and to entirely remove all the comments (#) to add just few lines and if i choose to use universe or multiverse it's on one single line.

Like this:

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse



after that, doing a "sudo apt-get update && sudo apt-get install sun-java5-jre sun-java5-plugin" will work fin to install & run Java.

Hope this help.. :)

Ax

---

### Post by Verlager on 2006-08-24
I got it, nevermind,

---

### Post by shimrah on 2006-08-27
Thank you thank you thank you! :)

> **Artificial Intelligence said:**
> If you want the latest version:

Download Java Runtime Environment (JRE) 5.0 Update 7: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp) pick **Linux self-extracting file**. Download it to your **Desktop**.

```
cd Desktop
sudo apt-get install build-essential
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
sudo update-alternatives --config java

```
When asking for which version you want to choose pick;
```
  3        /usr/lib/j2sdk1.5-sun/bin/java
```

Testing;
```
java -version
```


Making a Launcher for Java Control Center;
```
sudo gedit /usr/share/applications/java.desktop
```

fill in;

[b]
[Desktop Entry]
Name=Java Control Center
Comment=Java Options & Configuration.
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;
[/b]

Save and exit.
You can find it now under Applications tab ---> System Tools.

---

### Post by matchstich on 2006-12-10
well, i went and did everything on here cept for i changed the number to reflect up date 10, this what i got. bash: fakeroot: command not found
any ideas?
thanks
sorry, i went back and redid some of the stuff on here and i got it . 
its listed in system tools
thanks yall

---

