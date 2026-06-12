---
title: "Graphic Issues,ATI"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by bluebrew on 2007-12-31
So I'm having some issues gaming 
will post my original post that I made in another thread of mine,I marked as solved as it was about installation and it got ubuntu installed nicely 


ok seem to have another issue
system is freezing when playing games,yesterday when playing "bzflag",and just now playing "alien arena",note these are games installed and not online/through browser as all flash games seems just fine
didn't really think nothing of it yesterday as it was once and nothing runs perfect but now twice during game play within the first couple mins so I'm seeing a trend here
any known issues with this? hopefully theres something we can do


Quote:
Originally Posted by Don1500 View Post
Which ATI card do you have? If you go to System=preferences=appearance=visual effects can you select the custom preferences?

If you can not, reinstall your ATI driver from ENVY, Follow this link, you will be surprized how much more Ubuntu can do with the correct drivers.

Check here:
[http://ubuntuforums.org/showpost.php...10&postcount=6](http://ubuntuforums.org/showpost.php...10&postcount=6)

OK done that and it said graphic card could not be enabled when I selected the bottom option for extra
will check that link in a few




I'm hoping the above link that Don1500 will work thou

---

### Post by spiderbatdad on 2007-12-31
If you are trying to play those game while running gl, i would say that is your problem.

---

### Post by bluebrew on 2007-12-31
> **spiderbatdad said:**
> If you are trying to play those game while running gl, i would say that is your problem.

What is "gl" that your referring to?

---

### Post by overdrank on 2007-12-31
HI and to quote your specs
My system is:
3.2 ghz Intel Prescott
MSI 865 PE Mobo 800mhz
120 gig HDD Seagate
*9250 ATI Radeon (can't remember if its 9200 or 9250 but pretty sure 9250)
1.5 gig ram pc3200 400mhz DDR Ultra
As I understand it that card is on the cusp of being supporte by the restricted drivers and ATI also. So you may try Envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
If you are not able to use the restricted drivers. Good luck!

---

### Post by bluebrew on 2008-01-01
Like the old saying things will get worse before they get better


-When I run Envy - Install ATI driver I get a error in the terminal error that comes up,couldnt copy what it said but took a screen shot...see attachment if it works
-Ran the ATI Driver manually v8.4 - Do you want your xorg.conf to be automatically configured? (Recommended) - I selected Yes - prompted me to restart,came back on into low graphics mode,had to select to continue in that and my mouse was a white X till Ubuntu started completely

-Followed this link 
wiki.cchtml.com
and I get this in my terminal

joey@joey-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_CA
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [187B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
joey@joey-desktop:~$  sudo apt-get install linux-restricted-modules-generic restricted-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
restricted-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joey@joey-desktop:~$  sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joey@joey-desktop:~$ sudo depmod -a
joey@joey-desktop:~$ $ 




-I cannot open Restricted Drivers Manager at all,says "Your hardware does not need any restricted drivers"

-I have a directory now "ATI Catalyst Control Center" when I open it I get 
  Initializing error
There was a problem Initializing Catalyst Control Center Linux Edition.
No Ati graphic driver is installed,or the Ati driver is not functioning properly.Please install the Ati driver appropriate for your Ati Hardware or configure



I Definitely need more assistance 
man I feel dumb now



and btw Happy New Year all

---

### Post by bluebrew on 2008-01-01
BUMP BUMP BUMP

Seemed to be working from the original install,Initially I was able to enable the highest desktop graphics
Then when I tinkered around to see if there was a better driver as I was using a ATI and also not knowing if I was using the best one or not,seemed to make it worse

I cannot access my Restricted driver manager at all

When I go to add/remove programs,I see theres a ATI driver listed,when I highlight it to what I thought was to install it/select it...it just says that it cannot be removed as the system is Dependant on it or sumthing

---

