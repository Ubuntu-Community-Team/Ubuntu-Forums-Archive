---
title: "What are the min requirements for Ubuntu?"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by Talisker on 2005-12-02
Hi all

I spent the last couple of hours reading about the do's and don'ts.
I was planning on creating a dualboot on my primary laptop (WIN2k). It just happened that a friend of mine offered me hes old (and I'm afraid "old") laptop.
So, I have a couple of questions:

-What are the minimum system requirements to run Ubuntu?
-what is the recommended backup program to create a ghost image on a second HD in case the dualboot goes bad.

I appreciate the help.

---

### Post by aysiu on 2005-12-02
From Ubuntu's website: > Ubuntu 5.10 supports three (3) major architectures: Intel x86, AMD64, and PowerPC. Depending on your needs, you might manage with less than some of the recommended hardware listed in the table below. However, most users risk being frustrated if they ignore these suggestions.

128 megabytes RAM
2 gigabytes Hard Drive Space

Once again, the size of the installation will greatly depend on the software you install during setup. For most users, the default applications are suitable enough for general use.

Desktop

A standard desktop box, including the X Window System, full desktop environment, sound, office suite, email clients, etc. You'll need about 2 gigabytes of hard drive space using the standard desktop task. Generally, I'd say if you have under 256 MB, you'll have to run XFCE to make the computer usable. If you have 256 MB, you may find XFCE faster, but Gnome and KDE will operate. Gnome and KDE are optimal at 512 MB of RAM and above.

P.S. Gnome is the default desktop environment for Ubuntu
KDE is the default desktop environment for Kubuntu
XFCE is something you can install on either Kubuntu or Ubuntu but doesn't come as its own CD

Before committing to a dual boot, you may want to try the live CD. Otherwise, this dual boot guide is excellent: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by SickTwist on 2005-12-02
[QUOTE=Talisker]Hi all

I spent the last couple of hours reading about the do's and don'ts.
I was planning on creating a dualboot on my primary laptop (WIN2k). It just happened that a friend of mine offered me hes old (and I'm afraid "old") laptop.
So, I have a couple of questions:

-What are the minimum system requirements to run Ubuntu?
-what is the recommended backup program to create a ghost image on a second HD in case the dualboot goes bad.

I appreciate the help.[/QUOTE]

I have installed Ubuntu 5.10 (running GNOME) on a Pentium MMX 233 Mhz with 112 MB (I later upgraded it to 192 MB). I did some tweaking to minimize the RAM usage (disable icons on desktop, use only one panel, minimum number of panel applets, etc.) and it runs. It is slow, mind you, but it runs.

 There really isn't much harm in trying Linux on an old computer. The most likely scenario is that it will just run slowly. You'll have to find a *really* old machine (e.g. i286-era) before Linux starts giving you install headaches.

I would say the absolute minimum about of RAM for a graphical desktop would be about 96 MB but note that there are going to be limitations to a system such as this. RAM-hungry apps are out of the question (OpenOffice, Firefox) and you will have to minimize the number of apps you run simultaneously. If you are in a position to buy more RAM then do so. It's the best upgrade you can do on old hardware. There are limitations to how much RAM a motherboard can support so check that before buying.

There are many window managers and desktops available in the Ubuntu repositories that have varying degrees of resource usage and functionality. Here are some in order of least resource-hungry to most resource-hungry:

[Blackbox]("http://blackboxwm.sourceforge.net/")
[Fluxbox]("http://fluxbox.sourceforge.net/")
[IceWM]("http://www.icewm.org/")
[XFCE]("http://www.xfce.org/")
[GNOME]("http://www.gnome.org/") (Ubuntu default) / [KDE]("http://www.kde.org/") (Kubuntu default)

So as you can see GNOME or KDE will run the slowest. If they are too painful for you try something else.

There are also desktop apps that are faster/lighter than those included with Ubuntu. Some examples: [Leafpad]("http://tarot.freeshell.org/leafpad/") (text editor), [AbiWord]("http://www.abisource.com/") (word processor), [Gnumeric]("http://www.gnome.org/projects/gnumeric/") (spreadsheet), [Dillo]("http://www.dillo.org/") (minimal web browser), [Epiphany]("http://www.gnome.org/projects/epiphany/") (another web browser) and [Sylpheed]("http://sylpheed.good-day.net/en/") (e-mail client) to name a few. All of these are available in the Ubuntu repositories (you may have to enable Universe).

As for the second part of your question, there are a couple Free Software clones of Norton Ghost (tm): [Ghost for Linux]("https://sourceforge.net/projects/g4l") (G4L) is available as a CD image. There is also [Ghost for Unix]("http://www.feyrer.de/g4u/") (G4U) which is available as a CD image or two floppy disk images. If you do decide to dual boot with Ubuntu on your primary laptop, it is an excellent idea to make a backup before attempting the installation. At the very least, back up your personal data. Also, defragment all of the Windows partitions before starting the Ubuntu install. This will give you a better chance of avoiding data corruption if Ubuntu needs to resize the existing Windows partitions.

Good luck! :D

---

### Post by az on 2005-12-02
The dekstop starts to slow down a lot below 400 MHz (Pentium, with a huge cache - probably a lot higher for a Celeron or a Duron)  With 128 megs of ram, you are fine for the default desktop.  You will find things slow down as you open a lot of applications at once.  Anything less than 128 megs of ram is not reccommended.

You need just over 2 Gigs of Hard drive space for the default install.

You can install the X server and icewm in under one gig or hard drive space.

sudo apt-get install x-window-system-core gdm icewm menu mozilla-firefox xterm synaptic

---

### Post by patrick295767 on 2005-12-02
All informations are in it !!  Below 300-400Mhz desktop are a bit slow. RAM plays a big role. 64Mb is not enough. Even the Xterm is a big hug ! For internet, with 64MB, it's HELL 'cos mostly mozilla-firefox or Opera are also consumming lot of memory ... too much to say !
I tried all kind of linux on a 300 Mhz about, 64MB, it appears that older distributions slackware or mandrake or debian base were faster ... than this UBUNTU now kernel even with a lightest FVWM (that I recall you was programed to run on SX PC 486 sthg with 4MB ... Even using the fvwm doesnt help that that much 'cos even it's a bit slow sometimes). 
  
I have impression that the kernel is for sthg 'cos the corellinux (i am sorry of repeating thsi old distro not sooo great (xandros now)) had the KDE 1.1.2 and netscape and older kernel and was very pretty fast !!! 
I cannot explain this. I made trials with friends and it's a fact ! 
I cannot say why ... I don't know ... I am investigating.
 
If someone has more experience in the field, please give me some advices 'cos with Linux it's normally the total freedom to make your own system and make it as u desire and need !!
But experience and sometimes maybe too much are required , but everythg is possible !!! 
  
That's why we love this System !!
  
Kind regards, 
  
Patrick

---

### Post by KermitJr on 2005-12-02
As far as backup/ghosting goes, you can't beat parted .  Knoppix has it on the live CD.  I support backup over a network, file size limits (chopping for burn to CD) and various levels of compression.  I use it all the time.

Just note that if you restore to a larger disk or partition, you'll need to resize the partition with something like qtparted to realign the disk geometry.

As far as minimum requirements, I run Kubuntu on several Pentium 333 and 350s with 128-256 MB RAM and though slow, it works fine.  I may try for xfce4 soon if the menus all translate over easily.

Also, have you considered LTSP (Linux Terminal Server Project)?  You can run programs on a faster computer over the network transparently.  Apps run at the speed of the server, not the computer you're in front of.  Allows you to use a 486 at the same speed as a 3000+.

KJ

---

### Post by patrick295767 on 2005-12-02
I am using XDMCP on old PC's and result is amazing !!
  
On the other hand, videos (Avi, divX) is toooooo laggy : not possible !!
(sound on xdmcp server pc)
  
Otherwise, that's working like a normal fast & new pc !
(he was right, that's certainly the fastest solution)
  
kind regards, 

pat'

---

### Post by mcwtlg on 2005-12-02
I am running a web server / ftp server (I also download TV torrents for shows we missed (to be played on my wife's beefier PC) ) on a 400 mhz Celeron with 512 Megs of RAM.  The primary HD is a 6 gig, 5400 RPM and the "storage" disk is a 18 gig 5400 RPM.  It has an 8 meg Matrox Millenium II PCI video card, Soundblaster sound card, and a 3Com 10/100 ethernet card.  I do not have it set up to play videos so I do not know how it would do, but it plays mp3's just fine.

I use XFCE as my desktop environment.  I have run it on 256 megs of RAM under Gnome and it was pretty slow.  I need to download and configure video to test that, but I am sure it will play somewhat choppy in anything other than a small window.  I do not have a DVD player installed, but that will most likely change as a friend is giving me his old one to test with.

This machine has been completely built on donor / throw away parts.  It has been running Ubuntu for a year or so.  Before that, it was running Win2K.  I am now down to just one fully legal Windows box, as my wife's machine. I think if I were single, the only Windows machine I would have would be as a back up.  Since I am pretty new to Linux, I still find things I cannot do yet in it, but I am learning.

---

### Post by Talisker on 2005-12-02
wow, lots of info....:D 

I'll have a look at the "old" Laptop today. Since I can have it for free, it would be an excellent deal.
I can play with Ubuntu on a separate machine and don't have to worry about any screw ups. *G*
If the Laptop has enough CPU power, I'll sure get more memory.
Thanks for the help on that.

Regarding the backup:
I make backups of my personal files daily, of course.
It certainly would be nice to have a image of the HD, so I would be able to boot from a removable drive when things would go bad.

Question here:
-->As far as backup/ghosting goes, you can't beat parted . Knoppix has it on the live CD. I support backup over a network, file size limits (chopping for burn to CD) and various levels of compression. I use it all the time.

Just note that if you restore to a larger disk or partition, you'll need to resize the partition with something like qtparted to realign the disk geometry.<--

Parted is the programms name?

I have a 40 gig drivein my primary Laptop, using about 17 gig. 
I have an additional external USB drive (also 40gigs, 20 gigs free space) I would use for the backup. How does that inflict on realign the disk geometry?

Thanks

---

### Post by KermitJr on 2005-12-02
[QUOTE=Talisker]

Question here:
-->As far as backup/ghosting goes, you can't beat parted . Knoppix has it on the live CD. I support backup over a network, file size limits (chopping for burn to CD) and various levels of compression. I use it all the time.

Just note that if you restore to a larger disk or partition, you'll need to resize the partition with something like qtparted to realign the disk geometry.<--

Parted is the programms name?
[/QUOTE]

Typo on my part:  partimage is the program

[http://www.partimage.org/](http://www.partimage.org/)

qtparted is the resizer

[http://qtparted.sourceforge.net/](http://qtparted.sourceforge.net/)

Both are on Knoppix.  Not sure of Ubuntu LiveCD, though they should be... small and awesome tools.

My mom has a Win98 machine... she saves all data on a separate partition and I just reimage to the HDD from the data partition every few months to clean out the junk.

---

### Post by Talisker on 2005-12-02
Thanks Kermit, I'll check it out.

So, I got my free "old" Laptop..... :rolleyes: 
It is a Toshiba Tecra 700ct.... Old? oh yes...*G*

Well, unfortunatly the Laptop has only 32 MB Ram and the max is 48 MB. The RAM module is the size of your palm....*G* Kingston nevertheless.

Seems it wont do for Ubuntu... to bad...:sad:

---

### Post by KermitJr on 2005-12-03
Yes it will.  Running XFCE4, perhaps?  I'd fix it up to use for a few things.... could also make a router, firewall, dhcp server, but I think a light wm would work fine.  Install via net perhaps and set up swap. Start with server install only.

---

### Post by Talisker on 2005-12-03
[QUOTE=KermitJr]Yes it will.  Running XFCE4, perhaps?  I'd fix it up to use for a few things.... could also make a router, firewall, dhcp server, but I think a light wm would work fine.  Install via net perhaps and set up swap. Start with server install only.[/QUOTE]

I probly will mess around with it... since it is sitting under my desk...*G*
First I have to remember how to make a boot disk to get the CDrom support. Last time I did this I was using win3.x, now I have grey hair...*lol*

Tomorrow, Sunday will be a good day to perform some surgery...:D 

Thanks

Oh, the HD has only 2 Gigs... thats another drawback...

---

### Post by SickTwist on 2005-12-03
If you manage to get the Ubntu CD to boot, type this at the CD boot prompt (when you see the Ubuntu logo) and press Enter to do a server install:

server

That will only install the minimum packages to ensure that you don't fill up the HDD (Linux will not run right if the HDD fills up). Once the installer is done, you'll be presented with a log-in prompt. Log in with your name and password that you picked during the install. Then do the following command:

sudo apt-get install x-window-system-core xdm fluxbox dillo xterm

That will install these very light programs:
xdm - log in manager
fluxbox - window manager
dillo - web browser
xterm - terminal emulator

Synaptic will run annoyingly slow on that laptop. You're better off using apt-get at the command line. Firefox will run terrible with 32 MB of RAM. There are also links and lynx, two text-based browsers that you might want to install if dillo is too slow. GDM is also too bloated as it requires GTK2 and GConf; XDM is much more suitable for your machine.

You should also familiarize yourself with vi or some other command line editor.

Good luck!

---

### Post by Lovejoy on 2005-12-05
-Well, unfortunatly the Laptop has only 32 MB Ram and the max is 48 MB. The RAM module is the size of your palm....*G* Kingston nevertheless.

-Seems it wont do for Ubuntu... to bad...

I've been playing around with old computers that I get for free. I love ubuntu, but it is kind of heavy for some of them. I've been using Debian. You can do an install over the internet using only 3 or 4 floppies to get it going. Then after the basics are installed you have the option of installing the heavier desktops like KDE or manually selecting just what you need. You have to install some sort of X if you want graphical interface. 

It's fun to see what you can get the older computers to do.

---

### Post by patrick295767 on 2005-12-05
With one of the lightest X-desktop gui, e.g. FVWM ([www.fvwm.org)](www.fvwm.org)), why is the ubuntu distro rather slow for low memory and cpu <300MhZ ?
  
Is the kernel taking so much of ressources ?
Would older distributions, like mandrake 6-7, or redhat 7, ... with a fvwm offer greater performances (without USB (of course)) ?

Greetz'

Pat'

---

### Post by patrick295767 on 2005-12-05
[QUOTE=Lovejoy]-Well, unfortunatly the Laptop has only 32 MB Ram and the max is 48 MB. The RAM module is the size of your palm....*G* Kingston nevertheless.

-Seems it wont do for Ubuntu... to bad...

I've been playing around with old computers that I get for free. I love ubuntu, but it is kind of heavy for some of them. I've been using Debian. You can do an install over the internet using only 3 or 4 floppies to get it going. Then after the basics are installed you have the option of installing the heavier desktops like KDE or manually selecting just what you need. You have to install some sort of X if you want graphical interface. 

It's fun to see what you can get the older computers to do.[/QUOTE]
  
I am trying to install the KDE 1.1.2 and keep a rather fast ubuntu for my old pc... my results are not great ! Rather very difficult to install. I messed up my breezy. 
  
Let's get in touch in order to make relive our old pc, if you make progress or have further informations, plz let me know ...
  
Greetings, 

Patrick

---

### Post by Talisker on 2005-12-05
I got the Laptop to boot in dos with cd-rom support. I can't execute the install command tho..... what am I missing...
It lists a couple of directories and "Ubuntu" without file name. Shouldn't I have a install.exe or ubuntu.exe?

The Laptop does not support booting from the CDrom , so I have to load the floppy first.

Is there a way I could copy the most basic files (Ubuntu) on floppies?
:confused:

---

### Post by kalos on 2005-12-05
First I would recommend trying [Smart Boot Manager]("http://btmgr.sourceforge.net/about.html"). It will allow you to boot from CD.

(edit) Or, try [this post](http://www.ubuntuforums.org/showthread.php?t=75372) before resorting to installing debian and upgrading.

If that doesn't work, you could try to [install Debian (another Linux distro) from floppy]("http://www.debian.org/distrib/floppyinst") and you can then upgrade from [Debian to Ubuntu]("https://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge")
But this is all describing moving from Debian 'Sarge' to Ubuntu 'Hoary Hedgehog', so I don't know if it will work. (And only [some](http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge/talkback/1113587843) people have claimed complete success.

-kalos

---

### Post by Talisker on 2005-12-05
[QUOTE=kalos]First I would recommend trying [Smart Boot Manager]("http://btmgr.sourceforge.net/about.html"). It will allow you to boot from CD.

(edit) Or, try [this post](http://www.ubuntuforums.org/showthread.php?t=75372) before resorting to installing debian and upgrading.

If that doesn't work, you could try to [install Debian (another Linux distro) from floppy]("http://www.debian.org/distrib/floppyinst") and you can then upgrade from [Debian to Ubuntu]("https://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge")
But this is all describing moving from Debian 'Sarge' to Ubuntu 'Hoary Hedgehog', so I don't know if it will work. (And only [some](http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge/talkback/1113587843) people have claimed complete success.

-kalos[/QUOTE]


I installed the bootmanager, actually a neat programm :) 
Still, it doesn't want to boot from a cdrom, the live nor the install version. (the cd's are ok, they boot)

So, I can use a dos boot disk and I have cdrom access. Still I can't start the Ubuntu installer. The bootmanager doesn't even recognize the cdrom.

Maybe buy a second hd for my "new" laptop and install it there....*G*

Don't you hate when machines outsmart ya?????:mad:

---

