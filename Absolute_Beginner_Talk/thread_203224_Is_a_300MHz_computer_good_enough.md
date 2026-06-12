---
title: "Is a 300MHz computer good enough?"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by zedstillborn on 2006-06-24
I just installed ubuntu onto an  old HPcomputer.  I thought I would try it out on my old 300MHz with 128 MB of RAM. And Ubuntu runs incredibly slow.  Is my computer not grunty enough to run Ubuntu?  Does anyone have past experience running Ubuntu on an old computer?

---

### Post by Kilz on 2006-06-24
[QUOTE=zedstillborn]I just installed ubuntu onto an  old HPcomputer.  I thought I would try it out on my old 300MHz with 128 MB of RAM. And Ubuntu runs incredibly slow.  Is my computer not grunty enough to run Ubuntu?  Does anyone have past experience running Ubuntu on an old computer?[/QUOTE]
I would try Xubuntu on that hardware, it uses the lighter Xfce desktop. It dosnt require as much resources as gnome dose in Ubuntu

---

### Post by confused57 on 2006-06-24
You could try Xubuntu alternate CD installation, firefox would be slow on your computer so you may want to install dillo...if you're connected to the internet.

If you have a fast internet connection you may want to try Ubuntu Lite:

[http://www.ubuntuforums.org/showthread.php?t=98233&highlight=ubuntu+lite](http://www.ubuntuforums.org/showthread.php?t=98233&highlight=ubuntu+lite)
or
```
sudo aptitude update
sudo aptitude install x-window-system-core xterm gdm icewm menu firefox synaptic
```
I have a 500 MHz, 256 ram & Ubuntu runs pretty slow on it, Xubuntu is a lot faster.

---

### Post by az on 2006-06-24
[QUOTE=zedstillborn]  Is my computer not grunty enough to run Ubuntu?  Does anyone have past experience running Ubuntu on an old computer?[/QUOTE]
It will run much better with 256 megs of ram or more.  That is the minimum suggested fo rthe desktop.

Xubuntu will be better.  Also, if it is a pentium, you will see some improvement by installing the 686 kernel.  Install linux-686.

If Xubuntu is still too slow, install icewm.  Install the package nemed "menu" too.  Log out and then log back in and pick the icewm session.

On a sub-500Mhz computer, windows will probably run faster.  On modern (greater than 2 GHz) computers, ubuntu should run faster than windows.

---

### Post by Sef on 2006-06-24
Another option would be to install fluxbox: it is the lightest of the lightweight window managers.

---

### Post by az on 2006-06-24
[QUOTE=Sef]Another option would be to install fluxbox: it is the lightest of the lightweight window managers.[/QUOTE]
I think the difference in memory use and speed is negligeable ( I think windowmaker, icewm and fluxbox are all prety much equal).  Icewm just looks more familiar and had the neat cpu-meter and network-meter by default!

But please, install both fluxbox and icewm and take your pick.  (The secret to fluxbox is to right-click!)

---

### Post by Brunellus on 2006-06-24
[QUOTE=azz]I think the difference in memory use and speed is negligeable ( I think windowmaker, icewm and fluxbox are all prety much equal).  Icewm just looks more familiar and had the neat cpu-meter and network-meter by default!

But please, install both fluxbox and icewm and take your pick.  (The secret to fluxbox is to right-click!)[/QUOTE]
the fluxbox howto is linked in my .sig.

I prefer fluxbox for my "very light" wm needs.

---

### Post by Winblowz on 2006-06-24
Yet another option would be to use Gentoo. You can configure your system exactly to your hardware, and load times would be much faster. The major downside to using Gentoo though would be the compile times would be slow as hell because of your hardware.

[http://gentoo.org](http://gentoo.org)

---

### Post by catlett on 2006-06-24
I prefer ubuntu-lite to xubuntu. Ubuntu-lite runs icewm. You can add it through a repository if you have a little know how. Just in case you do here are the instructions.

You need to add a repository to your source list so enter this command intro the terminal ```
sudo gedit /etc/apt/sources.list
``` Add this line to the end of the list```
 deb http://blueeyedcreature.net/ubuntu ./
``` Save and close gedit. Then refresh the cache and install ```
sudo apt-get update
``````
 sudo apt-get install ubuntu-lite-desktop
``` I forget if you get a prompt about changing login managers, if it does you need to choose.  If you only want to run ubuntu-lite then say yes when asked if you want wdm as your login manager or choose gdm to keep gdm which is ubuntu's. 

If you keep gdm then you will have to change sessions through "options" to "icewm" to get ubuntu-lite. Go here for more info on ubuntu-lite and alternative installation methods. [http://www.ubuntulite.org/dokuwiki/doku.php](http://www.ubuntulite.org/dokuwiki/doku.php)

---

### Post by WADemosthenes on 2006-06-24
If you are well acquainted with Linux and want a desktop as fast as a newer computer with ubuntu, you can use DSL (Damn Small Linux).  I tried it, but came back to xubuntu, it is difficult to understand.  I have also tried Vector, which is faster than xubuntu, but no where near as user friendly (in my opinion).  So if you need user friendly (like me), I would use xubuntu (or the lite desktop if you like, it's rather simple to do as well).  I have xbunutu on my 364 mhz laptop, and it works okay.  

The web browser Epiphany is faster than Firefox, but will run JavaScript and flash, unlike dillo, which is fast, but impractical because it doesn't run java or flash.  Don't use Open Office if you can help it, nor other large applications.  

Above all, use the ubuntu wiki, it is extremely helpful.  There is an article on installing on low memory systems going from a server install (although if you are like me and you are new at this I would just use xubuntu, that's what I did), information about what to do once you set up your system, and other extremely helpful information.



PS:
If you want to use Ubuntu Lite, here are some more extensive directions, that go step by step.  [http://ubuntuforums.org/showthread.php?t=98233&page=2&highlight=ubuntu+lite+desktop+Howto](http://ubuntuforums.org/showthread.php?t=98233&page=2&highlight=ubuntu+lite+desktop+Howto) Post #17 is best:
> **DariusTriplet]Here's a (somewhat) simplified guide:

1) Put the Ubuntu install CD in the drive and (re)boot your computer.
2) You'll encounter a screen with the Ubuntu logo that asks about the type of installation said:**
> http://blueeyedcreature.net/ubuntu[/url] ./

This will allow for your computer to download and install the ubuntu-lite-desktop package, which is the point of this exercise.  

After you add that line, press CTRL-O to save the changes.

6) Only two more commands, and you're ready to go! Type at the prompt:


Code:

sudo apt-get update

which will let APT (the utility that communicates with the repositories and handles package downloads/installations) know that you changed sources.list. After that finishes, type:


Code:

sudo apt-get install ubuntu-lite-desktop

This downloads and installs the ubuntu-lite-desktop package.

After that finishes, type


Code:

sudo reboot

to restart your computer. After the reboot, you should be at a new login screen; if you are, then Ubuntu Lite will have properly installed!

As previously stated, if you have any questions, please ask; we're more than happy to help!

---

### Post by fuscia on 2006-06-24
openbox, dillo, sylpheed-claws, xfe, feh, mp3blaster, nano are all lightweight and would probably be fine on what you've got (which is about half of my old desktop).

---

### Post by xelink on 2006-06-25
[QUOTE=azz]It will run much better with 256 megs of ram or more.  That is the minimum suggested fo rthe desktop.

Xubuntu will be better.  Also, if it is a pentium, you will see some improvement by installing the 686 kernel.  Install linux-686.

If Xubuntu is still too slow, install icewm.  Install the package nemed "menu" too.  Log out and then log back in and pick the icewm session.

On a sub-500Mhz computer, windows will probably run faster.  On modern (greater than 2 GHz) computers, ubuntu should run faster than windows.[/QUOTE]
so you're saying that my opteron 165 will run faster on windows on stock clock settings(never mind the fact that it's more or less on par with a 3.0GHz pentium D on stock... I run it at 2.6-3.0 though, heh)

remember mhz isn't the biggest factor in determining speed. a 300mhz k6, G3, or cyrix will kill a 300mhz PII, and a 1GHz P3 a 1.2GHz Celeron D or p4

again shift towards some of the lighter apps and try to get more ram if possible.

---

### Post by SkyNet2029 on 2006-06-25
Ubuntu, or even Kubuntu for that matter, will run fine on a 300Mhz with 128Mb of Ram. You just need to figure out what is actually using those resources before you switch to a faster, but IMHO, super-ugly GUI's, with far-less functionality. 
A good place to start is by preventing any unnecessary services from starting up at boot. Things like:
Cups, HPlip, Rsync, Fetchmail, Postmail, etc. are a good place to start. You could also check to make sure that you 
have a decent amount of swap allocated to compensate for
the lack of enormous amounts of physical ram. Don't forget to disable all of your system's BIOS-caching 'features' by way
of your system BIOS settings. Let Linux handle all of that, since its better equipped to than the BIOS is. Small things like Ram-timings (not-really small actually, heh) or USB being enabled on your machine via BIOS when you don't use USB can make quite the difference on a resource limited machine.

---

### Post by catlett on 2006-06-25
[QUOTE=xelink]so you're saying that my opteron 165 will run faster on windows on stock clock settings(never mind the fact that it's more or less on par with a 3.0GHz pentium D on stock... I run it at 2.6-3.0 though, heh)

