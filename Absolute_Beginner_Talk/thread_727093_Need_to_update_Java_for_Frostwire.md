---
title: "Need to update Java for Frostwire"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by TNCharger on 2008-03-17
I've been trying for a week and a half to upgrade my Java (version 1.4.2) to at least 1.5 so I can run Frostwire but everything I have tried has failed. I've gone through all the other posts on this forum and nothing has worked. Where everyone else has 4 or 5 options under Alternatives, I have 2. Seems that I'm running Cacao? Can somebody please help a noobie?

---

### Post by taurus on 2008-03-17
What happens when you run these commands from a terminal?

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
sudo update-alternatives --config java
```

---

### Post by TNCharger on 2008-03-17
Here's what I got:

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy Release.gpg                            
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/universe Translation-en_US             
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/main Translation-en_US                 
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/multiverse Translation-en_US           
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates Release.gpg                    
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/universe Translation-en_US     
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/main Translation-en_US         
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/restricted Translation-en_US   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/multiverse Translation-en_US   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed Release.gpg                   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/universe Translation-en_US    
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/main Translation-en_US        
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/restricted Translation-en_US  
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/multiverse Translation-en_US
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports Release.gpg        
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/universe Translation-en_US
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/main Translation-en_US
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/restricted Translation-en_US
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/multiverse Translation-en_US
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US     
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]             
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates Release
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed Release             
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports Release            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/universe Packages            
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/main Packages                
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/multiverse Packages          
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/universe Sources             
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/main Sources                 
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                          
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/universe Packages   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/main Packages
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/restricted Packages  
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/multiverse Packages  
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/universe Sources     
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/main Sources         
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/restricted Sources   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/multiverse Sources   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/universe Packages   
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/main Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources               
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/restricted Packages
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/multiverse Packages
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                     
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/main Sources        
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/restricted Sources
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/multiverse Sources
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/universe Packages
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/main Packages
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/restricted Packages
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/multiverse Packages
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/universe Sources
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/main Sources
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
Ign [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/multiverse Sources
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/universe Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/main Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/multiverse Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/universe Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/main Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy/multiverse Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/universe Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/main Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/restricted Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/multiverse Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/universe Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/main Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/restricted Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-updates/multiverse Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/universe Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/main Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/restricted Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/multiverse Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/universe Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/main Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/restricted Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-proposed/multiverse Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/universe Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/main Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/restricted Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/multiverse Packages
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/universe Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/main Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/restricted Sources
  404 Not Found
Err [http://ubuntu.mirrors.tds.net](http://ubuntu.mirrors.tds.net) gutsy-backports/multiverse Sources
  404 Not Found
Fetched 2B in 2s (1B/s)  
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-updates/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/multiverse/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-proposed/multiverse/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/universe/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/main/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz](http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy-backports/multiverse/source/Sources.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by konungursvia on 2008-04-11
me too, I followed the solution telling us to select the 32 bit java, but still, the settings directories are not writable:

```

FrostWire version @version@
Java version 1.6.0_05 from Sun Microsystems Inc.
Linux v. 2.6.24-16-generic on i386
Free/total memory: 28916896/31195136

java.lang.RuntimeException: java.io.IOException: settings dir not writable
	at com.limegroup.gnutella.util.CommonUtils.getUserSettingsDir(CommonUtils.java:815)
	at com.limegroup.gnutella.gui.Initializer.initialize(Initializer.java:102)
	at com.limegroup.gnutella.gui.GUILoader.load(GUILoader.java:52)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.limegroup.gnutella.gui.Main.main(Main.java:44)
Caused by: java.io.IOException: settings dir not writable
	at com.limegroup.gnutella.util.CommonUtils.setUserSettingsDir(CommonUtils.java:747)
	at com.limegroup.gnutella.util.CommonUtils.getUserSettingsDir(CommonUtils.java:813)
	... 7 more

STARTUP ERROR!

