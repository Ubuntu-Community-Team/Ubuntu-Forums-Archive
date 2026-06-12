---
title: "Ubuntu Server with a GUI… on 128MB of RAM???"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by MPH on 2007-04-23
My only Linux experience was trying to build a SAMBA file and print server on a 1995 Gateway PC for our home network a few weeks ago.  The lack of command line documentation for dealing with PC hardware made it too frustrating to check out the installation and get the second parallel printer port (on an adapter card) to install properly.

I just brought home a 2001 Gateway E-3400 PC (community college surplus, $15) with 128MB of RAM as a better base for building the server…again I’ll install the basic server software from the Dapper server ISO and then install SAMBA.  This time around, I want to also install the ***ubuntu-desktop*** on the server to make the post-installation phase easier with the GUI tools.  Can ***ubuntu-desktop*** install and operate with just 128MB of RAM?

BTW… assuming the PC still works (it was sold “as-is”) and installs the server software, I’ll spring for the $33 to order 256MB of additional RAM so I can also use the server as a workstation and learn more about Ubuntu.  So if the GUI won’t work with 128MB of RAM, I’ll just need to be patient (not one of my strengths) and wait a few days more.

---

### Post by tgm4883 on 2007-04-23
your going to need something more lightweight than ubuntu-desktop, you could try xubuntu-desktop, as that only requires 128Mb to run (providing you dont install from the gui).  If that doesn't work, you could also try the unofficial Fluxbuntu

:EDIT:
Should have added that feisty with gnome requires 256

:EDIT #2:

Should have added that you might want to look into a different way to set it up (without a gui).  Maybe webmin?

---

### Post by MPH on 2007-04-23
Thanks, tgm4883, for your reply!

You made me curious about **webmin**.  Google found the following about webmin:

> Webmin consists of a simple web server, and a number of CGI programs which directly update system files like /etc/inetd.conf and /etc/passwd.

Doesn't webmin simply allow remote text editing... and nothing more?  If so, I could use Nano on the server ...right?

My concern is having available enough software tools so I know what hardware the server system considers installed and also being able to troubleshoot server hardware problems, etc.  I'm expecting to find those tools as part of the desktop... or that I'll need the desktop installed so I can install and use such tools.  Are my assumptions valid?

---

