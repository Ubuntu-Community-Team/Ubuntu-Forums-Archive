---
title: "Display issues, Hibernation and Desktop effect issues"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by src2206 on 2007-08-25
Hello

I use nVidia MX 4000 AGP card and I installed Ubuntu recently. I have installed the driver. Now as I try to set the the Monitor Refresh Rates, Ubuntu does not display all the available Refresh Rates properly though the supported resolutions are displayed accurately. I am using 1024x768 resolution, but the available refresh rates are shown as 52, 61, 62, 63, and 64. It is a dual boot system and in Windows I use the same resolution but with 70 as refresh rate. I tried the following command:

```
sudo dpkg-reconfigure xserver.xorg
```

but it is giving me the following output:

```
Package `xserver.xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed

```

I do not want to mess with the display much as because I had a very bad experience with the 6.10 version, and unfortunately I had to remove Ubuntu. 

So how can I fix this refresh rate issue?[B]

Secondly[/B], is Beryl get activated when Desktop Effect> Cube workspace is selected? When I activate the Desktop Effect I can not switch between workspaces anymore...rather no more multiple workspaces are available. So how can this be solved?

[B]
Lastly, [/B]I can put the PC into Hibernation but Ubuntu seems to be unable to start back. What can be done to make hibernation completely operational?

Thank you.

---

### Post by Majorix on 2007-08-25
> sudo dpkg-reconfigure xserver.xorg

Replace the . with a -, then it would read:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by src2206 on 2007-08-25
Thanks Majorix...it is working..now whats next?

---

### Post by dougfractal on 2007-08-28
Compiz Fusion is the new beryl.
[http://ubuntuforums.org/showthread.php?t=533476](http://ubuntuforums.org/showthread.php?t=533476)
 *Updated* Compiz Fusion Guide on Ubuntu 7.04

I find Hibernation a pain in ubuntu 

but try here
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)
 [HowTo]: Fix suspend and hibernate on laptops

---

### Post by src2206 on 2007-08-29
Thank you [[IMG]http://ubuntuforums.org/customavatars/avatar230202_1.gif[/IMG]]("http://ubuntuforums.org/member.php?u=230202") 			 			 				 					 					[dougfractal]("http://ubuntuforums.org/member.php?u=230202")

I shall post the feedback here.

Could you please tell me how can I solve the problem of display?

---

### Post by dougfractal on 2007-08-29
Tell me about your setup.
Run this script.

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by asmoore82 on 2007-08-29
> **src2206 said:**
> Hello
...
[B]
Lastly, [/B]I can put the PC into Hibernation but Ubuntu seems to be unable to start back. What can be done to make hibernation completely operational?

Thank you.

This one may have to be just a "Wait and See" ...

[http://ubuntuforums.org/showpost.php?p=3000074&postcount=3](http://ubuntuforums.org/showpost.php?p=3000074&postcount=3)

---

### Post by dougfractal on 2007-08-29
[B]
Hibernation[/B]
from [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)
> See also: [WWW] [https://launchpad.net/bugs/34043](https://launchpad.net/bugs/34043)

First: update your /etc/X11/xorg.conf and add an "Option "NvAGP" "1" line in the "Section "Device" :

Section "Device"
        ...
        Option          "NvAGP"       "1"
EndSection

Secondly: disable warm-booting the video hardware on resume by editing your /etc/default/acpi-support as follows :

...

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

...

If you don't have a suspend option, you need to manually enable ACPI_SLEEP in the same file. However, this should be enabled by default.



---

### Post by src2206 on 2007-08-30
> **dougfractal said:**
> Tell me about your setup.
Run this script.

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```
please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

Thank you

Please find the file attached as directed

---

### Post by dougfractal on 2007-08-30
Hi src2206

I've uploaded you info to my [http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml](http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml).

I have a question for you.
Do you find compiz a bit delayed, i.e. you click applications and then a second later the apps popup, infact everything just takes a second to happen.

I ask because I was testing out XGL and its smooth and instant.

---

### Post by src2206 on 2007-08-31
Hello dougfractal

> **dougfractal said:**
> Hi src2206

I've uploaded you info to my [http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml](http://fractaldimension.org.uk/ubuntu/xorg/xorg.xml).

Thank you :)

> **dougfractal said:**
>  I have a question for you.
Do you find compiz a bit delayed, i.e. you click applications and then a second later the apps popup, infact everything just takes a second to happen.

I ask because I was testing out XGL and its smooth and instant.

I have not installed beryl yet....so I am unable to tell you anything about this. I have tried the System>Preferences>Desktop Effect, but I find that sometimes it responds, sometimes does not.

I shall let you know about Beryl as soon as I install and use that.

Thank you.

---

### Post by src2206 on 2007-08-31
> **dougfractal said:**
> Compiz Fusion is the new beryl.
[http://ubuntuforums.org/showthread.php?t=533476](http://ubuntuforums.org/showthread.php?t=533476)
 *Updated* Compiz Fusion Guide on Ubuntu 7.04

Hello friend

OK I have installed compiz...and I shall let you know about the result in a short while.
Any idea?

---

### Post by src2206 on 2007-08-31
Ok here is the update:

The following problems I can see:

1. I can not anymore see multiple workspace either in the normal display or after enabling Desktop Effects (Compiz). How can I get it back?

2. As I activate CompizFusion, the Maximize, minimize and the Close buttons vanish from the title bar of any program window.

3. The Update Manager is continuously showing me that there is an Update available of Compiz Core, but no matter how many times I try to update, it keeps on showing me of its availability. I do not get any any error message but on the contrary it shows me that "Update successful, you may close this window. I tried the terminal window and the command line...but it is telling me that Compiz is already latest version.

Any idea?

Please advise.

Thank you.

[B]*****EDIT****

Bad news.....[/B]I uninstalled and reinstalled Compiz according to the guide that you have previously pointed. This time along with all the problems described earlier, anew one has been added. The "**Desktop Effect**" option which was used to be available under **System>Preferences is not available  anymore. :(**

---

### Post by dougfractal on 2007-08-31
This hope will fix your problem
> **dougfractal said:**
> I've automated the guide [http://fosswire.com/2007/08/11/compizfusion-updated-guide-for-ubuntu-704/](http://fosswire.com/2007/08/11/compizfusion-updated-guide-for-ubuntu-704/)

1) activate sudo
```
sudo echo "activate sudo"
```

2) run script
```
sudo apt-get --purge remove compiz* libcompizconfig0
sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev
#sudo gedit /etc/apt/sources.list
# autofix sources.list
sudo sed -i '/3v1deb.*eyecandy/d' /etc/apt/sources.list   #  remove Treviño's Ubuntu Repository
sudo sed -i '/ppa.dogfood.launchpad.net\/amaranth/d' /etc/apt/sources.list  #  remove amaranth Ubuntu Repository
echo "# Amaranth compiz Ubuntu Repository  (unsigned)
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse" | sudo tee -a /etc/apt/sources.list   #   add amaranth Ubuntu Repository

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager
```