-- listing properties --
AVERAGE_CONNECTION_TIME=2474967
APP_HEIGHT=879
DIRECTORIES_TO_SEARCH_FOR_FILES=/media/SVault/Transfer
FRACTIONAL_UPTIME=8.894147E-4
LAST_EXPIRE_TIME=1200193157659
SESSIONS=16
DIRECTORY_FOR_SAVING_FILES=/media/SVault/Transfer
LAST_FILECHOOSER_DIR=/media/SVault/Transfer
RUN_ONCE=true
TOTAL_CONNECTION_TIME=37124505
COUNTRY=US
UI_LIBRARY_PLAY_LIST_TAB_DIVIDER_LOCATION=442
CLIENT_ID=C4A4B1CEFF66C1F8E1D4169785FA1400
CHAT_IRC_NICK=konungursvia
LAST_SHUTDOWN_TIME=1201231199406
FREELOADER_FILES=33
MAX_UPLOAD_BYTES_PER_SEC=18
TOTAL_UPTIME=36863
PORT=30273
AVERAGE_UPTIME=2457
TOTAL_CONNECTIONS=15
APP_WIDTH=1440
MAX_SIM_DOWNLOAD=8
INSTALLED=true
UI_LIBRARY_TREE_DIVIDER_LOCATION=130
MAX_DOWNLOAD_BYTES_PER_SEC=123
CONNECTION_SPEED=350
WINDOW_Y=2
WINDOW_X=0



FILES IN CURRENT DIRECTORY:
/usr/lib/frostwire/FrostWire.icns
LAST MODIFIED: 1204210309000
SIZE: 65282

/usr/lib/frostwire/looks.jar
LAST MODIFIED: 1204210308000
SIZE: 630634

/usr/lib/frostwire/vorbis.jar
LAST MODIFIED: 1204210308000
SIZE: 27215

/usr/lib/frostwire/icu4j.jar
LAST MODIFIED: 1204210307000
SIZE: 741440

/usr/lib/frostwire/hs_err_pid8205.log
LAST MODIFIED: 1207947637000
SIZE: 27056

/usr/lib/frostwire/hs_err_pid8082.log
LAST MODIFIED: 1206668498000
SIZE: 27056

/usr/lib/frostwire/hs_err_pid7686.log
LAST MODIFIED: 1207947277000
SIZE: 27160

/usr/lib/frostwire/hs_err_pid12529.log
LAST MODIFIED: 1207950460000
SIZE: 27018

/usr/lib/frostwire/log4j.jar
LAST MODIFIED: 1204210308000
SIZE: 677952

/usr/lib/frostwire/libtray.so
LAST MODIFIED: 1204210308000
SIZE: 18501

/usr/lib/frostwire/commons-logging.jar
LAST MODIFIED: 1204210307000
SIZE: 59154

/usr/lib/frostwire/id3v2.jar
LAST MODIFIED: 1204210308000
SIZE: 45837

/usr/lib/frostwire/hs_err_pid1721.log
LAST MODIFIED: 1206329647000
SIZE: 26701

/usr/lib/frostwire/hs_err_pid8056.log
LAST MODIFIED: 1207947631000
SIZE: 27054

/usr/lib/frostwire/libjdic.so
LAST MODIFIED: 1204210308000
SIZE: 21447

/usr/lib/frostwire/themes.jar
LAST MODIFIED: 1204210308000
SIZE: 223746

/usr/lib/frostwire/tritonus.jar
LAST MODIFIED: 1204210308000
SIZE: 152711

/usr/lib/frostwire/jdic_stub.jar
LAST MODIFIED: 1204210308000
SIZE: 47444

/usr/lib/frostwire/mp3sp14.jar
LAST MODIFIED: 1204210308000
SIZE: 40064

/usr/lib/frostwire/hs_err_pid8173.log
LAST MODIFIED: 1206668532000
SIZE: 27056

/usr/lib/frostwire/libmozembed-linux-gtk2.so
LAST MODIFIED: 1204210308000
SIZE: 249499

/usr/lib/frostwire/xml.war
LAST MODIFIED: 1204210308000
SIZE: 7343

/usr/lib/frostwire/seenMessages.dat
LAST MODIFIED: 1207967452000
SIZE: 679

