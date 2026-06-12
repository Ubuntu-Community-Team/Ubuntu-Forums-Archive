---
title: "help with java plugins"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Dino05 on 2007-11-06
Can someone please help me with installing recent java plugins. I'm runing feisty-fawn 7.04  2.6.20-16-generic. I want to install jre1.6.0_03.

This is what I get when run "about:plugins" in my browser :-


GCJ Web Browser Plugin 0.92

    File name: libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	GCJ 	class,jar 	Yes
application/x-java-applet 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-applet;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
application/x-java-bean 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-bean;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes

---

### Post by markharding557 on 2007-11-07
install sun java from the repository it will work

---

### Post by taurus on 2007-11-07
Applications -> Accessories- -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin sun-java6-fonts
java -version
```
Don't forget to shutdown firefox and open it again after you've installed java.

---

### Post by Dino05 on 2007-11-30
This is what I got after installing java from synaptic and and updating it to the current release :-

dino@junix:~$ java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)
dino@junix:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418) feisty/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done

**dino@junix:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin **sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  ttf-sazanami-gothic ttf-sazanami-mincho
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.5MB of archives.
After unpacking 93.2MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-bin 6-00-2ubuntu2 [26.2MB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-jre 6-00-2ubuntu2 [6324kB]                   
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-fonts 6-00-2ubuntu2 [1814B]                  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse sun-java6-plugin 6-00-2ubuntu2 [1392B]                 
Fetched 32.5MB in 17m37s (30.8kB/s)                                                                         
Preconfiguring packages ...
Selecting previously deselected package sun-java6-bin.
(Reading database ... 109948 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-fonts.
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-00-2ubuntu2_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-00-2ubuntu2_i386.deb) ...
Setting up sun-java6-jre (6-00-2ubuntu2) ...

[B]Setting up sun-java6-bin (6-00-2ubuntu2) ...

Setting up sun-java6-fonts (6-00-2ubuntu2) ...
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.

Setting up sun-java6-plugin (6-00-2ubuntu2) ...
[/B]
dino@junix:~$ java -version
java version "1.5.0_11"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_11-b03)
Java HotSpot(TM) Client VM (build 1.5.0_11-b03, mixed mode, sharing)
dino@junix:~$ 


Why is the java version still 1.5.0.11?

---