3) check install
```
aptitude search ~icompiz -F "%20p %10v %10V %20d"
```

4) run compiz
```

compiz --replace &
ccsm
```

4)  sort any probs
>prefeneces>reset to defaults
>General Option>Desktop Size> Horizontal Virtual Size>4

---

### Post by src2206 on 2007-08-31
Thank you dougfractal

OK, here is the feedback:

Of Step 2:

>  sudo apt-get --purge remove compiz* libcompizconfig0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libgnome-compiz-manager0 for regex 'compiz*'
Note, selecting compiz-extra for regex 'compiz*'
Note, selecting libcompizconfig0 for regex 'compiz*'
Note, selecting ocaml-native-compilers for regex 'compiz*'
Note, selecting zinc-compiler for regex 'compiz*'
Note, selecting compiz-dev for regex 'compiz*'
Note, selecting lisp-compiler for regex 'compiz*'
Note, selecting compiz-gtk for regex 'compiz*'
Note, selecting compiz-kde for regex 'compiz*'
Note, selecting libsnmp-mib-compiler-perl for regex 'compiz*'
Note, selecting libcompizconfig-backend-gconf for regex 'compiz*'
Note, selecting compiz-config-ini for regex 'compiz*'
Note, selecting c-compiler-avr for regex 'compiz*'
Note, selecting gcc-avr instead of c-compiler-avr
Note, selecting gcompizthemer for regex 'compiz*'
Note, selecting haskell-compiler for regex 'compiz*'
Note, selecting ghc6 instead of haskell-compiler
Note, selecting c-compiler for regex 'compiz*'
Note, selecting fortran-compiler for regex 'compiz*'
Note, selecting compiz-plugins for regex 'compiz*'
Note, selecting libgnome-compiz-manager-dev for regex 'compiz*'
Note, selecting chill-compiler for regex 'compiz*'
Note, selecting chill-2.95 instead of chill-compiler
Note, selecting compilercache for regex 'compiz*'
Note, selecting c-sharp-2.0-compiler for regex 'compiz*'
Note, selecting mono-gmcs instead of c-sharp-2.0-compiler
Note, selecting compizconfig-settings-manager for regex 'compiz*'
Note, selecting ocaml-compiler-libs-3.09.2 for regex 'compiz*'
Note, selecting ocaml-compiler-libs instead of ocaml-compiler-libs-3.09.2
Note, selecting python-compizconfig for regex 'compiz*'
Note, selecting ocaml-best-compilers for regex 'compiz*'
Note, selecting ocaml-native-compilers instead of ocaml-best-compilers
Note, selecting objc++-compiler for regex 'compiz*'
Note, selecting compiz-freedesktop-dev for regex 'compiz*'
Note, selecting fortran95-compiler for regex 'compiz*'
Note, selecting gfortran-4.1 instead of fortran95-compiler
Note, selecting pnet-compiler for regex 'compiz*'
Note, selecting c-sharp-compiler for regex 'compiz*'
Note, selecting objc-compiler for regex 'compiz*'
Note, selecting compiz-bcop for regex 'compiz*'
Note, selecting java-compiler for regex 'compiz*'
Note, selecting pascal-compiler for regex 'compiz*'
Note, selecting java2-compiler for regex 'compiz*'
Note, selecting libgnome-compiz-manager for regex 'compiz*'
Note, selecting c++-compiler for regex 'compiz*'
Note, selecting libcompizconfig0-dev for regex 'compiz*'
Note, selecting compiz-fusion-plugins-extra for regex 'compiz*'
Note, selecting fp-compiler for regex 'compiz*'
Note, selecting compiz-compcomm-plugins-main for regex 'compiz*'
Note, selecting compiz for regex 'compiz*'
Note, selecting libcompizconfig-backend-kconfig for regex 'compiz*'
Note, selecting ada-compiler for regex 'compiz*'
Note, selecting gnat-4.1 instead of ada-compiler
Note, selecting compiz-core for regex 'compiz*'
Note, selecting gnome-compiz-manager for regex 'compiz*'
Note, selecting compiz-fusion-plugins-main for regex 'compiz*'
Note, selecting c-compiler-m68hc11 for regex 'compiz*'
Note, selecting gcc-m68hc1x instead of c-compiler-m68hc11
Note, selecting c-compiler-m68hc12 for regex 'compiz*'
Note, selecting gcc-m68hc1x instead of c-compiler-m68hc12
Note, selecting ocaml-compiler-libs for regex 'compiz*'
Note, selecting fortran77-compiler for regex 'compiz*'
Note, selecting compiz-gnome for regex 'compiz*'
Note, selecting libgnome-compiz-manager0-dev for regex 'compiz*'
The following packages will be REMOVED:
  compiz-core* compiz-gnome* compiz-plugins* compizconfig-settings-manager*
  libcompizconfig-backend-gconf* libcompizconfig0* python-compizconfig*
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7995kB disk space will be freed.
Do you want to continue [Y/n]? y
Abort.
srijan@srijan-desktop:~$** ources.list**
** bash: ources.list: command not found**
srijan@srijan-desktop:~$ sudo sed -i '/3v1deb.*eyecandy/d' /etc/apt/sources.list   #  remove Treviño's Ubuntu Repository
srijan@srijan-desktop:~$ sudo sed -i '/ppa.dogfood.launchpad.net\/amaranth/d' /etc/apt/sources.list  #  remove amaranth Ubuntu Repository
srijan@srijan-desktop:~$ echo "# Amaranth compiz Ubuntu Repository  (unsigned)
> deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
> deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse" | sudo tee -a /etc/apt/sources.list   #   add amaranth Ubuntu Repository
# Amaranth compiz Ubuntu Repository  (unsigned)
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
srijan@srijan-desktop:~$ 
srijan@srijan-desktop:~$ sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-managery
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_IN                  
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Translation-en_IN                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Translation-en_IN           
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_IN          
Get:5 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_IN      
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty Release.gpg                        
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Translation-en_IN             
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Translation-en_IN       
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_IN          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Translation-en_IN             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Translation-en_IN           
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release.gpg [191B]           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Translation-en_IN         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Translation-en_IN   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_IN    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_IN      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_IN    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_IN    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_IN      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_IN    
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_IN        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_IN      
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Translation-en_IN         
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Translation-en_IN       
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty Release                            
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_IN           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_IN     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_IN       
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_IN     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Packages                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/main Sources                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages                
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages                  
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages                
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Sources                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Packages                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/universe Sources                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) feisty-updates/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages   
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Sources       
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Sources         
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Sources       
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages            
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages      
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Sources
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Sources
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Sources
Fetched 8B in 2s (3B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  compiz-gnome: Depends: compiz-core (= 1:0.5.2-0ubuntu3~ppa4) but 1:0.5.5~git20070828+3v1ubuntu0 is installed
                Depends: compiz-plugins (= 1:0.5.2-0ubuntu3~ppa4) but 1:0.5.5~git20070828+3v1ubuntu0 is installed
E: Unmet dependencies. Try using -f.**Step 3**:

> desktop:~$ aptitude search ~icompiz -F "%20p %10v %10V %20d"
compiz-core                  1:0.5.5~gi 1:0.5.5~gi OpenGL window and compositing
compiz-gnome                 1:0.5.2-0u 1:0.5.2-0u OpenGL window and compositing
compiz-plugins               1:0.5.5~gi 1:0.5.5~gi OpenGL window and compositing
compizconfig-settings-manage 0.5.2+git2 0.5.2+git2 Compiz configuration settings
libcompizconfig-backend-gcon 0.5.2+git2 0.5.2+git2 Settings library for plugins 
libcompizconfig0             0.5.2-0ubu 0.5.2-0ubu Settings library for plugins 
python-compizconfig          0.5.2-0ubu 0.5.2-0ubu Compiz configuration system b

**Step 4**:

> :~$ compiz --replace &
[1] 6245
srijan@srijan-desktop:~$ ccsm/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070828
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'
I get windows without buttons as I described earlier.

Last but not the least: I could not find this option  [B]>prefeneces>reset to defaults under Systems.

:(

[/B]Please help.

Thank you for your continuous support.

---

### Post by dougfractal on 2007-08-31
> sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager
 the thing about using && means do the next bit only on successful complete.
> The following packages will be REMOVED:
compiz-core* compiz-gnome* compiz-plugins* compizconfig-settings-manager*
libcompizconfig-backend-gconf* libcompizconfig0* python-compizconfig*
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7995kB disk space will be freed.
Do you want to continue [Y/n]? y
Abort.
is a fail.
> You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
compiz-gnome: Depends: compiz-core (= 1:0.5.2-0ubuntu3~ppa4) but 1:0.5.5~git20070828+3v1ubuntu0 is installed
Depends: compiz-plugins (= 1:0.5.2-0ubuntu3~ppa4) but 1:0.5.5~git20070828+3v1ubuntu0 is installed
also a fail.

Fix
1)
> sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev

2)
> sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager

