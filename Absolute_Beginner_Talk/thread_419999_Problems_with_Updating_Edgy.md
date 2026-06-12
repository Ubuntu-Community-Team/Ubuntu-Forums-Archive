---
title: "Problems with Updating Edgy"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Mairi on 2007-04-23
I think my update-manager is broken. I've not had updates for several days, though no error messages. So, I opened it with terminal and got this. And my bad, I know I should use gksudo. I got this. My internet is definitely up.

mairi@mairi-desktop:~$ sudo update-manager
Password:
warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Next I tried aptitude

mairi@mairi-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                    
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US       
Get:3 [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release.gpg [191B]           
Ign [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Translation-en_US         
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                              
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                            
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial Release                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release                             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial/main Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Translation-en_US   
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/multiverse Sources
Fetched 7B in 1s (4B/s)  
Reading package lists... Done
mairi@mairi-desktop:~$ sudo aptitude update install
E: The update command takes no arguments
mairi@mairi-desktop:~$ sudo aptitude install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  alien debhelper devscripts feh giblib1 
The following packages will be REMOVED:
  build-essential comerr-dev dpkg-dev enscript eterm fbdesk fbpager 
  fluxconf g++ g++-4.1 gettext-kde gnome-mud gsetroot hspell kate kcontrol 
  kdebase-bin kdebase-data kdebase-dev kdebase-kio-plugins kdelibs-data 
  kdelibs4-dev kdelibs4c2a kdeprint kdesdk-scripts kdesktop kdocker kfind 
  khelpcenter kicker klipper kmenuedit konqueror konqueror-nsplugins 
  konsole ksmserver ksplash ksysguard ksysguardd kwin libacl1-dev 
  libart-2.0-dev libarts1-dev libarts1c2a libartsc0-dev libasound2-dev 
  libaspell-dev libast2 libattr1-dev libaudio-dev libaudiofile-dev 
  libavahi-client-dev libavahi-common-dev libavahi-compat-libdnssd1 
  libavahi-qt3-1 libavahi-qt3-dev libbz2-dev libc6-dev libcupsys2-dev 
  libdbus-1-dev libdbus-qt-1-1c2 libesd0-dev libexpat1-dev 
  libfontconfig1-dev libfreetype6-dev libgcrypt11-dev libgl1-mesa-dev 
  libglib2.0-dev libglu1-mesa-dev libgnutls-dev libgpg-error-dev libice-dev 
  libidn11-dev libimlib2 libjasper-1.701-dev libjpeg62-dev libkadm55 
  libkonq4 libkrb5-dev liblcms1-dev liblua50 liblua50-dev liblualib50 
  liblualib50-dev liblzo-dev libmng-dev libnss-mdns libogg-dev 
  libopencdk8-dev libopenexr-dev libopenexr2c2a libpcre3 libpcre3-dev 
  libpcrecpp0 libpng12-dev libpopt-dev libqt3-headers libqt3-mt 
  libqt3-mt-dev libsasl2-dev libsm-dev libssl-dev libstdc++6-4.1-dev 
  libtasn1-3-dev libtiff4-dev libtiffxx0c2 libvorbis-dev libx11-dev 
  libxau-dev libxcomposite1 libxcursor-dev libxdmcp-dev libxext-dev 
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxml2-dev libxmu-dev 
  libxmu-headers libxmuu-dev libxpm-dev libxrandr-dev libxrender-dev 
  libxslt1-dev libxt-dev libxtrap-dev libxtst-dev libxv-dev linux-libc-dev 
  lua50 mesa-common-dev papaya poster psutils qt3-dev-tools tf x-dev 
  x11proto-core-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev 
  x11proto-randr-dev x11proto-record-dev x11proto-render-dev 
  x11proto-trap-dev x11proto-video-dev x11proto-xext-dev 
  x11proto-xinerama-dev xlibs-dev xtrans-dev zlib1g-dev 
0 packages upgraded, 0 newly installed, 152 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 267MB will be freed.
The following packages have unmet dependencies:
  debhelper: Depends: dpkg-dev (>= 1.13.13) but it is not installable
  feh: Depends: libimlib2 but it is not installable
  giblib1: Depends: libimlib2 but it is not installable
  devscripts: Depends: dpkg-dev but it is not installable
  alien: Depends: dpkg-dev but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
dpkg-dev [1.13.22ubuntu7 (edgy, now)]
libc6-dev [2.4-1ubuntu12.3 (edgy-updates, now)]
libimlib2 [1.2.1-2ubuntu1.2 (edgy-security, edgy-security, now)]
libnss-mdns [0.7-1ubuntu1 (edgy, now)]
linux-libc-dev [2.6.17.1-11.37 (edgy-security, edgy-security, now)]

Score is -195

Accept this solution? [Y/n/q/?] 


I'm puzzled by this, I just don't know enough. Feh, certainly seems to be working.  Synaptic makes no mention of broken packages, hence I can't repair them there. I am not sure about allowing aptitude to remove all those packages without knowing what's going on. I don't even know if the two issues are related. L

Last night, I ran synaptic, and when I hit reload, it threw out all kind of errors about unable to connect to repositories. Nothing like that today, I presume that's something else entirely. Well, I'm sorry this is so long, and as ever I'll be grateful for any help. :)

---

### Post by Mairi on 2007-04-24
Mehness! I figured out what was wrong, as per the second part of my question. aptitude upgrade, not install. However I still don't know what is wrong with upgrade manager, I haven't been able to update for days. Can't go on like that, if I can't figure out what's wrong, I'll have to do a clean install. Still gives me that error about the network when I tell it to check. I am probably just doing something dumb. Ah, well, a clean install is not the hardest thing to do or the worse thing that could happen.

---

### Post by zvacet on 2007-04-25
If you get updates after** sudo aptitude upgrade** everything should be fine.Is it Automatix repo one wich give you trouble?Did you try go to the software properties and choose local server.If you use local try with main.

---

### Post by Mairi on 2007-04-25
Hello and thank you very much for your response. I know I'm vague on this, I'm just not sure what's going on. Alright, I'll show as best I can.

I open update-manager via gksudo and put in my password.

mairi@mairi-desktop:~$ gksudo update-manager
warning: could not initiate dbus

It's my understanding from looking around the forums and googling that this warning is not important. I really do research this stuff before I post, honest! The update manager opens. It says system up to date, so I tell it to check. The terminal pops up this.

could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

And then reports the system as up to date. 

Onto apt-get. I won't regale you with the list of repositories, they all show as hit and I unchecked the automatix one, before hand, just in case. I get this. 

Fetched 5B in 1s (3B/s)  
Reading package lists... Done
mairi@mairi-desktop:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
mairi@mairi-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mairi@mairi-desktop:~$ 
mairi@mairi-desktop:~$ 

Which it has been saying for days. Do I even have anything to worry about, am I making a fuss for nothing? Is it possibly because I turned off automatic notification of updates, to save memory? I'm not used to having NO updates for so long, Edgy is so good about keeping up on that. 

I even tried with Synaptic, though I am a bit hazy on how, and wether it can even be done. I opened it with gksudo, hit reload, and hit mark all upgrades. Nothing is ever marked, but no error messages in the terminal. Allow me to use my favorite word of distress. MEH!

Why aptitude wants to remove 130 packages and insists five are broken when Synaptic says none are broken, is probably a topic to bother everyone with another time. Again, my thanks for your response.

---

### Post by Anicka on 2007-04-25
> **Mairi said:**
> Why aptitude wants to remove 130 packages and insists five are broken when Synaptic says none are broken, is probably a topic to bother everyone with another time. Again, my thanks for your response.

After I had upgraded and did sudo aptitude install, I got the same thing. I reinstalled all the packages on the list and after that, aptitude was happy. (Not very fun when there are +150, but it solves the problem.)

---

### Post by Mairi on 2007-04-25
Thank you, Anicka. I'll try that. We know it's best to keep aptitude happy. :) I'm betting it'll work, and if something does go wrong..well, like they say, I get to keep both pieces and it's easy enough, at least for me, to glue them back together.

---

### Post by Mairi on 2007-04-28
I'm marking this resolved, as it seems like it turned out to be a non-issue. Thanks for help and answers all.

---