remember mhz isn't the biggest factor in determining speed. a 300mhz k6, G3, or cyrix will kill a 300mhz PII, and a 1GHz P3 a 1.2GHz Celeron D or p4

again shift towards some of the lighter apps and try to get more ram if possible.[/QUOTE]
My personal experience is that ram is the key to speed. I have a couple of old computers that I experiment with. One is a PII with 300mhz. I run Edgy on it (edgy is the next version of dapper, it is still a beta) without any problems but I have 512mb of ram.

The best suggestion is the above. Tweak your configuration to keep the resource hogs from starting. BUM is a good application for that (BUM is boot-up manager) If you don't have it install it with```
 sudo apt-get install bum
``` It will be under System<Administration after it is installed.

Also the Gnome Control Center has a "Sessions" category. Select "startup programs". You can remove any unwanteds apps from startup here as well.

Last just do a little hunting. Open Synaptic Package Manager and browse. There are thousands of apps available. Use terminal based apps for the best speed. For example use vi or nano instead of gedit to edit text files. If you need a gui app, look for the least rersource hungry. i.e. use Abiword instead of Open Office.org Writer.

Last you can try the many distros available for low resource boxes. My favorite Ubuntu low resource is ubuntu-lite. My favorite all around low resource distro is Puppy Linux [http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1) It is a live cd but you can install it to the hard drtive.

---

### Post by WADemosthenes on 2006-06-26
When using Damn Small Linux the status of my computer was always on the desktop, so I looked at it alot.  It showed that when doing normal things (firefox, abiword, etc) my proccessing speed always topped out when about half the ram was being used (365 mhz and 128 mb of RAM).  I don't know if the RAM would have caught up if I experimented more (I hated DSL, got rid of it after two days), but proccessing power seemed to be what got me.  But maybe my computer works differently, or maybe I screwed it up somehow, I'm don't know :D

---

### Post by catlett on 2006-06-27
Obviously you can't ignore processor speed but if you have an old Pentium a big ram boost gives a big performance bost.
Meaning if I took an old PII with as 300mhz processor and 64mb of ram and upgraded to a P3 700mhz processor, you aren't going to get a huge boost in performance.
But if I take that PII system and upgrade the 64mb of ram to 256mb of ram, there will be a huge difference in performance.
Nothing outways a new dual core 3+ghz chip but if you want to get an old computer running well, get some more ram. I run Edgy on a PII 300mhz with 256mb ram. I dual boot with Puppy linux and Puppy flies like it is running on my P4 :-D

---

### Post by jis on 2006-10-15
There is some information about resource need of different window managers in a Stem Debian's Desktop FAQ [chapter]("http://debian.cante.net/stem/faq/index.html#can_i_use_different_window").
(More information about Stem Debian is available [here]("http://debian.cante.net/stem/").)

---

### Post by Klaidas on 2006-10-15
>  Is a 300MHz computer good enough?
Someone needs an upgrade! ;)
Well, you could try Xubuntu - it works better on slow hardware, but again, my suggestion is to upgrade :)

---

### Post by jis on 2006-10-15
> **azz said:**
> 
Xubuntu will be better.  Also, if it is a pentium, you will see some improvement by installing the 686 kernel.  Install linux-686.


According to the description of linux-686 package is suitable for Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV. I have linux-386 installed. (I think there is no way to select another kernel during install from any Ubuntu PC (Intel x86) desktop CD.) Is it enough to install linux-686 to upgrade to 686 kernel? Do I have to uninstall linux-386? (I think I have previous versions of linux-386 available via Grub menu.)

---

### Post by jis on 2006-10-15
> **WADemosthenes said:**
> 
The web browser Epiphany is faster than Firefox, but will run JavaScript and flash, unlike dillo, which is fast, but impractical because it doesn't run java or flash.  Don't use Open Office if you can help it, nor other large applications.  


Dillo does not even support Cascading Style Sheets, consequently most pages would look stripped-down on Dillo. (There is support for CSS in most mobile phone browsers today.)

OpenOffice.org is very slow to start. It takes maybe five times longer time to start than MS Office 2000 in Windows. But AFAIK it is currently the only office suite that has full support for OpenDocument format. (See [the Wikipedia page]("http://en.wikipedia.org/wiki/OpenDocument").)

---

