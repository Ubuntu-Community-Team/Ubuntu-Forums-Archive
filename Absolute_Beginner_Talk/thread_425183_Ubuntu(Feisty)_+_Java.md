---
title: "Ubuntu(Feisty) + Java?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by ech0^ on 2007-04-27
I just installed the latest version of Feisty which installed perfectly and I'm really enjoying it.

I'm just trying to find out which package i need to install java? There is alot of packages and seems a bit daunting as to which i have to pick.


I don't know if i need to post any computer details or not, so if you need anything ask for details.


eCh0

---

### Post by theredcross on 2007-04-27
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Java_.26_Non-Media_Browser_Plug-ins)

generally, refer to this site for most of your basic issues like this, I've been using ubuntu for a year and linux for a few and I still keep going back to it for important information like this.

---

### Post by ech0^ on 2007-04-27
theredcross  , thanks very much

---

### Post by crav on 2007-04-27
First, you'll need to install the new version of Java:
```
sudo apt-get install sun-java5-jdk
```
This will get you Java 1.5, which I'm told is more stable than 1.6. For 1.6, simply replace the 5 with a 6. After this, you'll need to change the default virtual machine for Java:
```
sudo update-alternatives --config java
```

---

### Post by silkstone on 2007-04-27
See [http://ubuntuforums.org/showthread.php?t=422692&highlight=install+java](http://ubuntuforums.org/showthread.php?t=422692&highlight=install+java)

Gmaster1440's method worked for me, although it installs Java 1.6.0 instead of the latest 1.6.1 - I guess that's what's in the repo.

---

### Post by ech0^ on 2007-04-27
i get this message when i type


me@compt:~$ sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
me@compt:~$ 


any ideas.

---

### Post by theredcross on 2007-04-27
do you have any other terminals running apt? Do you have synaptic, adept, or dpkg running? because that is whats wrong, apt cannot run more than one instance at a given time.

---

### Post by ech0^ on 2007-04-27
None.

---

### Post by Hendrixski on 2007-04-27
oh that's an easy one:  either you have something else using apt (like another terminal window that's running apt-get whatever) of you have Synaptic open somewhere.

If it persists, just log out and log back in.  (notice, you never have to do this, sometimes it's just easier) (don't reboot, just log out & in)

---

### Post by ech0^ on 2007-04-27
I logged in and out and it worked.

this is what results.


sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  sun-java6-bin 
The following NEW packages will be installed:
  java-common sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/32.6MB of archives. After unpacking 93.6MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 91331 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.25ubuntu2_all.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-fonts.
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-00-2ubuntu2_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-00-2ubuntu2_i386.deb) ...
Setting up java-common (0.25ubuntu2) ...

Setting up sun-java6-jre (6-00-2ubuntu2) ...

Setting up sun-java6-bin (6-00-2ubuntu2) ...

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

then it has stopped.

---

### Post by Hendrixski on 2007-04-27
Also.. in the future... if you want to install Java... or ANYTHING
just search for it in synaptic.  :-) or if you like the terminal just type in "apt-cache search xxxxx" where xxxxx is what you're looking for

so apt-cache search java would give you
java6-a
java6-b
java-somethingelse
java-somethingyou-don't-wan-0.3

then you can apt-get install xxxxx, and it's cool because the <tab> button will autocomplete stuff for you.  or you can highlight it with you mouse and click both of the buttons at the same time and it'll paste it for you.  :-)

---

### Post by Hendrixski on 2007-04-27
> **ech0^ said:**
> I logged in and out and it worked.

this is what results.


sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  sun-java6-bin 
The following NEW packages will be installed:
  java-common sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/32.6MB of archives. After unpacking 93.6MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package java-common.
(Reading database ... 91331 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.25ubuntu2_all.deb) ...
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-fonts.
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-00-2ubuntu2_all.deb) ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-00-2ubuntu2_i386.deb) ...
Setting up java-common (0.25ubuntu2) ...

Setting up sun-java6-jre (6-00-2ubuntu2) ...

Setting up sun-java6-bin (6-00-2ubuntu2) ...

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

then it has stopped.

hhmmm... there's usually a little confirmation thing that pops up.. if you ever feel like something is botched, just remove it and try again :-) it's really easy

You can just unselect it on synaptic, or type
sudo apt-get remove xxxxxx
or if you want it totally deleted then sudo apt-get remove --purge xxxx
and then can re-install it.  
:-) hope that helps

---

### Post by theredcross on 2007-04-27
It should be opening a big blue box in your terminal to ask some questions about sun java (do you agree to the licencing agreement and such). i'd suggest first trying 
```
sudo apt-get install -f
```
then
```
sudo dpkg-reconfigure -a
```
when packages get stuck like this it can be a pain in the rear, i think there was a help.ubuntu page somewhere on this, i'll see if i can find it for you. but check that wiki again, there may just be something pertinent to this situation in there.

---

### Post by ech0^ on 2007-04-27
sudo dpkg-reconfigure -a trying this now.

---

### Post by whee on 2007-04-27
Here's an easy way to do it via synaptic:

1) Open synaptic
2) Click on "Search"
3) Type "jre"(without the quotes) in the searchfield
4) Check the following packages for installation: sun-java6-bin , sun-java6-jre , sun-java6-plugin
5) Restart any web browsers(Firefox/Opera/Etc.) you had running during the installation of those java packages.
6) That's it, you should be good to go. (maybe try testing it on some website that contains a Java6 applet)

---

### Post by ech0^ on 2007-04-27
whee, i tried that and in synaptic i only have under `jre`

docbook-jrefentry
sun-java5-jre ( installed )
sun-java6-jre ( installed )

YEt when i go to sites that have java it comes up with the applet cert then i accept and then "error loading java


and when i try sudo dpkg-reconfigure -a it stops on "resetting networking xxxxxxx" or something i couldn't remember it turned all my network off so i had to reboot. that happened twice too.

---

### Post by theredcross on 2007-04-27
ooook, lets try
```
sudo dpkg-reconfigure sun-java6
```
the network thing sounds like a problem for another day.

---

### Post by ech0^ on 2007-04-27
Package `sun-java6' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: sun-java6 is not installed.
effektz@r00t:~$

---

### Post by theredcross on 2007-04-27
did you try 
```
sudo apt-get -f install
```

---

### Post by ech0^ on 2007-04-27
effektz@r00t:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gappletviewer-4.1 fakeroot debhelper intltool-debian po-debconf dpkg-dev
  gcjwebplugin-4.1 fastjar html2text
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by theredcross on 2007-04-27
check synaptic to see if you have sun-java6-plugin and sun-java6-fonts installed, because if you are testing websites to see if it works you will need those as well.

---

### Post by ech0^ on 2007-04-27
they both wasnt, but ive installed them both now.

---

### Post by ech0^ on 2007-04-27
my java problem is now fixed ty.


you guys rock :)

---

### Post by theredcross on 2007-04-27
additionally, look for 'flashplugin-nonfree'.
you may to unlock the backports repo to get that one, but its important if you want java for web browsing.

---

