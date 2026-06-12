---
title: "Advanced Visual Preferences Disappeared!"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by diaz028 on 2007-12-05
I cannot set anything up anymore ... Desktop (right click) -> Change Desktop background -> Visual effects -> Preferences 

Preferences does not open the settings window anymore ! And my panel only shows 2 desktop workspaces even if I have it set to 4! Cube wont work, and flip screen either... 

HELP !

-D

---

### Post by lswest on 2007-12-05
did you by any chance remove the compiz fusion and plugins (if you're in gutsy)?  that would explain why the effects are gone...
command to install the programs again
```
sudo apt-get install compizconfig-settings-manager compiz-plugins
```
if it says it's still installed reinstall it by typing
```
sudo apt-get install --reinstall compizconfig-settings-manager compiz-plugins
```

hopefully it will solve your problems^^

---

### Post by diaz028 on 2007-12-05
I tried, and it still does not work. I have also re-installed my OS and i still get the same thing... Maybe ubuntu didnt delete my preferences? 

-D

---

### Post by Het Irv on 2007-12-05
> **diaz028 said:**
> I tried, and it still does not work. I have also re-installed my OS and i still get the same thing... Maybe ubuntu didnt delete my preferences? 

-D
What do you mean by re-install.  I take that to mean that you reformatted, if so there is no way your setting could be saved.  Just make sure that you run the first command posted by lswest.  also to rotate the cube you have to have cube rotation turned on (it is a seperate plugin for some reason).

---

### Post by skjoldfetter on 2007-12-05
when you reinstalled your OS compiz wont be there.. and neither will the effects

find it in the add/remove programs (search "compiz")  and then find the settings in main menu > system > preferences > appearance  (then select the visual effects tab and there should be a "custom" option in the bottom with a button to choose which effects you want.)

it could also be because your graphics card cant handle it, but its very unlikely (unless the card is pre 1990)

---

### Post by diaz028 on 2007-12-05
> **skjoldfetter said:**
> when you reinstalled your OS compiz wont be there.. and neither will the effects

find it in the add/remove programs (search "compiz")  and then find the settings in main menu > system > preferences > appearance  (then select the visual effects tab and there should be a "custom" option in the bottom with a button to choose which effects you want.)

it could also be because your graphics card cant handle it, but its very unlikely (unless the card is pre 1990)

Well, everything use to work perfectly ... for a whole week, until i screwed with Emerald and Compiz settings yesterday, dont know what did it, and then re-installed from live cd... Symptoms are still there for some weird reason... 

When I get to Custom Effects -> Preferences, I click on preferences and nothing happens. I go to System ->  Preferences   and there is no menu for 'advanced desktop preferences' or 'desktop pref' or anything like that... I tried clicking -> Compiz Config Settings Manager, and nothing happens at all. 

Help?

EDIT: Maybe it is a recent update that came through? Makes sense, since the problem happened DIRECTLY after an update... 

-D

---

### Post by diaz028 on 2007-12-06
I is an update... The new update screws everything up! Damn.... 

How do I undo an update?

---

### Post by xfearxnxloathing on 2008-01-14
> **diaz028 said:**
> I is an update... The new update screws everything up! Damn.... 

How do I undo an update?

wtf?!  i updated some compiz and emerald stuff that said it needed updated and that's when my settings disappeared...  before the update everything worked including the cube!  

...linux hurts my feelings sometimes, 'tis very tricky stuff.

***UPDATE***

i did this command in the terminal 
> sudo apt-get install compizconfig-settings-manager compiz-plugins
and got this message
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
compiz-plugins is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
i noticed it says "2 not installed" so i wnet to the update manager and sure enough there's "emerald" and "libemeraldengine0" listed and uncheckable.  i then proceed to hit the check button to make sure and the following error message appears.
> W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9

emerald theme manager still works just the desktop effects are gone and when i look in preferences custom is still selected, any ideas?

---

### Post by RomeReactor on 2008-01-14
Hi. Try fetching the GPG key:
```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```
Then:
```
sudo apt-get update
```

---

### Post by xfearxnxloathing on 2008-01-14
> **RomeReactor said:**
> Hi. Try fetching the GPG key:
```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```
Then:
```
sudo apt-get update
```

i got
 > wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
--21:08:26--  [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,180 (4.1K) [application/octet-stream]

100%[====================================>] 4,180         --.--K/s             

21:08:27 (35.83 KB/s) - `-' saved [4180/4180]

OK

and for the next command
> sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release.gpg [189B]                  
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US        
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release [14.2kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Get:6 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Packages [14.8kB]
Get:7 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy Sources [37B]
Fetched 29.2kB in 1s (14.9kB/s)
Reading package lists... Done


now what, check and see if everything works?

---

### Post by RomeReactor on 2008-01-14
> **xfearxnxloathing said:**
> now what, check and see if everything works?

Yes.

---

### Post by kathryn on 2008-01-14
My visual preferences (using gutsy) similarly disappeared recently, probably as a result of the update.  The settings kept reverting back to "normal" or "none".

I fixed the problem entirely by reinstalling the following synaptic packages:

compizconfig-settings-manager
emerald
gnome-compiz-manager

Best of luck!

---

### Post by xfearxnxloathing on 2008-01-15
> **RomeReactor said:**
> Yes.

didn't do anything.  thnx for trying to help me and all, i'll keep looking around on here.

> My visual preferences (using gutsy) similarly disappeared recently, probably as a result of the update. The settings kept reverting back to "normal" or "none".

I fixed the problem entirely by reinstalling the following synaptic packages:

compizconfig-settings-manager
emerald
gnome-compiz-manager

Best of luck!

well when i look at appearance it's still locked in at custom.

how do i get rid of them before reinstalling?  does it just reinstall over top?

---

### Post by RomeReactor on 2008-01-15
Are you still unable to install the emerald and libemeraldengine0 updates?

---

### Post by xfearxnxloathing on 2008-01-15
> **RomeReactor said:**
> Are you still unable to install the emerald and libemeraldengine0 updates?

affirmative.  the check box beside each one to the left i cannot click to add checkmark.  weird huh...

[IMG]http://i23.photobucket.com/albums/b366/ecko7two90/Screenshot.png[/IMG]

---

### Post by RomeReactor on 2008-01-15
Looking again at the output of apt-get update, you have Feisty repositories even though you are now running Gutsy:
```
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Get:6 http://download.tuxfamily.org feisty/eyecandy Packages [14.8kB]
Get:7 http://download.tuxfamily.org feisty/eyecandy Sources [37B]
Fetched 29.2kB in 1s (14.9kB/s)
Reading package lists... Done
```

If you get Emerald from the TuxFamily repositories, it would be a good idea to uninstall everything from that repository and look for a Gutsy version. I seem to recall that there are certain libraries that version of Emerald requires that are no longer available for Gutsy.

---

### Post by xfearxnxloathing on 2008-01-16
> **RomeReactor said:**
> Looking again at the output of apt-get update, you have Feisty repositories even though you are now running Gutsy:
```
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Get:6 http://download.tuxfamily.org feisty/eyecandy Packages [14.8kB]
Get:7 http://download.tuxfamily.org feisty/eyecandy Sources [37B]
Fetched 29.2kB in 1s (14.9kB/s)
Reading package lists... Done
```

If you get Emerald from the TuxFamily repositories, it would be a good idea to uninstall everything from that repository and look for a Gutsy version. I seem to recall that there are certain libraries that version of Emerald requires that are no longer available for Gutsy.

funny thing, emerald never stopped working, only compiz fusion manager and the actuall desktop effects...  
for the fiesty and third party sources, i totally noticed that that wasn't right and that the actuall compiz fusion is now listed in the package manager i just uninstalled it and took the two fiesty sources off the source list and unchecked the two gutsy sources that were previously checked under the third party menu.  i reinstalled using the package manager, rebooted, logged in and there she was, sitting right in the system menu.  i had to go back and do all the tweaking but it was most def worth it.  thnx all of you who helped.  now how do i get this post selected as [SOLVED]????

:popcorn:

---

### Post by RomeReactor on 2008-01-16
To mark the thread as 'Solved', go to the top of the first post on the page, click on "Thread Tools" and select it there.

---

### Post by xfearxnxloathing on 2008-01-16
> **RomeReactor said:**
> To mark the thread as 'Solved', go to the top of the first post on the page, click on "Thread Tools" and select it there.

erm, seems i didn't even start this thread haha.

---