good luck

---

### Post by src2206 on 2007-09-01
Hello dougfractal

Thank you very much for your support

I ran all the above scripts and commands as you directed in the previous posts and the results seems to be okay, except the following  problems after Compiz Fusion is enabled:

[B][COLOR=DarkGreen]1. The program windows are still without the [SIZE=3]Close, Minimize and Maximize/Restore[/SIZE] button.[/COLOR]
[COLOR=Blue]
2. I [SIZE=3]can not[/SIZE] revert back to the Normal Desktop (ie without any visual effect) without restarting my PC. I [SIZE=3]do not[/SIZE] have the option "[SIZE=3]reset to Default[/SIZE]" yet.[/COLOR]

[COLOR=Red]3. The Synaptic Update Manager is continuously showing that " Compiz-Core" is available; and as I apply it is installing [SIZE=3]without[/SIZE] any error message, but the [SIZE=3]update icon remains[/SIZE].

[COLOR=Purple]4. I still [SIZE=3]do not have multiple workspaces[/SIZE], even the option is not available in the [SIZE=3]Right Click[/SIZE] menu.
[/COLOR][/COLOR] 
[/B]I could not see the cube effect yet though I have enabled it through Compiz Control Panel.
Please advise me on the solution of these problems. I sincerely need your help. :(:(:(

Regards

---

### Post by dougfractal on 2007-09-01
Very colourful!!!!!

2)    You are looking in the wrong place .  ** ccsm**  >prefeneces>reset to defaults
normal desktop **metacity --replace &**

It's good to say whats not working , but with out any logs or info  I can't help.

---

### Post by src2206 on 2007-09-01
> **dougfractal said:**
> Very colourful!!!!!

:D Thank you. Just tried to make things look different as well as trying to draw attention to the individuality.

> **dougfractal said:**
>  2)    You are looking in the wrong place .  ** ccsm**  >prefeneces>reset to defaults
normal desktop **metacity --replace &**

Thank you very much...found.

Well the **GUI** of CCSM (** ccsm**  >prefeneces>reset to defaults) **does not put the destop back to the Normal Desktop.....**on the contrary **it is setting the options of Compiz to Default options**.

The Command (**metacity --replace &) worked , **though the following message is displayed in the terminal window and the command prompt did not come back.

> srijan@srijan-desktop:~$ metacity --replace &
[1] 7970
srijan@srijan-desktop:~$ Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


What exactly does it point to?

> **dougfractal said:**
>  It's good to say whats not working , but with out any logs or info  I can't help.

Sorry dougfractal, my intention was not only to point out problems and I shall be very happy to provide you all the logs that you may need. Please tell me which logs you may need to look at and where can I find those logs. Please understand I am really new in this Linux OS and moreover I need to know it well enough to teach my sister to use Linux properly.

Regards

---

### Post by dougfractal on 2007-09-01
try 
> sudo apt-get -y remove --purge compiz compiz-core libcompizconfig0
sudo apt-get -y install compiz compizconfig-settings-manager 
note: I used '*' before thinking it was a wildcard infact it means purge.


> 3) check install
Code:
aptitude search ~icompiz -F "%20p %10v %10V %20d"

