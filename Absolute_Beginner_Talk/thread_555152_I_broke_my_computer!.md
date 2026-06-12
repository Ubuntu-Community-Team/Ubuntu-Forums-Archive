---
title: "I broke my computer!"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Southeast First on 2007-09-19
After playing trying multiple tutorials on getting Compiz-Fusion working on my amd64, ati box, I've discovered that I somehow broke dpkg. When I tried to install xserver this is the terminal output:

$ sudo apt-get -f install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xserver-xgl
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/1865kB of archives.
After unpacking 4968kB of additional disk space will be used.
(Reading database ... 127150 files and directories currently installed.)
Unpacking xserver-xgl (from .../xserver-xgl_7.2.0.git.20070224-0ubuntu3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xgl_7.2.0.git.20070224-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/Xgl', which is also in package xorg-xgl
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xgl_7.2.0.git.20070224-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

edit/ Furthermore, I would kill for gnome-dock or awm right now. If anyone knows how to properly install Compiz-Fusion for ATI on my amd64 box, I would forever be in your debt.

---

### Post by Southeast First on 2007-09-19
Anyone?

---

### Post by Pumalite on 2007-09-19
What do you get with:

sudo apt-get update

---

### Post by Southeast First on 2007-09-19
$ sudo apt-get update
Password:
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release                                 
Get:2 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US      
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release.gpg                                
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Translation-en_US                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 8B in 5s (1B/s)  
Reading package lists... Done

---

### Post by CaptainInsaneO on 2007-09-19
Can you apt-get install anything else? If you have a gui, I thought you already had xserver...

---

### Post by angryfirelord on 2007-09-19
ATI drivers don't work with 3D desktops yet. Sorry, you'll have to wait until ATI releases the 8.42 drivers.

Now, if you're using the open-source driver, that's a different story. First, remove all of your Compiz-Fusion packages so dpkg works again and tell us what driver you're using. If you're not sure, post the output of:
```
cat /etc/X11/xorg.conf | grep Driver
```

---

### Post by Southeast First on 2007-09-19
I did a lot of intalling/uninstalling again and again each time i tried a new tutorial.

@angryfirelord: i'm using fglrx. That doesn't make much since, though. Before I switched from 32 to 64bit I had compiz-fusion working.

---

### Post by Pumalite on 2007-09-19
Try installing:

sudo apt-get install xserver-xorg-video-ati

---

### Post by Southeast First on 2007-09-19
already installed.

---

### Post by angryfirelord on 2007-09-20
Hmm, try following this guide: [http://osnovice.blogspot.com/2007/09/how-to-install-compiz-fusion-updated.html]("http://osnovice.blogspot.com/2007/09/how-to-install-compiz-fusion-updated.html")

---

### Post by Southeast First on 2007-09-20
Update: I CAN install other stuff using apt-get, but I still get that error with xgl.

Going through Synaptic, I got this error:

E: /var/cache/apt/archives/xserver-xgl_7.2.0.git.20070224-0ubuntu3_amd64.deb: trying to overwrite `/usr/bin/Xgl', which is also in package xorg-xgl

I'm fine using fglrx without xgl, I just want a good dock!

---

### Post by Southeast First on 2007-09-20
bumppp please!

---

### Post by Southeast First on 2007-09-21
That was easy enough. I just uninstalled package xorg-xgl and installed xserver-xgl.

---

### Post by Southeast First on 2007-09-21
I have a new problem!

Whenever I try to login, I enter my username and password then I hear the login music, but the screen stays the same! Can anyone help? I've tried reconfiguring X but I can't seem to fix it.

---

### Post by Southeast First on 2007-09-21
Anyone? When I try to login the password box goes gray and the music plays as if it were logging in normally but nothing happens. I can move the mouse but that's it.

---

### Post by angryfirelord on 2007-09-21
> **Southeast First said:**
> I have a new problem!

Whenever I try to login, I enter my username and password then I hear the login music, but the screen stays the same! Can anyone help? I've tried reconfiguring X but I can't seem to fix it.
Try looking here: [http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html](http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html) I think you're missing the xgl login script.

---

### Post by Southeast First on 2007-09-21
You think so? MY default login is Gnome. I can't change the session in the GDM login because whenever I click Select Session it freezes just as what happens when I try to log in. Is there any way I can get into my desktop through command line in recovery mode? Or even fix the problem in recovery move?

---

### Post by bluglue on 2007-09-21
Messing with software in development as we all know breaks or it will at some point usually when it's updated, Compiz fusion looks great but it does'nt do much for the usablity of your system so your not missing much! my advice is to wait for Gutsy which is out on the 18th of next month, this will have it in already all nice and working right!

---

### Post by Southeast First on 2007-09-21
How can I fix my login?

---

### Post by angryfirelord on 2007-09-22
Sounds like you've hit a bug & I'd do what bluglue said: Wait for Gutsy (provided that it's a Compiz-Fusion big and not an XGL big).

While I don't have a solution to fix your XGL issue, your best bet is to just remove it for now until you or anyone else can find a solution. Press Ctrl+Alt+F1, which will take you into text mode and you can then uninstall the xgl packages from there.

If it is an XGL bug, then you'll have to wait until ATI releases their 8.42 drivers (which will take another 1-2 months). Those drivers will (hopefully) include support for AIGLX, which is more stable than XGL.

---

### Post by Southeast First on 2007-09-22
Thanks for the reply, though I should have mentioned when I try to go into text mode it freezes. My only way of getting to the command line is through recovery mode. Will this still work? I suppose I have to try!

---

### Post by anemptygun on 2007-09-22
> **bluglue said:**
> Messing with software in development as we all know breaks or it will at some point usually when it's updated, Compiz fusion looks great but it does'nt do much for the usablity of your system so your not missing much! my advice is to wait for Gutsy which is out on the 18th of next month, this will have it in already all nice and working right!

I agree, I am also waiting for Gutsy.

---

### Post by Southeast First on 2007-09-22
Alright, so in recovery mode I reinstalled gnome but that didn't do anything, so I reinstalled xserver-xorg and it gave me this error:

Setting up xserver-xorg
GTK-Warning ** cannot open display: at /usr/share/perl5/debconf/frontend/gnome.pm line 54.
debconf: unable to initialize frontend: gnome
debconf: (DISPLAY problem?)
debconf: falling back to frontend: dialog.



Anything clue what's going on? I'm going to try to sudo dpkg-reconfigure debconf

edit// alright, I switched from Gnome to dialog then used sudo apt-get install --reinstasll xserver-xorg to reinstall xserver but that didn't fix the problem. If I uninstall xserver (sudo apt-get remove xserver-xorg) will that kill my internet connection and not let me reinstall it (sudo apt-get install xserver-xorg)?

---

### Post by Southeast First on 2007-09-22
bumpp

---

