---
title: "Ubuntu  Guest Restrictions"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by ru0n on 2007-09-20
Hello!
I'd like to restrict a "guest" account. Is there any way to "lock" the taskbar? So nothing can be added there? Also is it possible to "lock" the desktop? Or disable rightclicking? 

If its possible, how can i achieve it?

Thanks in advance...
ru0n

---

### Post by julian67 on 2007-09-22
Pessulus is a lockdown tool for Gnome, available from the main repository.

---

### Post by mysticmatrix on 2007-09-22
> **ru0n said:**
> Hello!
I'd like to restrict a "guest" account. Is there any way to "lock" the taskbar? So nothing can be added there? Also is it possible to "lock" the desktop? Or disable rightclicking? 

If its possible, how can i achieve it?

Thanks in advance...
ru0n

You might have a look at newest edition of Fullcircle Magzine. It has a section on parental control.
[http://fullcirclemagazine.org/issue-4/](http://fullcirclemagazine.org/issue-4/)

---

### Post by nowshining on 2007-09-22
> **julian67 said:**
> Pessulus is a lockdown tool for Gnome, available from the main repository.

ahhh :) great application - googled and found this thread trying to lockdown the taskbar from meself - :P u know so that way it  can't be moved up or down or side to side -it's currently at the bottom.

---

### Post by ru0n on 2007-10-02
I've got another Problem...