I need to see it, as the loss of window decorations is often connected to T's packages.

---

### Post by src2206 on 2007-09-01
Hello dougfractal

I thank you for your wholehearted support.

> **dougfractal said:**
> try 
 >  			 				sudo apt-get -y remove --purge compiz compiz-core libcompizconfig0
sudo apt-get -y install compiz
note: I used '*' before thinking it was a wildcard infact it means purge.

Should I use the above set of commands again to **Purge and reinstall** Compiz? Sorry for my poor understanding.

> **dougfractal said:**
>  I need to see it, as the loss of window decorations is often connected to T's packages.

Here is the output of the command you pointed above ( aptitude search ~icompiz -F "%20p %10v %10V %20d"):

[QUOTE]srijan@srijan-desktop:~$ aptitude search ~icompiz -F "%20p %10v %10V %20d"
compiz                       1:0.5.2-0u 1:0.5.2-0u OpenGL window and compositing
compiz-core                  1:0.5.2-0u 1:0.5.2-0u OpenGL window and compositing
compiz-fusion-plugins-extra  0.5.2+git2 0.5.2+git2 Collection of extra plugins f
compiz-fusion-plugins-main   0.5.2-0ubu 0.5.2-0ubu Collection of plugins from Op
compiz-gnome                 1:0.5.2-0u 1:0.5.2-0u OpenGL window and compositing
compiz-plugins               1:0.5.2-0u 1:0.5.2-0u OpenGL window and compositing
compizconfig-settings-manage 0.5.2+git2 0.5.2+git2 Compiz configuration settings
libcompizconfig-backend-gcon 0.5.2+git2 0.5.2+git2 Settings library for plugins 
libcompizconfig0             0.5.2-0ubu 0.5.2-0ubu Settings library for plugins 
python-compizconfig          0.5.2-0ubu 0.5.2-0ubu Compiz configuration system b


Thank you again.

---

### Post by dougfractal on 2007-09-01
cube try
> ccsm
>General Option>Desktop Size> Horizontal Virtual Size>4

window decorations try
> sudo apt-get install emerald

emerald --replace &   #  from compiz
compiz --replace emerald --replace &    # from metacity
metacity --replace &      # standerd gnome

---

### Post by src2206 on 2007-09-01
Thank you very much...as usual.

OK, all the effects of the Compiz seems to be working including the Cube :)

I have installed Emerald and while running Compiz used **emerald --replace to activate it. But I could not understand how exactly can I use the theme from emerald.** So the problem of missing buttons still remain and this seems to be the only remaining trouble.

---

### Post by dougfractal on 2007-09-01
Well I've managed to loose my window decorations, shortly after install emerald.

I removed installed and stopped all sort of apps. logged out, restarted  and even switched to aiglx (i have nvidia) but in the end the fix was to :-  

ccsm >preferences>reset to defaults.


I am now having trouble trying to break my window decorations !!!


>   457  aptitude search ~icompiz -F "%20p %10v %10V %20d"
  458  compiz --replace -c emerald
  459  compiz --replace  emerald  --replace
  460  sudo apt-get install emerald
  461  compiz --replace  emerald  --replace
  462  compiz --replace  & emerald  --replace
  463  compiz --replace  &&  emerald  --replace &