### Post by tgm4883 on 2007-04-23
Not really, it is more of a gui, but run through a webserver.  So in order to use it, you log in through a webbrowser to [http://servername:10000](http://servername:10000)

then its gui from there

---

### Post by MPH on 2007-04-23
Sorry that I wasn't very clear!  I really appreciate your input!!!

My first install, as I mentioned above, was a bust in spite to searching high and low for information.  Please bear with me as I try to explain better what I want to be able to do as admin of the server.  I definitely want to do more than edit the configuration files and then sit back.  I'm still thinking that webmin is a GUI text editor and won't do all that I want, as stated below.  _Please correct me if I'm wrong!!!_

The reason I wanted a desktop on the server is because the server natively uses a command line interface (CLI) rather than a GUI... and _I'd be perfectly okay with that_ EXCEPT I can't find even a simple list of commands beyond the common BASH commands.  I can't find *help menus* or documentation providing commands to:

[LIST=1]
[*]see what hardware the server considers installed... 
[*]run any hardware diagnostics...
[*]check the status or performance of any part of the system...
[/LIST]
I'd be extremely happy if the server provided a character-based "80x25" menu of commands like MS-DOS had.  My three previous threads sought such answers but no one replied.  I found posts from Ubuntu Noobies on other websites  expressing difficulty with using the CLI on a server... for example:

> _LAMP On Ubuntu 6.06 For Noobs_
 I, like many others, made the decision to attempt an install of Ubuntu 6.06 server with the preconfigured LAMP option without having ever attempted using Linux before. My goal was to build a setup that I could host my personal web site from. Embarking on this journey I had no idea how much knowledge I lacked and in turn would learn in my quest to host. I floundered around on forums and clung helplessly to Google for aid in all the places I fell short. I found that a really good resource for building a LAMP configuration for complete Linux noobs was either not available, or stuffed neatly in some Google Bermutan triangle which my browser was afraid to go. Hence, I am writing this as a partial documentation of my trials and tribulations with hopes of aiding all...

Almost all Ubuntu support documents I've examined assume the user has access to the Ubuntu desktop, which I sloppily refered to earlier as a GUI.  I need the tools and lists I'm used to in Windows and *apparently *I need some desktop package installed to get those features and to get much support from the user community.

Sorry if I let my frustrations do some of the typing... but I've concluded that a Linux noobie needs a desktop if he wants to do much more administrating a server than editing configuration files.  It's not about the GUI for me, it's knowing how to run enough programs to administer a server decently... and that includes knowing what's going on with the hardware.

---

### Post by ilovebsod on 2007-04-23
I use Dapper Xubuntu on a AMD k6/2 300mhz w/ 128MB RAM to play media (music/video files) on a continuous loop in my shop.  Hasn't been rebooted since it was released, runs fast.

you can download it here  [http://www.xubuntu.org/](http://www.xubuntu.org/)

if reinstalling isn't an option you should be able to install it by

sudo apt-get xubuntu-desktop

---

### Post by tgm4883 on 2007-04-23
Use xubuntu, if that doesn't work, try fluxbuntu, if still that doesn't work, then try webmin.  If you can use command line only, then use that, it is by far the best.  But if your skill in that are lacking (like mine) then use something lightweight.  Whatever you do, after you have it setup, have it boot to the command line.  That will make it much lighter on the computer, and you can always startx if you need to.  My setup with webmin is always at a command line and I access it from another computer when needed

Included are some screenshots of my webmin.  Hopefully they construe my explanation better.  I use webmin rather than a gui because I have a headless server and im still green to just working with command line.

---

### Post by mlentink on 2007-04-23
Completely agree. I run my server with the Xubuntu desktop, but I hardly eve use it, since Webmin does most of the jobs. Including editing text and conf files. Nice thing is, if you want to chance it, you can remotely supervise and manage your server.
Recommended

---

### Post by Ephilei on 2007-04-23
I'm running Fiesty on 192 RAM with Gnome and it's quite happy. Big software like Openoffice and gimp are slow enough to annoy most people, but Firefox, text editors, terminal, etc are fine.

---

### Post by tgm4883 on 2007-04-23
hmm, guess i shouldn't have trusted wikipedia

From wikipedia
> System requirements

The current Ubuntu release, 7.04, requires 256 megabytes of RAM, and, when installed to the hard disk, requires at least three gigabytes of hard-disk space if installed as the usual Desktop installation. The Server installation requires 64MB of RAM and 500MB of hard disk space.[41]

From Ubuntu Wiki
> Desktop installation

Most people will want to install a desktop system such as Ubuntu or Kubuntu. A desktop system is typically used for personal computing tasks and has a graphical user interface. 

Minimum requirements

    *      300 MHz x86 processor
    *      64 MB of system memory (RAM)
    *      At least 2 GB of disk space (for full installation and swap space)
    *      VGA graphics card capable of 640x480 resolution
    *      CD-ROM drive

If your system has less than 192 MB of system memory, use the Alternate Installation CD.


my bad

---

### Post by louieb on 2007-04-23
Check out post #9 of this [http://ubuntuforums.org/showthread.php?t=411370](http://ubuntuforums.org/showthread.php?t=411370)
install gnome-core on top of Ubuntu server. I tried it and found it used around 50MB ram with LAMP, ftp server, and ssh server  running. or just install openssh-server and log on to it from a computer with a GUI.

---

### Post by jeremy12 on 2007-04-23
I just wrote up this tutorial the other day it may help you a bit

[http://ubuntuforums.org/showthread.php?t=419530](http://ubuntuforums.org/showthread.php?t=419530)

main part of interest for you i believe will be Section 1 disabling the GUI from turning on with the PC does so that it is not wasting any recources

---

### Post by MPH on 2007-04-23
Great replies… I’ll got something from each!

Xubuntu does sound like a more economical GUI option than GNOME or KDE for a **true server**.  My home server will be very lightly loaded as a family file and print server… and I would like to try out the equivalent of the Ubuntu desktop ISO… so I was hoping that adding 256MB of RAM for a total of 384MB would make a decent server/desktop combo.  384MB is larger than the memory requirements for independent server and desktop installations (256+64=320) plus 320MB includes a lot of replicated code in the calculation.  Spending $33 for the 256MB RAM upgrade seems like a bargain if it allows the server and desktop to run concurrently…  I don’t expect great **desktop** performance anyway from the old PC… just a good test bed for learning more about Ubuntu Desktop and what apps run on it.  Does anyone see a problem with my reasoning?

(BTW… I have a keyboard, video, mouse (KVM) plus audio switch for my Windows PC and server so it should almost be like having a dual boot option.)

Jeremy12, I’ll also try out your tip to disable/enable the GUI!!!  With your tip, I’ll have an eraser if the 384MB of RAM isn’t enough to leave an idle GUI up and running!

tgm4883, I now see that webmin is a point and click interface for “editing” many configuration files.  Is SAMBA one of them?  I assume that a Windows PC could even be used to change the configuration files via webmin!

Does anyone know why webmin is a **universe **component rather than a **main**?  From a security standpoint, I love how main and restricted components are so conveniently updated if a security “fix” is needed.

I can see helping friends install an Ubuntu server on their old PCs and helping them with configuration issues from my home if webmin was on their server… IF I knew webmin was updated with the rest of the system by being a main component.  I’d hate to recommend webmin to anyone who would have trouble even running Ubuntu updates regularly!!!

---

### Post by tgm4883 on 2007-04-23
Yea SAMBA is one of them, as well as many other things (there are 3rd party modules too).  One thing I have noticed is that if I don't have a component installed (ie samba isn't installed) and i click on samba, it asks me if i want to install it.  But the installer works about 50/50.  Thats when ssh comes in handy to sudo apt-get install

---

