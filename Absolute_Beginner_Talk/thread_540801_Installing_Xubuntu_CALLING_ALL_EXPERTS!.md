---
title: "Installing Xubuntu: CALLING ALL EXPERTS!"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by GA_M on 2007-09-02
Hi,

PLEASE, please help me.  I am wasting *hours and hours* trying to install Xubuntu.  I wake up in the morning thinking of different ways to install it -- this is driving me crazy!

Before I begin, let me say that I always check the sum, burn the CD as slowly as possible, and again check it when I place it in the CD-Rom.
---

It's an older computer that used to run Win98.  I completely deleted everything in order to convert it to Ubuntu or Xubuntu:
[LIST]
[*]BIOS/motherboard: ASUS P3V4X (AWARD BIOS, flashed to version ),  JumperFree PC-133 AGP/4X Motherboard
[*]Hard Drive:
[*]CPU: Pentium 3, 800Mhz
[*]RAM:4
[*]Other: SoundBlaster Live! (Model CT4830) sound; ATI Rage128 (32mb?) video; it IS connected to the internet (DSL, using router -- internet works when in Live CD mode)
[/LIST]
----

I tried installing Xubuntu 6.10 various times, but perhaps I wasn't clearing up the hard drive completely. Sometimes I was told I did not have authority to install it, other times, once I'd filled in the info (name, password, user settings) the installer would do its thing for a while and then suddenly disappear, and I'd find myself back in the Live CD mode with Xubuntu uninstalled.

So I downloaded *Darik's Boot & Nuke* and completely "nuked" the hard drive. From then on  I did that EACH time I tried to install Xubuntu or Ubuntu Server.

I tried installing Ubuntu *Server* 6.10 but I got this warning: 
[INDENT]Debootstrap warning: Failure trying to run chroot /target dpkg ~force  -- install var/cache/apt/archives/deb conf _ 1.4.72ubuntu9_all.deb    Check /var /log/sylog or see virtual console 4 for details.[/INDENT]

So I thought, that's OK, let's try Xubuntu 7.04. The Live CD gave me a taste of Xubuntu Feisty Fawn. I then clicked on "Install" and although it asked me my regional settings, username, password, and how to partition the 10 gig hard drive (I told it to use all the hard drive and do automatic partitioning) an error appeared at around 48% (Installing system):
[INDENT]Failed to copy files: faulty CD/DVD?  [Errno2] No such files or directory: '/rofs/usr/share/foomatic/db/source+printer/Epson-Stylus_Color_600xml'  This particular error is often due to a faulty CD/DVD disk or drive..."/INDENT]    (I don't even have an Epson printer.)

I again nuked the hard drive.  I then looked at every single Xubuntu "help me" posting to see if I could find the answer, but to no avail.

So I downloaded and burned at the slowest possible speed (using Ubuntu-recommended software) the PC (Intel x86) alternate install CD.  However, surprisingly (:mad: ) I got the following error:
[INDENT][!!] Install the base system -- Base system installation error.  The debootstrapping program exited with an error (return value 1). Check /var/log/syslog or see virtual console 4 for the details.[/INDENT]

I clicked on <Continue> and predictably got the following message:
[INDENT]Failed to install the base system.  The base system installation into /target/ failed. ...[/INDENT]

I'm eventually brought to the "Ubuntu installer main menu". I assume everything including and up to "Set up users and passwords" worked.  Installing the base system ALWAYS is the problem, and it's useless to try it again. So this time I decided to select "proceed with installation" and although I got a warning that the HD was not clean, I proceeded. Now it's asking me which kernel to install next. 

What should I do?  PLEASE, somebody help me!

Thank you.

PS: Stupid me, I'd installed Ubuntu Server 6.10 (even though there were error messages at some point!) but as I am moving soon, I wanted to leave a GUI computer behind for my family for them to do internet and word processing, and foolishly decided to start from scratch instead of installing a GUI on top of the server.  Darn!

PPS Is there some other non-Ubuntu Linux operating system that I could try that is user-friendly, easy on resources and with internet access/word processor/spreadsheet software, if this doesn't help?
-----

I'll try installing Xubuntu from the second, older CD-Rom, but I doubt that'll help.  I'll let you know if it does, though.

---

### Post by kerry_s on 2007-09-02
make sure you check your bios settings, some of the older systems have this anti virus setting, that screws up installs, turn that off if you have that.

try debian, it's much better for older systems.
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

if your cdroms no good, try the net installer, hopefully it works long enough to pass the job off.
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

---

### Post by jpsimm on 2007-09-02
I'm a newbie too and changed to Xubuntu from Ubuntu 6.04 by simply going to Snaptic Package Manager and selecting Xubuntu Desktop.  The conversion was automatic and thereafter I had the choice of either Gnome or Xubuntu at power up.

There were some things about X that I did not like however and went back to U.

jpsimm

---