BROKE DECORATIONS  (one of the above commands) :(
  464  metcity --replace &
  465  metacity --replace &
  466  compiz --replace  &&  emerald  --replace &
  467  compiz --replace  & 
  468  metacity --replace &
  469  ps -e | grep compiz
  470  ps -A | grep compiz
  471  ps -A 
  472  pkill emerald
  473  compiz --replace  & 
  474  metacity --replace &
  475  pkill gtk-window-deco
  476  compiz --replace  & 
  477  gtk-window-decorator &
  478  gtk-window-decorator  --replace &
  479  sudo apt-get remove emerald
  480  metacity --replace &
  481  compiz --replace  & 
  482  sudo apt-get install emerald emerald-themes
  483  sudo apt-get remove emerald libemeraldengine0
  484  compiz --replace  & 
  485  metacity --replace &
  486  compiz --replace  & 
  487  sudo apt-get -y remove --purge compiz compiz-core libcompizconfig0
  488  sudo apt-get -y install compiz
  489  sudo apt-get -y install compiz compizconfig-settings-manager
  490  compiz --replace  & 
  491  metacity --replace &
  492  compiz --replace  & 
  493  metacity --replace &
  494  ps -A
  495  pkill avant-window-na
  496  compiz --replace  & 
  497  ccsm
  498  metacity --replace &
  499  compiz --replace  & 
  500  sudo reboot
  501  glxinfo
  502  gtk-window-decorator  --replace &
  503  emerald --replace
  504  cat xinfo.sh
  505  sudo apt-get install --reinstall libwnck*
  506  compiz --replace  & 
  507  metacity --replace &
  508  compiz --replace  & 
  509  ps -A
  510  pkill compiz.real
  511  pkill gtk-window-deco
  512  pkill compiz
  513  pkill  avant-window-na
  514  compiz --replace  & 
ccsm (from another term)  RESET == FIXED  :-)
  515  emerald --replace
  516  sudo apt-get install emerald
  517  emerald --replace
  518  compiz --replace  & 
  519  pkill  avant-window-na
  520  compiz --replace -c emerald --replace
  TRIED TO BREAK NO JOY :(


if RESET doesn't work
```
sudo echo "activate"
pkill compiz.real
pkill gtk-window-deco
pkill compiz
pkill  avant-window-na
metacity --replace &
sudo apt-get -y remove --purge compiz compiz-core libcompizconfig0
sudo apt-get -y install compiz compizconfig-settings-manager 
sudo apt-get -y install --reinstall libwnck*
compiz --replace  & 
ccsm  #   RESET
```


try 
CCSM>Window Decoration: enabled
CCSM>Window Decoration> command :  is set to "gtk-window-decorator --replace"

then try
does adding in xorg.conf in the  &#8220;Device&#8221; Section: **Option &#8220;XAANoOffscreenPixmaps&#8221;**  then [ctrl+alt+backspace] help?


I don't know where compiz logs its errors

---

### Post by dougfractal on 2007-09-01
Further Investigation of window decorator
compiz --replace emerald --replace   # BREAK
ccsm #  Reset to defaults   #  FIX

---

### Post by src2206 on 2007-09-02
Hello dougfractal

Thank you very much....you are great. :)

OK, now I think that all the problems are almost over...after adding the command in the window decoration almost everything is fixed, I can see all the three buttons, though it is using the default Ubuntu theme (please see the screen shot attached). I still can not use the Emerald themes.

Moreover **I [COLOR=Blue]can not[/COLOR] switch between the [COLOR=Red]workspaces[/COLOR]**. I can see the four workspaces in the right hand bottom corner of my task bar but I can not switch.

Please tell what to do.

PS: I have installed Beryl Manager, just to try a way to solve the problem and in turn help you too. :). Sorry I should have informed you in my last post, **but if you feel that I should uninstall it, I shall surely do**.

> Further Investigation of window decorator
compiz --replace emerald --replace   # BREAK
ccsm #  Reset to defaults   #  FIX

I tried these, but did not make much of a difference.

Thank you again.

---

### Post by dougfractal on 2007-09-02
Beryl Manager is fine for compiz managing,  there is compiz-icon  but you have to git install it and I've lost the howto.  (In git they are are at 0.6  and all our compiz is at 0.5.2)

from beryl-manager you should be able to open emerald and select a theme, (or make one)   
from beryl-manager you should be able to select window decorator > emerald

or 
>  compiz --replace & sleep 1; emerald --replace &  #  to start


Cube

does you cube spin on middle mouse drag?
what settings are ccsm > general options> desktop size.?  (screen shot)

---

### Post by src2206 on 2007-09-02
Thank you very much dougfractal Please find the feedback as follows.

> **dougfractal said:**
> Beryl Manager is fine for compiz managing,  there is compiz-icon  but you have to git install it and I've lost the howto.  (In git they are are at 0.6  and all our compiz is at 0.5.2)

from beryl-manager you should be able to open emerald and select a theme, (or make one)   
from beryl-manager you should be able to select window decorator > emerald

or 
>  			 				 compiz --replace & sleep 1; emerald --replace &  #  to start


I have kept Bereyl Manager. I can access Emeald Theme Manager from Beryl. But I am not sure how I can use those themes. there seem to be only one theme and a number of Engines available. Please see attached screen shots 1 and 2. **The first one shows the theme window of Emerald manager open and the second one shows the condition of the windows once the Compiz Theme is applied using Beryl**. I have used the command too but the same result is obtained.

> **dougfractal said:**
>  Cube

does you cube spin on middle mouse drag?
what settings are ccsm > general options> desktop size.?  (screen shot)

Please find the Screen shot 3 indicating the setting that you have asked for.

