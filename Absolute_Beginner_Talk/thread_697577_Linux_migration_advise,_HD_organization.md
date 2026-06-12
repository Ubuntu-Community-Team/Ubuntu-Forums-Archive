---
title: "Linux migration advise, HD organization"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Mike V on 2008-02-15
Hi all, first of all, I would like to apologize in advance for any mutilation/degradation/bad spelling/etc to the English language, as you can see from my info, English is not my native language besides I never attend to a language school or something like that.

Ok, Ive been using Linux (again, my first try was several years ago with KNOPPIX and it wasn't right for me then) since January, at my job I use primarly windows but I have to do some things with two Linux boxes (red hat and Centos) so I decided to give Linux another chance because I really like what linux has to offer, I downloaded Debian and Ubuntu (Desktop and Server), I like them, I'm going to try Kubuntu too (more on that later) XD, the thing here is that my primary hard drive is a mess, sometimes doesn't boot (I have problems with the PCBA), the other one is a 4 GB seagate HD from the stone age, and its going to explode anytime soon, I will buy a new 160 GB SATA HD and Im doing a plan to migrate all my data to new the HD and switch to Ubuntu as my main OS, so having said that here is my plan to do this, any advice would be highly appreciated.

Current system:
10 GB - Windows XP SP2 (NTFS)
70 GB - DATA, personal data mp3s, movies, documents, etc (NTFS)
        Note: I have Ubuntu in this partition installed via Wubi (10 GB)
---------------------------------------------------------------
80 GB - Desktop

03 GB - Ubuntu LAMP Server (ext3)
01 GB - Ubuntu swap (swap)
---------------------------------------------------------------
04 GB - Server

Future System:
20 GB - Windows XP SP2 (NTFS) (justification: Need to run some apps there :()
20 GB - Ubuntu Desktop 7.10 (ext3) (justification: Do I need to say something?)
20 GB - Kubuntu Desktop 7.10 (ext3) (justification: see note 1)
20 GB - Debian 4.0 (ext3) (justification: see note 1)
05 GB - linux distros swap (swap) (is this possible?, can I share the swap between the three distros?)
50 GB - DATA, my personal data (NTFS) (justification: need to be NTFS because every SO I'm installing can read it)
25 GB - DATA, share between Linux and Windows (FAT32) (justification: If I need to share data between distros that goes here)
---------------------------------------------------------------
160 GB - Desktop

70 GB - Ubuntu LAMP Server 7.10 (ext3)
10 GB - Ubuntu swap (swap)        
---------------------------------------------------------------
80 GB - Server (see note 2)

Note 1: I want to be proficient at the three and sometimes things don't work exactly the same way.
Note 2: This is the HD with I'm having problems in the first place, but I'm going to have a backup in the new HD while I'm get a new HD for this.

That is how I want to have my two boxes at the end of the day, but I have this problems/doubts/comments right now: 

a) If I can transfer my current Wubi-Ubuntu install over, that would be great, if don't, I can reinstall, I don't have many configurations there, just all the updates, that I would need to download again :( but it can be solved.
b) How can I transfer my server data to the other HD, I want to transfer the data and expand the partitions from 3 to 70 and from 1 to 10 for the system and the swap.
c) As I stated before, can I share swap partitions?
d) If I install SAMBA can I access from the internet to my server via ftp and from there access my desktop data?, I will mount the desktop folders in the server, but it will work?

Any advise to get this done in the weekend and be up and running by Monday? Any suggestion to make this better?

Note 3: I don't have a CD/DVD burner so I cant burn anything and must relay in booting images from HD 
Note 4: I have a Celeron at 2.23Ghz and 512MB of RAM
Note 5: Sorry for the huge post, but I wanted to give you as much information as you needed, to help me.

---

### Post by Golem XIV on 2008-02-15
Hi Mike

I'll try to answer what I know:

> **Mike V said:**
> 
20 GB - Ubuntu Desktop 7.10 (ext3) (justification: Do I need to say something?)
20 GB - Kubuntu Desktop 7.10 (ext3) (justification: see note 1)