/usr/lib/frostwire/log4j.properties
LAST MODIFIED: 1204210308000
SIZE: 7171

/usr/lib/frostwire/jdic.jar
LAST MODIFIED: 1204210308000
SIZE: 45364

/usr/lib/frostwire/pmf.ico
LAST MODIFIED: 1204210309000
SIZE: 3262

/usr/lib/frostwire/hs_err_pid12607.log
LAST MODIFIED: 1207950470000
SIZE: 26969

/usr/lib/frostwire/runFrostwire.sh
LAST MODIFIED: 1204210308000
SIZE: 3440

/usr/lib/frostwire/jcraft.jar
LAST MODIFIED: 1204210308000
SIZE: 137190

/usr/lib/frostwire/jl011.jar
LAST MODIFIED: 1204210308000
SIZE: 255016

/usr/lib/frostwire/hs_err_pid1255.log
LAST MODIFIED: 1206329623000
SIZE: 26860

/usr/lib/frostwire/ProgressTabs.jar
LAST MODIFIED: 1204210308000
SIZE: 3699

/usr/lib/frostwire/root
LAST MODIFIED: 1207967270000
SIZE: 4096

/usr/lib/frostwire/commons-net.jar
LAST MODIFIED: 1204210307000
SIZE: 180799

/usr/lib/frostwire/hs_err_pid28417.log
LAST MODIFIED: 1206377224000
SIZE: 26915

/usr/lib/frostwire/commons-httpclient.jar
LAST MODIFIED: 1204210307000
SIZE: 212343

/usr/lib/frostwire/libmozembed-linux-gtk1.2.so
LAST MODIFIED: 1204210308000
SIZE: 468140

/usr/lib/frostwire/hs_err_pid8132.log
LAST MODIFIED: 1207947635000
SIZE: 27054

/usr/lib/frostwire/update.ver
LAST MODIFIED: 1204210309000
SIZE: 2618

/usr/lib/frostwire/irc.jar
LAST MODIFIED: 1204210308000
SIZE: 451559

/usr/lib/frostwire/hs_err_pid22222.log
LAST MODIFIED: 1207949438000
SIZE: 27070

/usr/lib/frostwire/xml-apis.jar
LAST MODIFIED: 1204210308000
SIZE: 124724

/usr/lib/frostwire/hashes
LAST MODIFIED: 1204210309000
SIZE: 1238

/usr/lib/frostwire/FrostWire.jar
LAST MODIFIED: 1204210307000
SIZE: 4449683

/usr/lib/frostwire/commons-pool.jar
LAST MODIFIED: 1204210307000
SIZE: 66648

/usr/lib/frostwire/i18n.jar
LAST MODIFIED: 1204210307000
SIZE: 25678

/usr/lib/frostwire/clink.jar
LAST MODIFIED: 1204210306000
SIZE: 313184

/usr/lib/frostwire/docs
LAST MODIFIED: 1207967270000
SIZE: 4096

/usr/lib/frostwire/daap.jar
LAST MODIFIED: 1204210307000
SIZE: 376921

/usr/lib/frostwire/hs_err_pid8705.log
LAST MODIFIED: 1207948091000
SIZE: 27001

/usr/lib/frostwire/jmdns.jar
LAST MODIFIED: 1204210308000
SIZE: 69306

/usr/lib/frostwire/MessagesBundle.properties
LAST MODIFIED: 1204210308000
SIZE: 156440

/usr/lib/frostwire/MessagesBundles.jar
LAST MODIFIED: 1204210308000
SIZE: 530089

/usr/lib/frostwire/jython.jar
LAST MODIFIED: 1204210308000
SIZE: 719950

/usr/lib/frostwire/jarbundler-1.9.jar
LAST MODIFIED: 1204210308000
SIZE: 17640



```

---

### Post by zvacet on 2008-04-12
@ **TNCharger**

```
gksudo gedit /etc/apt/sources.list
```

Remove # sign from all lines start with **deb**.Save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get install ubuntu-restricted-extras
```

If still no luck in system>admin>software sources change server to **main**.

---