Regarding Cube: as I pointed earlier I cant even switch between the workspaces anymore once Compiz is enabled. If I have anything else opened in any other workspaces before Compiz runs, that can not be accessed anymore. Middle mouse drag does not spin the Cube. :(

Please tell me what else can be done.

---

### Post by dougfractal on 2007-09-02
I wish I new the command line for debugging/logging compiz

ccsm>Desktop>Viewport switcher: enable       #   mouse spin cube

themes:  There used to be emerald-themes  but this seems to have gone.  try google and download a theme. (Sorry I use gtk-theme)

I would remove workspace panel then add panel or disable cube enable Desktop
plane. Then enable cube.

I think you problem is a config file error  (but I have now idea which one)..

Also try create a new user account and login and test from there.

Good luck.

One Last thought.
I mentioned xsever-xgl before, I really like it. And gives compiz a very responsive experience. Also some features just work in xgl (cube gears). This I my experience and might not be the same for others.

If you what to try XGL here is the NVIDIA install.
.......

```
sudo echo "activate sudo"
```

```
sudo apt-get -y install dbus-x11 xsever-xgl
echo "[Desktop Entry]
Encoding=UTF-8
Name=Xgl Gnome
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application"   | sudo tee /usr/share/xsessions/xgl.desktop
echo "if [ \$(grep -c vidia /etc/X11/xorg.conf) -gt '0' ] ; then 
     Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
else   # ATI & Intel
      Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
fi
DISPLAY=:1
dbus-launch --exit-with-session gnome-session   # GNOME
#exec startkde   # KDE
#exec xfce4-session   # XFCE"  | sudo tee /usr/bin/startxgl.sh
sudo sed -i '1i#!/bin/bash'  /usr/bin/startxgl.sh
sudo chmod +x /usr/bin/startxgl.sh
echo "logout, change session \"Xgl Gnome\", login"
```

---

### Post by src2206 on 2007-09-03
> #exec startkde   # KDE
#exec xfce4-session   # XFCE"  | sudo tee /usr/bin/startxgl.sh

Will it install KDE instead of Gnome?

I shall post back the feedback about rest of your suggestions in a short while.

Thank you so very much.
Regards

---

### Post by src2206 on 2007-09-03
Great...the problem solved my changing the ccsm setting as you suggested. I can access my workspaces...yahoo!!!!!!!!!!!!!!! U R Great. :D

And yes I can add other themes too, I found by googling. Honestly I can't thank you enough.

Could you tell me that is there any setting which would enable me to send one program window from the task bar to another workspace by right clicking on it and choosing the appropriate workspace number? As can be done in metacity.

Should I still change to XGL? And if you advice me to do so is there any fall back option available?

BTW, the update manager is still showing that "Compiz Core" update is available?

Why?

Regards

---

### Post by dougfractal on 2007-09-03
> Could you tell me that is there any setting which would enable me to send one program window from the task bar to another workspace by right clicking on it and choosing the appropriate workspace number? As can be done in metacity.
That's strange. I recommend a new tread.

> Should I still change to XGL? And if you advice me to do so is there any fall back option available?   
I would recommed XGL if you find the compiz desktop expirence slower than metacity. 
XGL is seperate and runs on top of xorg.
by having an "Xgl gnome" session at login you can choose which one to use. 

> 
BTW, the update manager is still showing that "Compiz Core" update is available?
Lets hope it fixes its self when new updates come.

---

### Post by src2206 on 2007-09-03
Thank you. :)

I shall start a new thread as you advised.