You can either **sudo apt-get install kubuntu-desktop** (if you've installed Ubuntu) or **sudo apt-get install ubuntu-desktop** (if you've installed Kubuntu.  The inner workings are the same, I don't see the need for 2 separate partitions.

> **Mike V said:**
> 
c) As I stated before, can I share swap partitions?

I don't see why not.  5 GB is a bit much IMO, 2 GB should be more than enough.
> **Mike V said:**
> 
d) If I install SAMBA can I access from the internet to my server via ftp and from there access my desktop data?, I will mount the desktop folders in the server, but it will work?

You don't need SAMBA to set up an FTP server.  You need SAMBA to access Linux systems from within a Windows workgroup or domain - we're talking home or corporate LAN here.  For remote access you should use some kind of VNC (sorry I can't help you much more there).

---

### Post by Mike V on 2008-02-15
First, thanks for the reply.

> **Golem XIV said:**
> Hi Mike
You can either **sudo apt-get install kubuntu-desktop** (if you've installed Ubuntu) or **sudo apt-get install ubuntu-desktop** (if you've installed Kubuntu.  The inner workings are the same, I don't see the need for 2 separate partitions.


Yeah I know, but Im I going to have problems with mixed apps or something? like screwing one app because it doesn't work with Gnome/KDE or something? is this going to have an impact on performance?

> **Golem XIV said:**
> 
I don't see why not.  5 GB is a bit much IMO, 2 GB should be more than enough.


Cool, I wonder if it is some table to look up at this, like if you have 1GB of RAM you are better with XX MB/GB of swap partition.

> **Golem XIV said:**
> 
You don't need SAMBA to set up an FTP server.  You need SAMBA to access Linux systems from within a Windows workgroup or domain - we're talking home or corporate LAN here.  For remote access you should use some kind of VNC (sorry I can't help you much more there).

It's a home network, well I will use VNC to access my Desktop and do some tasks, but what I want here is to access my DATA files from an outside network, but without having to access the desktop and forwarding ports, etc (only the VNC ones), I want my server to be visible from outside but not my desktop (I don't know if I'm explaining this correctly), and since my DATA it's going to be at the NTFS partition in the Desktop drive I think I need SAMBA, obviously this is temporary, because eventually I will get a replace for the 80 GB defective drive and Im going to switch everything to the server, so the desktop only has the OS.

---

### Post by indytim on 2008-02-15
I'll chime in on another option for you to consider:

I'd recommend keeping the data partition  at ext3.  There is a utility that can be installed on the Windows side to see and write to ext2 & ext3.  I'm using it on my Win2k to access all of my data storage partitions (all of them are ext3).

I think you also referenced a LAMP server.  I'm assuming you're running it from within Ubuntu or Kubuntu.

Best,

IndyTim

p.s.  Had the occasion to visit you hometown several time on business :)

---

### Post by Golem XIV on 2008-02-15
General rule of thumb for swap space is 2xRAM.  However, it depends heavily on the kind of usage your system will have.  For standard, everyday use (mail, web, text processing, low-demand games) you can easily get away with less.  For stuff that requires more muscle (for example, if you expect your server to handle a lot of work), you could increase it.  Also, Linux IMO manages memory a lot better than Windows.  While XP would start paging even if I only fire up Notepad (regardless of the fact that there is a lot of RAM still available), I've been watching my swap usage in Ubuntu for the last 15 minutes and I see it flat on 34 MB.  All this is running comparatively the same software - Firefox, Evolution, Skype, Pidgin - the only things I don't run in Linux and I do in Windows are my virus scanner and firewall (but then again, I run compiz in Ubuntu).  As you can see, Linux is a lot more efficient.

As for the KDE/Gnome thing,  there is only one problem and it's question of taste.  You see, when you install both desktops, the applications menus on both will have all apps from both environments included.  This overloads the menus, makes it more difficult to find the app you want, and since KDE doesn't "see" Gnome icons and vice versa, it also looks godawful ugly.  It can be fixed, but it requires some work and patience.  If this doesn't bother you, go for it because KDE apps will work happily under Gnome and Gnome apps won't have a problem with the KDE environment, so you don't need to worry about it.

---

### Post by Golem XIV on 2008-02-15
Oh, yeah, another advice:

Get yourself an external HD enclosure (just the box, like an adapter) and put your old disk into it.  Then install the "temporary" Linux distros - the ones you just want to play with and don't plan on keeping - onto that.  Even if the disk eventually dies, you didn't have anything of value there, so no big loss.

I did this with an old 40 GB drive and at the moment I am using it as external storage/backup, but as soon as I can get some time on my hands I'll use it for an LFS project :)

---

### Post by Mike V on 2008-02-15
> **indytim said:**
> I'll chime in on another option for you to consider:

I'd recommend keeping the data partition  at ext3.  There is a utility that can be installed on the Windows side to see and write to ext2 & ext3.  I'm using it on my Win2k to access all of my data storage partitions (all of them are ext3).


Yeah I heard about it, but it is safe? because if it is, the partition file system problem is solved XD

> **indytim said:**
> I think you also referenced a LAMP server.  I'm assuming you're running it from within Ubuntu or Kubuntu.

Yeah, Im running the server from Ubuntu 7.10 on another HD/Computer

> **indytim said:**
> p.s.  Had the occasion to visit you hometown several time on business :)

Really? cool, business, uh?, do you work for a "Maquiladora"

> **Golem XIV said:**
> General rule of thumb for swap space is 2xRAM.  However, it depends heavily on the kind of usage your system will have.  For standard, everyday use (mail, web, text processing, low-demand games) you can easily get away with less.  For stuff that requires more muscle (for example, if you expect your server to handle a lot of work), you could increase it.  Also, Linux IMO manages memory a lot better than Windows.  While XP would start paging even if I only fire up Notepad (regardless of the fact that there is a lot of RAM still available), I've been watching my swap usage in Ubuntu for the last 15 minutes and I see it flat on 34 MB.  All this is running comparatively the same software - Firefox, Evolution, Skype, Pidgin - the only things I don't run in Linux and I do in Windows are my virus scanner and firewall (but then again, I run compiz in Ubuntu).  As you can see, Linux is a lot more efficient.

Yeah I know, thats the reason I take the final step into converting myself into a full dedicated Linux user rather than using Linux as a second SO, in Windows you need to reinstall roughly every six months, in order to get the system back on performance.

> **Golem XIV said:**
> As for the KDE/Gnome thing,  there is only one problem and it's question of taste.  You see, when you install both desktops, the applications menus on both will have all apps from both environments included.  This overloads the menus, makes it more difficult to find the app you want, and since KDE doesn't "see" Gnome icons and vice versa, it also looks godawful ugly.  It can be fixed, but it requires some work and patience.  If this doesn't bother you, go for it because KDE apps will work happily under Gnome and Gnome apps won't have a problem with the KDE environment, so you don't need to worry about it.

I dont mind "customizing" XD

> **Golem XIV said:**
> Oh, yeah, another advice:

Get yourself an external HD enclosure (just the box, like an adapter) and put your old disk into it.  Then install the "temporary" Linux distros - the ones you just want to play with and don't plan on keeping - onto that.  Even if the disk eventually dies, you didn't have anything of value there, so no big loss.

yeah, in fact, I'm going to use this HD for the server (I will have a daily backup in the fresh new HD) until I can afford another one to replace this.

---

### Post by Mike V on 2008-02-15
I have a few things that I'm still figuring out how to do:

1.- How can I transfer my current wubi-ubuntu installation?
2.- How can I transfer my current ubuntu server installation to a bigger HD?
3.- If I install everything but Windows on an ext3 partition, I could access all my files from the server, but lets say I map some folders from the desktop in the server, this folders are going to be locked or something?

---

