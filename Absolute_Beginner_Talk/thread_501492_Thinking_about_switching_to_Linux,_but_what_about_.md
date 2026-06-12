---
title: "Thinking about switching to Linux, but what about my software that I use daily?"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by jimvsmij on 2007-07-15
I am thinking about switching to Linux but the deciding factor will be compatability with off the shelf software.  Will Linux allow me to install my Diet Power software which I absolutely need to regulate my diet as well as AutoCad, SolidWorks, Nero, DVDShrink, Bittorent, Limewire and be able to open and edit all my MS Word, Excel, and Viseo Documents? Those things are all critical to me and If I have to give up any of them then I will be stuck using Windows.  :-(  
Also how is it for loading games?  Can you load World of Warcraft on it?

---

### Post by starsky on 2007-07-15
> **jimvsmij said:**
> I am thinking about switching to Linux but the deciding factor will be compatability with off the shelf software.  Will Linux allow me to install my Diet Power software which I absolutely need to regulate my diet as well as AutoCad, SolidWorks, Nero, DVDShrink, Bittorent, Limewire and be able to open and edit all my MS Word, Excel, and Viseo Documents? Those things are all critical to me and If I have to give up any of them then I will be stuck using Windows.  :-(  
Also how is it for loading games?  Can you load World of Warcraft on it?

hi there :)
alternatives that i am aware of are listed below.
Nero - K3b
Bittorrent - azureus
Limewire - Limewire
Ms Word - open office, abi word
Games - wine, cedega.

---------------- OR ----------------

use virtualisation softwares like vmware, xen, qemu to run Microsoft windows from within Ubuntu. :) Running this way will get you access to windows software from Ubuntu.

There are lots of alternatives in free software world :)

HTH

---

### Post by Ralob on 2007-07-15
WINE allows DVDShrink to run perfectly in Linux. :)

[www.winehq.com](www.winehq.com)

---

### Post by jimvsmij on 2007-07-15
> **starsky said:**
> 

use virtualisation softwares like vmware, xen, qemu to run Microsoft windows from within Ubuntu. :) Running this way will get you access to windows software from Ubuntu.

There are lots of alternatives in free software world :)

HTH

If I use a program that runs MS Windows within Ubuntu so that I can run all my software that I need the computer for,  isn't that the same as just having windows?  Won't I have all the problems of what I have now, CPU & memory usage, Adwares, viruses, etc...?

---

### Post by Majorix on 2007-07-15
^There is also xDVDShrink I believe which is native Linux software.

There was also an alternative to AutoCAD, but I don't remember the name. You can search the repos for AutoCAD and see for yourself.

Your diet software might not have a Linux clone. I hope it can be run under Wine. You will have to try.

And finally you can also run games if you have enough RAM and CPU power, like in Windows.

---

### Post by Arwen on 2007-07-15
I think there are versions of limewire and bittorrent but you can use frostwire and azureus instead.As far as nero and DVDShrink are concerned,I dont think there is linux version for nero(but there is one for DVDShrink) but there many other equivalent programs such serpentine audio cd creator,dvd::rip,Brasero disc burning application,CD/DVD Writer GnomeBaker,Sound juicer CD extractor,avidemux and others.Of course there is no linux version of MSOffice but there is OPEN OFFICE which can open and edit .doc,.xls,etc.I don't know though about DietPower,AutoCad,SolidWorks and games but if there's no other way you can install Qemu or wine,which are OS emulators(just like vmware and virtual pc for XP) where you can install XP and run there all the applications that linux can't run.
I don't know if I helped you,I suggest you should wait for other members to reply(the more the merrier ;-))
Welcome to the world outside the Windows :-D

Guess I'm too late..
In wine I think you can adjust the RAM percentage you want to use for xp..

---

### Post by Majorix on 2007-07-15
> **jimvsmij said:**
> If I use a program that runs MS Windows within Ubuntu so that I can run all my software that I need the computer for,  isn't that the same as just having windows?  Won't I have all the problems of what I have now, CPU & memory usage, Adwares, viruses, etc...?


No not at all. Wine is just an emulator, it is not Windows itself. You won't have malwares.

---

### Post by bme on 2007-07-15
I installed linux to be able connect to local network and the internet more securely. Most of the windows software except bittorent and the like are run without network connection....
The best thing for you to do is install linux(not necessarilly Ubuntu) on a separate partition and Dual boot like me....
This way you can try out linux for a while until you get the hang of it....
Mind you, there are a lot of things NOT working in linux that work off the shelf in windows so it would be better for you to keep windows....

---

### Post by Wiebelhaus on 2007-07-15
> **Ralob said:**
> WINE allows DVDShrink to run perfectly in Linux. :)

[www.winehq.com](www.winehq.com)

There's linux versions of both [nero]("http://www.gnomefiles.org/app.php/NeroLinux") & [dvdshrink]("http://www.gnomefiles.org/app.php/xdvdshrink").

But brasero does kick nero right in the kisser.

---