Regarding XGL the following is the output I received in my terminal window after coping the whole script you have kindly provided here ([http://ubuntuforums.org/showpost.php?p=3297924&postcount=29):]("http://ubuntuforums.org/showpost.php?p=3297924&postcount=29%29:")

> srijan@srijan-desktop:~$ sudo apt-get -y install dbus-x11 xsever-xgl
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dbus-x11 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dbus-x11 has no installation candidate
srijan@srijan-desktop:~$ sudo -i
root@srijan-desktop:~# sudo apt-get -y install dbus-x11 xsever-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dbus-x11 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dbus-x11 has no installation candidate
root@srijan-desktop:~# echo "[Desktop Entry]
> Encoding=UTF-8
> Name=Xgl Gnome
> Comment=Start an Xgl Session
> Exec=/usr/bin/startxgl.sh
> Icon=
> Type=Application"   | sudo tee /usr/share/xsessions/xgl.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Xgl Gnome
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
root@srijan-desktop:~# echo "if [ \$(grep -c vidia /etc/X11/xorg.conf) -gt '0' ] ; then 
>      Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
> else   # ATI & Intel
>       Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
> fi
> DISPLAY=:1
> dbus-launch --exit-with-session gnome-session   # GNOME
> #exec startkde   # KDE
> #exec xfce4-session   # XFCE"  | sudo tee /usr/bin/startxgl.sh
if [ $(grep -c vidia /etc/X11/xorg.conf) -gt '0' ] ; then 
     Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
else   # ATI & Intel
      Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
fi
DISPLAY=:1
dbus-launch --exit-with-session gnome-session   # GNOME
#exec startkde   # KDE
#exec xfce4-session   # XFCE
root@srijan-desktop:~# sudo sed -i '1i#!/bin/bash'  /usr/bin/startxgl.sh
root@srijan-desktop:~# sudo chmod +x /usr/bin/startxgl.sh
root@srijan-desktop:~# echo "logout, change session \"Xgl Gnome\", login"
logout, change session "Xgl Gnome", login


After the above result I can find **XGL Gnome session under Option> Session**. But this session seems to be **unable to load**- I tried thrice. Every time it **brings me back to the Log On screen**. As I chose the default "Last Session" (which I think is the previous Gnome Session) I can log back again.

---

### Post by dougfractal on 2007-09-04
> Reading state information... Done
Package **dbus-x11** is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Thanks for sending a complete log, makes thing so much easier to debug.
dbus-x11 might be a gutsy thing.

sudo nano /usr/bin/startxgl.sh
dbus-launch --exit-with-session gnome-session # GNOME

to **dbus-launch -exit-with-session gnome-session # GNOME**
from 
[http://linuxcrypt.net/?p=34](http://linuxcrypt.net/?p=34)

---

### Post by src2206 on 2007-09-04
> **dougfractal said:**
> Thanks for sending a complete log, makes thing so much easier to debug.
dbus-x11 might be a gutsy thing.

sudo nano /usr/bin/startxgl.sh
dbus-launch --exit-with-session gnome-session # GNOME

to **dbus-launch -exit-with-session gnome-session # GNOME**
from 
[http://linuxcrypt.net/?p=34](http://linuxcrypt.net/?p=34)

Happy to help someone who is trying to help me selflessly...its my pleasure.

So should I run the script again incorporating the little change you pointed out and let you know the result?

Thanks and regards

---

### Post by src2206 on 2007-09-04
Hello dougfractal

I ran the following script:

> sudo apt-get -y install dbus-x11 xsever-xgl
echo "[Desktop Entry]
Encoding=UTF-8
Name=Xgl Gnome
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application"   | sudo tee /usr/share/xsessions/xgl.desktop
echo "if [ \$(grep -c vidia /etc/X11/xorg.conf) -gt '0' ] ; then 
     Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
else   # ATI & Intel
      Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
fi
DISPLAY=:1
dbus-launch -exit-with-session gnome-session   # GNOME
#exec startkde   # KDE
#exec xfce4-session   # XFCE"  | sudo tee /usr/bin/startxgl.sh
sudo sed -i '1i#!/bin/bash'  /usr/bin/startxgl.sh
sudo chmod +x /usr/bin/startxgl.sh
echo "logout, change session \"Xgl Gnome\", login"And the following is the output I received:

> srijan@srijan-desktop:~$ sudo apt-get -y install dbus-x11 xsever-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package dbus-x11 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package dbus-x11 has no installation candidate
srijan@srijan-desktop:~$ echo "[Desktop Entry]
> Encoding=UTF-8
> Name=Xgl Gnome
> Comment=Start an Xgl Session
> Exec=/usr/bin/startxgl.sh
> Icon=
> Type=Application"   | sudo tee /usr/share/xsessions/xgl.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Xgl Gnome
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
srijan@srijan-desktop:~$ echo "if [ \$(grep -c vidia /etc/X11/xorg.conf) -gt '0' ] ; then 
>      Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
> else   # ATI & Intel
>       Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
> fi
> DISPLAY=:1
> dbus-launch -exit-with-session gnome-session   # GNOME
> #exec startkde   # KDE
> #exec xfce4-session   # XFCE"  | sudo tee /usr/bin/startxgl.sh
if [ $(grep -c vidia /etc/X11/xorg.conf) -gt '0' ] ; then 
     Xgl :1 -fullscreen -ac -accel xv:fbo -accel glx:pbuffer &
else   # ATI & Intel
      Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
fi
DISPLAY=:1
dbus-launch -exit-with-session gnome-session   # GNOME
#exec startkde   # KDE
#exec xfce4-session   # XFCE
srijan@srijan-desktop:~$ sudo sed -i '1i#!/bin/bash'  /usr/bin/startxgl.sh
srijan@srijan-desktop:~$ sudo chmod +x /usr/bin/startxgl.sh
srijan@srijan-desktop:~$ echo "logout, change session \"Xgl Gnome\", login"
logout, change session "Xgl Gnome", login
After this I rebooted and chose "xgl gnome" as login session. After 2 or3 seconds I received an error message that "**your last session lasted only for 10 seconds**, ..........." (sorry can't remember the whole). Though I remember that the error message is logged at **~/.xsession error files**. Unfortunately I could not locate this file.

I tried **[COLOR=Red]sudo gedit ~/.xsession-erros file[/COLOR] **and** [COLOR=Blue]sudo gedit ~/.xsession-erros, [/COLOR]**[COLOR=Blue][COLOR=DimGray]and both cases gedit opened up files but none of those two contained any data.[/COLOR][/COLOR]  

I also tried the following:

> srijan@srijan-desktop:~$ ls -l .ICEauthority
-rw------- 1 srijan srijan 1575 2007-09-04 15:31 .ICEauthority
srijan@srijan-desktop:~$ ls -l .Xauthority
-rw------- 1 srijan srijan 125 2007-09-04 15:31 .Xauthority

Hope this helps you to understand.  :)

---

### Post by dougfractal on 2007-09-05
A new file has been added to xserver-xgl

**/etc/X11/Xsession.d/00xserver-xgl_start-server**  Its a new xgl autostart.
 
cat etc/X11/Xsession.d/00xserver-xgl_start-server
if you have a file then you don't need "gnome xgl" session

---

### Post by src2206 on 2007-09-14
Hello dougfractal

Sorry for this delayed response but I was out of station for quite some time.. and so the absence.

I ran the command as you said but the result is as follows:

> cat etc/X11/Xsession.d/00xserver-xgl_start-server
cat: etc/X11/Xsession.d/00xserver-xgl_start-server: No such file or directory


Thank you for all the help. :)

---

### Post by dougfractal on 2007-09-14
typo 

should have read
> cat **/**etc/X11/Xsession.d/00xserver-xgl_start-server

Can you state were you are at. and do you have xserver-xgl installed?
what is your frame rate?

---

### Post by src2206 on 2007-09-15
> **dougfractal said:**
> typo 

should have read
			 				cat **/**etc/X11/Xsession.d/00xserver-xgl_start-server

Hello dougfractal :)

Thank you for your reply. Here is the output:

> srijan@srijan-desktop:~$ cat /etc/X11/Xsession.d/00xserver-xgl_start-server
cat: /etc/X11/Xsession.d/00xserver-xgl_start-server: No such file or directory


> **dougfractal said:**
>  Can you state were you are at. and do you have xserver-xgl installed?
what is your frame rate?

Ummmmm...how am I supposed to find out all these? I tried to use "which -a xserver-xgl" and "which xserver-xgl", both did not return anything. Presently I am logging in Gnome envioronment- if that what you want to know.

Regards

---

### Post by dougfractal on 2007-09-15
> and do you have xserver-xgl installed?

CLI
> aptitude search xgl
i = installed   p= something else

GUI
**synaptic**   >> search  >> xgl

> sudo apt-get upgrade
sudo apt-get install xserver-xgl

> 
if that what you want to know.
How is you compiz expirence?





sudo

---

### Post by src2206 on 2007-09-15
Hello dougfractal

The result of aptitude command is as follows:

> p   python-wxglade                  - GUI designer written in Python with wxPyth
p   xserver-xgl                     - GL-based X server 

Now after searching the Synaptic package manager I found that xserver-xgl is not yet installed. So I have installed it. Now the aptitude command is resulting an "i" before xserver-xgl. So it appears to be alright. I shall try to log into xserver-xgl session again and let you know. :)

Regarding compiz, I would say it is fine, though I can not seem to able to use/see/activate all the effects. Unfortunately sudden pressure in my work is preventing from experimenting with it. I shall try to dig in further, :). I really like the Themes and I must thank you whole heartedly for opening the world of this wonderful visual experience to me. Please accept my gratitude. The best thing about these themes are that these generally do not slow down the system as a whole, which happens in windows. Though I won't say that everything is perfect but still this Compiz and the theme manager is great. BTW, I have found the Fusion Icon's debian installer package somewhere in their homepage.