i'm not able to install Sabayon or Pessulus because it can't find the package in the terminal (i've also searched in the synaptic paket manager). Although Universe and Multiverse seem to have a check on them. Weird is that when i press Close in SoftwareSource a window comes up where it wants to download Paket Information or something, but after about 50%  there's a error message.

I'm lost. :confused:

---

### Post by overdrank on 2007-10-02
> **ru0n said:**
> I've got another Problem...

i'm not able to install Sabayon or Pessulus because it can't find the package in the terminal (i've also searched in the synaptic paket manager). Although Universe and Multiverse seem to have a check on them. Weird is that when i press Close in SoftwareSource a window comes up where it wants to download Paket Information or something, but after about 50%  there's a error message.

I'm lost. :confused:

Hi and what is the error that you get? Have you tried to fix broken packages in synaptic manager?
Pessulus is also available in add and remove

---

### Post by ru0n on 2007-10-02
> **overdrank said:**
> Hi and what is the error that you get? Have you tried to fix broken packages in synaptic manager?
Pessulus is also available in add and remove

Yes i've also tried to install it with add and remove. Yet another error message. 

I haven't tried to fix broken packages in synaptic manager.. How can i do that?
I'm reinstalling ubuntu right now since after about one hour of trying without progress i thought it might be a wise decision. I hope it works fine after this.. otherwise i'll try to fix broken packages in the synaptic package manager when i know how :p

---

### Post by Circus-Killer on 2007-10-02
> **ru0n said:**
> I've got another Problem...

i'm not able to install Sabayon or Pessulus because it can't find the package in the terminal (i've also searched in the synaptic paket manager). Although Universe and Multiverse seem to have a check on them. Weird is that when i press Close in SoftwareSource a window comes up where it wants to download Paket Information or something, but after about 50%  there's a error message.

I'm lost. :confused:

sabayon is a distribution, like ubuntu. as far as i know, the only way to get sabayon is to download the install cd .iso and burn it to disk, and do an install. much like you did when installing ubuntu.

because sabayon is based off ubuntu, there very well may be a meta-package that will install everything that sabayon has, but i highly doubt it (correct me if i'm wrong). so as said, to get sabayon, google "sabayon", goto their homepage and then follow the download links to get the install cd .iso file.
burn it, run it, install it. just like ubuntu.

---

### Post by overdrank on 2007-10-02
> **ru0n said:**
> Yes i've also tried to install it with add and remove. Yet another error message. 

I haven't tried to fix broken packages in synaptic manager.. How can i do that?
I'm reinstalling ubuntu right now since after about one hour of trying without progress i thought it might be a wise decision. I hope it works fine after this.. otherwise i'll try to fix broken packages in the synaptic package manager when i know how :p

Hi, yes reinstalling it a little over kill but since you are on your way. If you ever have to fix broken packages in synaptic manager it is under edit, also you can refine the search for broken packages under settings filters. Good luck! Please post back if you still have a problem and if not please mark thread as solved. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by ru0n on 2007-10-02
> **overdrank said:**
> Hi, yes reinstalling it a little over kill but since you are on your way. If you ever have to fix broken packages in synaptic manager it is under edit, also you can refine the search for broken packages under settings filters. Good luck! Please post back if you still have a problem and if not please mark thread as solved. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

I reinstalled it, tried to fix broken packages. But still get this message in the synaptic package manager or in the add&remove programm. "Could not download all repository indexes". 
Help.
:confused:

---

### Post by overdrank on 2007-10-02
> **ru0n said:**
> I reinstalled it, tried to fix broken packages. But still get this message in the synaptic package manager or in the add&remove programm. "Could not download all repository indexes". 
Help.
:confused:

Hi could you post the out put of the commands in the terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ru0n on 2007-10-02
> **overdrank said:**
> Hi could you post the out put of the commands in the terminal
```
sudo apt-get update
sudo apt-get upgrade
```

After update..
```

sudo apt-get update
Ign http://security.ubuntu.com feisty-security Release.gpg
Ign http://ch.archive.ubuntu.com feisty Release.gpg
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://ch.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://ch.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://ch.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://ch.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://ch.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security Release
Ign http://ch.archive.ubuntu.com feisty-updates Release.gpg
Ign http://security.ubuntu.com feisty-security/main Packages
Ign http://ch.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Packages
Ign http://ch.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/main Sources
Ign http://ch.archive.ubuntu.com feisty Release
Ign http://security.ubuntu.com feisty-security/restricted Sources
Ign http://ch.archive.ubuntu.com feisty-updates Release
Ign http://security.ubuntu.com feisty-security/universe Packages
Ign http://ch.archive.ubuntu.com feisty/main Packages
Ign http://security.ubuntu.com feisty-security/universe Sources
Ign http://ch.archive.ubuntu.com feisty/restricted Packages                 
Ign http://security.ubuntu.com feisty-security/multiverse Packages             
Ign http://ch.archive.ubuntu.com feisty/main Sources                           
Ign http://security.ubuntu.com feisty-security/multiverse Sources
Ign http://ch.archive.ubuntu.com feisty/restricted Sources
Ign http://security.ubuntu.com feisty-security/main Packages                   
Ign http://ch.archive.ubuntu.com feisty/universe Packages                      
Err http://security.ubuntu.com feisty-security/main Packages                  
  403 Forbidden [IP: 91.189.88.37 80]
Ign http://ch.archive.ubuntu.com feisty/universe Sources                      
Err http://security.ubuntu.com feisty-security/restricted Packages             
  403 Forbidden [IP: 91.189.88.37 80]
Err http://security.ubuntu.com feisty-security/main Sources                    
  403 Forbidden [IP: 91.189.88.37 80]
Err http://security.ubuntu.com feisty-security/restricted Sources           
  403 Forbidden [IP: 91.189.88.37 80]
Ign http://ch.archive.ubuntu.com feisty/multiverse Packages                 
Err http://security.ubuntu.com feisty-security/universe Packages
  403 Forbidden [IP: 91.189.88.37 80]
Ign http://ch.archive.ubuntu.com feisty/multiverse Sources
Err http://security.ubuntu.com feisty-security/universe Sources
  403 Forbidden [IP: 91.189.88.37 80]
Ign http://ch.archive.ubuntu.com feisty/main Packages
Err http://security.ubuntu.com feisty-security/multiverse Packages
  403 Forbidden [IP: 91.189.88.37 80]
Ign http://ch.archive.ubuntu.com feisty-updates/main Packages                  
Err http://security.ubuntu.com feisty-security/multiverse Sources              
  403 Forbidden [IP: 91.189.88.37 80]
Err http://security.ubuntu.com feisty-security/main Packages                   
  403 Forbidden [IP: 91.189.88.37 80]
Ign http://ch.archive.ubuntu.com feisty-updates/restricted Packages            
Ign http://ch.archive.ubuntu.com feisty-updates/main Sources
Ign http://ch.archive.ubuntu.com feisty-updates/restricted Sources
Err http://ch.archive.ubuntu.com feisty/main Packages   
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty/restricted Packages
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty/main Sources
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty/restricted Sources
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty/universe Packages
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty/universe Sources
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty/multiverse Packages
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty/multiverse Sources
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty/main Packages
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty-updates/main Packages
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty-updates/restricted Packages
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty-updates/main Sources
  403 Forbidden [IP: 130.59.10.35 80]
Err http://ch.archive.ubuntu.com feisty-updates/restricted Sources
  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz  403 Forbidden [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz  403 Forbidden [IP: 91.189.88.37 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.88.37 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/source/Sources.gz  403 Forbidden [IP: 91.189.88.37 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.88.37 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/source/Sources.gz  403 Forbidden [IP: 91.189.88.37 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz  403 Forbidden [IP: 91.189.88.37 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz  403 Forbidden [IP: 130.59.10.35 80]
Failed to fetch http://ch.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz  403 Forbidden [IP: 130.59.10.35 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

After upgrade:
```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by overdrank on 2007-10-02
HI you may try and change your server location. System, administration, software sources and change your  server and then see if that helps.

---

### Post by ru0n on 2007-10-02
> **overdrank said:**
> HI you may try and change your server location. System, administration, software sources and change your  server and then see if that helps.

I've changed from Server for Switzerland to Main Server, to some german Server and again to the United States Server. Everytime after i change it asks me to reload or to close... if i click reload then i get another error message.

---

### Post by nowshining on 2007-10-02
it would be wise to post the error messages as like I said before in the box you can select and copy the error messages and paste them for others to see and help u out. Also they can be deleted in the box too. :D what Version of ubuntu are u running?

edit: n/m ur running feisty.

---

### Post by nowshining on 2007-10-02
in a terminal type or copy and paste following and then enter ur password - note ur password will not show as u type and this is normal, just type it out as normal and then hit the enter key. After which try what u were trying to do fhe first time around.

```

sudo rm /var/lib/apt/lists/partial/*

```

---

### Post by ru0n on 2007-10-02
> **nowshining said:**
> in
```

sudo rm /var/lib/apt/lists/partial/*

```

After that command:
```
 rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory 
```

[B]
Error Message:[/B]
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz: 403 Forbidden [IP: 91.189.88.37 80]
http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 403 Forbidden [IP: 91.189.89.6 80]
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty/main/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty/restricted/source/Sources.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty/universe/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty/universe/source/Sources.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty/multiverse/source/Sources.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-updates/restricted/source/Sources.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-security/restricted/source/Sources.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-security/universe/source/Sources.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz: 403 Forbidden
http://ftp-stud.fht-esslingen.de/Mirrors/ubuntu/dists/feisty-security/multiverse/source/Sources.gz: 403 Forbidden
```

**Another Error Message:**
Lockdown Editor cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by nowshining on 2007-10-02
hmm I got it installed and I'm using I386.

---

### Post by nowshining on 2007-10-02
what's odd tho is the "403 Forbidden" part which i see now hmmm.. I picked a url in the code box and tried to download it via firefox and all worked fine.

---

### Post by ru0n on 2007-10-02
[SOLVED!!!]

I somehow managed to solve the problem, no idea what exactly it was. A Friend asked me to switch servers once again, which i did a couple times. Then suddenly it worked. Already got both Programms installed! THANKS FOR THE GREAT SUPPPORT!!!
=D>=D>=D>=D>

---

### Post by overdrank on 2007-10-02
> **ru0n said:**
> [SOLVED!!!]

I somehow managed to solve the problem, no idea what exactly it was. A Friend asked me to switch servers once again, which i did a couple times. Then suddenly it worked. Already got both Programms installed! THANKS FOR THE GREAT SUPPPORT!!!
=D>=D>=D>=D>

Great and good luck! :guitar:

---

### Post by nowshining on 2007-10-02
I am so happy for u :) and ur welcome.

---

### Post by ru0n on 2007-10-03
Thanks alot! I've managed to get everything ready, there's just one last thing that really bothers me.

**The normal user is able to change the Background(Wallpaper) at any time...  Which is a bad thing, since they'll be able to put in a Wallpaper which isn't suited...**

I've got a emergency solution, which i wouldn't like to use since the Internet Browser icon would also be gone...  that would be disabling the nautilus desktop.
/apps/nautlius/preferences/show_desktop 

:confused:

---

### Post by ru0n on 2007-10-04
Is it possible to restrict the amount of pages you can Print? Like 5Pages every 10minutes or something?
::EDIT::

Found out how to do it:
[http://nixcraft.com/linux-software/469-ubuntu-linux-how-do-i-setup-print-quotas.html](http://nixcraft.com/linux-software/469-ubuntu-linux-how-do-i-setup-print-quotas.html)

::EDIT::
> 
Code:
sudo /etc/init.d/cups restart

-That command doesn't work for me.... when i changed the Quota Period and the Pagelimit, how can i save the settings?

::EDIT::
I was able to change the settings that i wanted to...
QuotaPeriod 600
PageLimit 10

then i entered
:wq

But after i logged into the "Guest" account, i still was able to print 12pages even though it was set to 10pages per 10minutes.
=(

---

### Post by ru0n on 2007-10-04
Can anyone help me with these Problems :confused:

---

### Post by nowshining on 2007-10-04
answering to also ur pm regarding the disable desktop right-click - no that's all i found out to is to disable nautilus drawing the desktop, u COULD move the icon to the teskbar (yes u can add icons to the taskbar and app icons - i have) and then use the pessulus program to disable right-clicking on the taskbar I have so that I don't accidenlty move it (i have two by the way) - by ping to the program and the command to open it up in terminal is pessulus and then hit enter, and then going to 

panel - lock down the panels........

for the printer you could to a clusty.com or google.com search also. :) or search.yahoo.com , etc..

---

### Post by ru0n on 2007-10-05
> **nowshining said:**
> answering to also ur pm regarding the disable desktop right-click - no that's all i found out to is to disable nautilus drawing the desktop, u COULD move the icon to the teskbar (yes u can add icons to the taskbar and app icons - i have) and then use the pessulus program to disable right-clicking on the taskbar I have so that I don't accidenlty move it (i have two by the way) - by ping to the program and the command to open it up in terminal is pessulus and then hit enter, and then going to 

panel - lock down the panels........

for the printer you could to a clusty.com or google.com search also. :) or search.yahoo.com , etc..


Well i've kind of disabled the Desktop right-click, i went into the Home Folder and selected the permission to only Access, now it's not possible to save or create anything on the Desktop. I know about icons on the taskbar, but they're kind of small there.... I've also locked down the pannels with pessulus. The Only thing you can still do with rightclicking is changing the background image.

I've heard something about the printer problem, not sure if its 100% true but the Cups Quota Printer settings dont work with a NetworkPrinter.

---

### Post by nowshining on 2007-10-05
oh wow :) never did think of that, it never did enter my mind :( sorry :P but yay you taught me something.

---

### Post by ru0n on 2007-10-05
> **nowshining said:**
> oh wow :) never did think of that, it never did enter my mind :( sorry :P but yay you taught me something.

Hehe! :)

I'm trying to lock the background image by editing the xml... i'll inform you if i have any luck!

---

### Post by nowshining on 2007-10-05
if you do then well you've taught me something to teach others. :) and I may very well lock the background from myself.

---

### Post by nowshining on 2007-10-05
oh by the way Desktop is the Desktop Folder - u also locked the WHOLE home folder from access from them.. :P so anything input into the Desktop folder appears on the desktop.

---

### Post by ru0n on 2007-10-05
No luck this far... but i've heard of a pretty decent solution...

That by every login... that it would put the Background-Image into the original state.

I don't know how to do it though, help anyone? :p

---

### Post by ru0n on 2007-10-08
Well i've got these Background files... Is there anyway to lock them down? To Disable Background changes? 

/home/blub/.gconf/apps/panel/toplevels/bottom_panel_screen0/background

/home/iblub/.gconf/apps/panel/toplevels/bottom_panel_screen0/background/%
gconf.xml

/home/blub/.gnome2/backgrounds.xml

/home/blub/.gconf/desktop/gnome/background

/home/blub/.gconf/desktop/gnome/background/%gconf.xml

---

### Post by nowshining on 2007-10-09
well have u tried changing the owner from the username to root, etc?? and applying those restrictions and such? on each file and or folder of infobar of course. :)

---

### Post by ru0n on 2007-10-10
Well... the only thing that happened is that everytime i log out, the original ubuntu image comes back... (now it would be nice if the image that i have choosen would come back by every log/in/out..)


::EDIT::
Found a buncha stuff
> [QUOTE]gconf /desktop/gnome/background/picture_filename &#8211;File to use for the background image

General Desktop Settings Say that you want, as a user to have a particular desktop image and you wanted to use gconf-editor to do so, you might first open gconf-editor and under 'Edit -> Find' search for 'background'. The results that return represent the virtual/logical directory structure of the gconfd settings. Thus changing one of these settings would affect ~/.gconf/desktop/gnome/background/%gconf.xml. 
Applications -> System Tools -> Configuration Editor
Edit -> Find # Case sensitive
[x] Search also in key names. If as the administrator you were looking at the Defaults Window in gconf-editor you would be able to change the default backgroud in the same virtual path, but it would represent /etc/gconf/gconf.xml.defaults/desktop/gnome/background/%gconf.xml. 
# You should never log into x as root!!!
DISPLAY=":0.0" sudo gconf-editor
File -> New Defaults Window
If as the administrator you were looking at the Mandatory Window in gconf-editor you would be realizing one of the major downfalls of gconf-editor - it only allows you to edit settings which already exist, not create or delete keys. Right now on your fresh install.... there aren't ANY mandotory settings. 
File -> New Mandatory Window
So now you have the option of (option here means "not-really-an-option") using gconftool-2. 
Code: using gconftool-2 to create mandatory setting 
 gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory \
  --type string \
  --set /desktop/gnome/background/picture_filename \
  /usr/share/pixmaps/wallpaper/desktop.png
It may look like a headache at first glance, but there are really only 4 variables in this command. Let me break this down as clearly as possible: 
Code: using gconftool-2 to create mandatory setting 
 gconftool-2 --direct \
  --config-source xml:readwrite:/etc/gconf/gconf.xml.[defaults|mandatory] \
  --type [int|bool|float|string|list|pair] \
  --set [/virtual/path/to/key] \
  [value(s)]
&#8226;	--direct - don't tell gconfd that settings are changing right now, write it out to a file 
&#8226;	--config-source - where the settings are to be written (hint: don't make a typo!!!) 
&#8226;	--type - what type of data the value is 
o	string - text, file paths 
o	bool - true/false 
o	int - 1, 2, 3 
o	float - 1, 3.14, 1024000000 
&#8226;	--set - change the value of the following key 
&#8226;	[value] - whatever the value is to be 
In the above example, notice that we specify the key 'picture_filename', but physically all keys belonging to the same virtual path exist in a similar physical path together in %gconf.xml, along with their values. 
Now, the Gnome guys would probably like to shoot me for saying this, but if you're a big fan of doing things the wrong way if I said this, because you'll most likely screw things up if you do it, but for the case above where no settings existed previously, you could do a little bash action as well. For example, if you were a cruel cruel guy, you might decide that the defaults were good enough for everyone - and you don't care if Sue is left-handed, she's using right-handed mouse settings from now on (dang it!!!), you might do this: 
Code: the wrong way 
 mkdir /etc/gconf/gconf.xml.mandatory/desktop/gnome/background/
 cp /etc/gconf/gconf.xml.defaults/desktop /etc/gconf/gconf.xml.mandatory/


Try this:
Code:
sudo gedit /usr/share/gconf/defaults/10_libgnome2-common
Change this line:
Code:
/desktop/gnome/background/picture_filename	/usr/share/backgrounds/warty-final-ubuntu.png
Replace /usr/share/backgrounds/warty-final-ubuntu.png with whatever you want your default image to be. I suggest that you also store that background in /usr/share/backgrounds/.
__________________



Gonna try testing every line of code.

---

### Post by ru0n on 2007-10-12
Is it possible to lock down the saving in OpenOffice? So that it always saves into the (tmp) folder?

---

### Post by nowshining on 2007-10-14
open up a terminal type gconf-editor
hit enter

/desktop/gnome/background

check gnome to draw the desktop and input in the path the path to the image ur wanting to use.

---

### Post by ru0n on 2007-10-19
Does Ubuntu 7.10 have any Background restricitions?
I heard it had some new things with which you could restrict openoffice and other things.

---