### Post by AndyCooll on 2007-07-15
I second the view that it will probably be best to dual-boot for awhile and try out Linux. There's an excellent howto in my signature.

Linux however is not a drop-in replacement for Windows it is a completely different OS (again see the link in my signature). If all you want to do is run your Windows apps then you're best staying with Windows. If however you are willing to change then we'll be happy to help.

So having said the above you'll find there are alot of good alternatives in Linux that perform equivalent functions. Open Office is a direct replacement for Microsoft Office. Nero can be replaced either by the built-in burning functions or for more advanced projects by K3B or Gnomebaker. Limewire has an equivalent in Frostwire. There is a Linux version of DVDshrink, and BitTorrent clients are aplenty. World of Warcraft runs fine under Wine, and I'm fairly sure AutoCAD can be made to run under it too.

Welcome to the world of Linux!

:cool:

---

### Post by notwen on 2007-07-15
Win Apps (Linux equivalents)
---
AutoCad (Possibly runs under WINE) [WineHQ + AutoCAD]("http://appdb.winehq.org/appview.php?iAppId=86")
SolidWorks  (Possibly runs under WINE) [WineHQ + SolidWorks]("http://appdb.winehq.org/appview.php?iAppId=318")
Nero ([Nero 4 Linux]("http://www.nero.com/eng/NeroLINUX.html"))
DVDShrink ([k9Copy]("http://k9copy.sourceforge.net/"))
Bittorent ([kTorrent]("http://ktorrent.org/"))
Limewire ([Frostwire]("http://www.frostwire.com/?id=downloads"))
MS Word, Excel, and Visio ([OpenOffice]("http://www.openoffice.org"), not sure about Visio

Generally Linux has multiple options when looking for a windows application alternatives, these are just some that I know are fairly straight forward in use and have a low learning curve.  The WineHQ links give the individual applications page, neither look too promising running under Wine, but perhaps you can run it w/o issue under a Virtual Machine or even dual boot when you need to work in these two applications.  Gaming also is somewhat limited.  I'd suggest dual booting and use Ubuntu as much as you can and fall back to Windows(whether it be under a VM or dual-booted) when you need to.  Good luck and keep browsing the forums, limitless amounts of knowledge can be found here. =]

---

### Post by louieb on 2007-07-15
Windows software runs best in windows.. Unless your open to finding new applications to work with, you are better off staying with windows.
 
Someone has in there signature. Linux is a **better operating s**ystem that windows. It is **not a better windows** that windows.

---

### Post by rye_ on 2007-07-15
hi,

Your software interests sound not dissimilar to my own.
As far as I'm aware (and I've tried) Autocad will not run.

Ryan

---

### Post by Arwen on 2007-07-15
[http://www.linuxalt.com/]("http://www.linuxalt.com/")
[http://linuxappfinder.com/windows]("http://linuxappfinder.com/windows")

+1  for dual boot :-)

---

### Post by jimvsmij on 2007-07-15
Thanks!  You guys taught me more in 5 minutes than what I tried learning by myself over the course of a week! I'm going to try Ubunto Linux with Wine.  My new notebook will be here tomorrow and it has Vista on it.  My Fiance's computer has Vista and she has trouble installing her old software so that is why I am looking for an alternative to Vista.  
The support for Linux seems to be great!  

Thanks again!!!!!!
:)

---

### Post by Ralob on 2007-07-15
> **jimvsmij said:**
> Thanks!  You guys taught me more in 5 minutes than what I tried learning by myself over the course of a week! I'm going to try Ubunto Linux with Wine.  My new notebook will be here tomorrow and it has Vista on it.  My Fiance's computer has Vista and she has trouble installing her old software so that is why I am looking for an alternative to Vista.  
The support for Linux seems to be great!  

Thanks again!!!!!!
:)

No problem dude. I hope you like Ubuntu as much as we do. Don't be afraid to ask questions :)

And welcome to the forums :popcorn:

---

### Post by Nythain on 2007-07-15
keep in mind wine is not going to be an end all solution to most of your software needs... after getting the feel for ubuntu i would highly suggest reading through these forums and other websites and finding native alternatives... most popular windows apps and decent if not better linux alternatives (the only exceptions ive ever heard anyone complain about are Gimp vs. Photoshop, while gimp will do it for the average user, it pales for serious graphic artists... MSOffice vs. OpenOffice, aparently openoffice lacks in certain formatting and just isnt suitable for an environment where you woudl be emailing your docs to msoffice users)

---

### Post by sancho panza on 2007-07-15
Looks like the best for you would be a DUAL-BOOT setup. 
WHY: I havent used Wine much, but in my experience, it can give problems. VMWare is a good option, but not a good choice if you want to run lots of programs in it (and yes, windows in vmware needs antivirus, firewall, etc). Also, the Linux alternatives to MS Office is good only if you dont have to deal with complex MS Office files written in windows. For games, [check this]("https://help.ubuntu.com/community/WorldofWarcraft").

---