Regards...

---

### Post by src2206 on 2007-09-15
Ok here is the update on xserver-xgl

This time the log in was successful (I got the audio alert), but I could not get the desktop load. the screen only showed something like a black and white wire mesh with the cross like mouse pointer...after that nothing. I had to forcefully restart the PC, ctrl+alt+del did not work.

Hope this helps you to understand.

---

### Post by dougfractal on 2007-09-15
Did you have to unistall xserver-xgl to get gnome running?

This is my last question to you (I hope) whats your present frame rate in glxgears ?

---

### Post by src2206 on 2007-09-16
No I did not uninstall xserver-glx. If I remember correctly, in one of your previous posts you told me that I just need to switch between the desktop environments in the Log in screen...presence of one will not affect the other (hope I have understood that correctly), so I will be able to use whichever I like.

Regarding frame Rate, how should I find it?

Regards

---

### Post by dougfractal on 2007-09-16
**glxgears**
a frame rate will appear at 5 sec intervals

> If I remember correctly, in one of your previous posts you told me that I just need to switch between the desktop environments in the Log in screen...presence of one will not affect the other (hope I have understood that correctly), so I will be able to use whichever I like.
I did say that but there has been a package change, which means if you install xserver-xgl then xgl starts automatically as default.

run my Xinfo.sh script again if your frame rate is faster than 1292 FPS

you can remove xgl  with 
sudo apt-get remove xserver-xgl

disable xgl
less /usr/share/xserver-xgl/xserver-xgl-notification.update-notifier
> Name: Xgl server setup changed
Priority: High
Terminal: False
DontShowAfterReboot: True
DisplayIf: true
Description: The Xgl server will now be started automatically next time you login.  It is no longer necessary to use any special X session to start Xgl, and such sessions will likely fail to work properly.  Please select a regular session from your session manager next time you log in.  To disable Xgl autostart for this user, create a file named **~/.config/xserver-xgl/disable**


---

### Post by tiggzy on 2007-09-16
much props to *dougfractal* .... i'd jus like to ask one question .....don't mean to hijack the thread ......... i ave a Nvidia geforce4 MX4000 128MB gfx card, is it better to use XGL or AIGLX ? 
thnx in advance :-D

---

### Post by dougfractal on 2007-09-16
tiggzy
> i ave a Nvidia geforce4 MX4000 128MB gfx card, is it better to use XGL or AIGLX ? 
I find XGL a lot better on my 7100 card and AIGLX unbareable. (the delay does my head in)
many will say that AIGLX should be better.
I say try it and let me know. ;-)

XGL may have problems with 3D games.

---

### Post by tiggzy on 2007-09-19
well ... i upgraded my drivers for nvidia ... and updated my xorg to 7.2 ..... and compiz-fusion is running excellently....no lag ...at all ....:) ...... i tink i'm staying wid the nvidia+ aiglx combo .. thnx for ur info non di less* dougfracta*l

---

### Post by src2206 on 2007-09-20
hello dougfractal :)

The following is the frame rate result with Compiz enabled:

> 4539 frames in 5.0 seconds = 907.446 FPS
2633 frames in 5.0 seconds = 526.599 FPS
4719 frames in 5.0 seconds = 943.704 FPS
4703 frames in 5.0 seconds = 940.464 FPS
4705 frames in 5.0 seconds = 940.908 FPS
4679 frames in 5.0 seconds = 935.747 FPS
4737 frames in 5.0 seconds = 947.299 FPS
4646 frames in 5.0 seconds = 928.872 FPS
4677 frames in 5.0 seconds = 934.766 FPS
1596 frames in 5.0 seconds = 319.168 FPS
4650 frames in 5.0 seconds = 929.981 FPS
3929 frames in 5.3 seconds = 745.184 FPS
13210 frames in 5.0 seconds = 2641.927 FPS
8598 frames in 5.1 seconds = 1688.352 FPS
8413 frames in 5.0 seconds = 1682.530 FPS
15476 frames in 5.0 seconds = 3095.146 FPS
19176 frames in 5.7 seconds = 3362.711 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

And following is with Compiz disabled (running metacity)

> 5393 frames in 5.0 seconds = 1078.596 FPS
2750 frames in 5.0 seconds = 549.897 FPS
2544 frames in 5.0 seconds = 508.728 FPS
2543 frames in 5.0 seconds = 508.440 FPS
2543 frames in 5.0 seconds = 508.536 FPS
2545 frames in 5.0 seconds = 508.802 FPS
2543 frames in 5.0 seconds = 508.594 FPS
2544 frames in 5.0 seconds = 508.797 FPS
2544 frames in 5.0 seconds = 508.793 FPS
2468 frames in 5.0 seconds = 493.472 FPS
2213 frames in 5.0 seconds = 442.465 FPS
2563 frames in 5.0 seconds = 512.410 FPS
2334 frames in 5.0 seconds = 466.794 FPS
2543 frames in 5.0 seconds = 508.555 FPS
2543 frames in 5.0 seconds = 508.464 FPS
2544 frames in 5.0 seconds = 508.764 FPS
2543 frames in 5.0 seconds = 508.543 FPS
2543 frames in 5.0 seconds = 508.542 FPS
X connection to :0.0 broken (explicit kill or server shutdown).


I hope this will help you to understand.

Regarding the script...I plan to run it tomorrow. :)

Regards

---

### Post by src2206 on 2007-09-22
Hello dougfractal

I have run the script though I am not sure whether anything changed or not.

Please let me know what else I need to do.

Regards

---

