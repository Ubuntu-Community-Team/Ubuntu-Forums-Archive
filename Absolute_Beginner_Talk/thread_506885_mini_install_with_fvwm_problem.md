---
title: "mini install with fvwm problem"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by killphil on 2007-07-22
I'm trying to setup an old computer I had laying around for a email and web machine for my younger sisters who keep infecting my mothers machine with malware (she won't give up windows).

Specs: Emachines etower 533id2- 533mhz celeron, anaheim 2 - MB, DVDRom (not sure what brand), Seagate 15GB HDD

Here's where I'm at right now.

1.Installed mini .iso.
2.Reboot and login
3.Edit sources list
sudo nano /etc/apt/sources.list
4.Uncomment all official repositories by removing # at the beginning of the line. Do not uncomment the narrative portions of that file; in other words, where you see a double hash mark (##) leave those lines alone.
5.Now hit Control+X.  It will ask you if you want to write changes.  Hit y then Enter.
6.sudo aptitude update
7.sudo aptitude upgrade
8.sudo aptitude install xorg
9.startx
10.sudo aptitude install -y xorg fvwm-crystal build-essential msttcorefonts
11.Now download the newest version.
wget [http://download.gna.org/fvwm-crystal/3.0.4/fvwm-crystal-3.0.4.tar.gz](http://download.gna.org/fvwm-crystal/3.0.4/fvwm-crystal-3.0.4.tar.gz)
12.untar file
tar -xvzf fvwm-crystal-3.0.4.tar.gz
13.When it's finished, change into the directory it creates.
cd fvwm-crystal-3.0.4
14. Install it over the old version
sudo make install

Now it says "sudo: make: command not found".  Sorry for the weird format.  I'm trying to make a consolidated how to so that I won't have to jump back and forth between 3 webpages again.

---

### Post by ddrichardson on 2007-07-22
automake isn't installed.

---

### Post by benx009 on 2007-07-22
install the package "build-essential" from the command line (something like "*sudo apt-get install build-essential*" i would think).  that should install the make package.

---

### Post by killphil on 2007-07-22
It worked.  Thanks.

---

### Post by killphil on 2007-07-22
New problem

Here's where I'm at now.

1.Install newer version
sudo make install
2.make sure X knows to trigger FVWM-Crystal when it starts up. Enter this command to create an .xinitrc file in your home directory.
nano -w ~/.xinitrc
3.Type this line into it
exec fvwm-crystal
4.Hit Control+O then Enter to write the file
5.Hit Control+X to exit nano.
6.startx

Here's what I get

(auth:  creating new authority file /home/rachel/.serverauth.8276

(: user not authorized to run the Xserver, aborting.
$sudo startx

(auth:  creating new authority file /home/rachel/.serverauth.8297

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove  /tmp/.X0-lock and start again.

---

### Post by killphil on 2007-07-22
problem solved.  I just rebooted, logged in, and startx and it works fine

---

### Post by kerry_s on 2007-07-22
wow, so complicated. why fvwm? 
debian is faster & supports more on older systems.
also with debian, you don't have to distro jump every time there's a new release, you can just add lenny & sid repos and update the whole system to the latest.


[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

it's like what your doing now:

use the net installer(" installgui " for the pretty installer), when it comes to package selection uncheck them all for a mini install. when it reboots

log in as root
apt-get install xorg gdm synaptic fluxbox
reboot(ctrl+alt+delete)
select fluxbox in the session menu and login as the user you created.
open synaptic and install what ever you want.

---

### Post by killphil on 2007-07-22
I tried debian yesterday and couldn't get wireless to work.  The support community(forums)  and documentation just doesn't seem as good as ubuntu.  They don't seem to like answering noob questions without being condesending.  I've only been using linux for a couple of months and it's awesome.  But I still need a lot of help with things that probably seem very stupid to power users.  Gotta start somewhere.  You're right though, debian is much faster.  Even with gnome.  Web browser was ungodly slow, but everything else flew.  I spent all night trying to get wireless to work.  Debian's ndiswrapper documentation blows.  This morning I decided to try the ubuntu mini install to see if I can get it to work.  I'm going to debian on my laptop though.  Plus, I don't get why they bash ubuntu.  I guess it's kind of like high school kids picking on middle school kids.  Seems a bit juvenille, especially when ubuntu is a major stepping stone to debian,arch, or gentoo for people like myself.

---

### Post by ddrichardson on 2007-07-22
Actually if its on an older machine and just for email - try one of the mini distros like [DSL]("http://www.damnsmalllinux.org/"). It supports ndiswrapper and runs fine on older machines, actually very quickly. Also very easy to install and support because its live cd based.

Debian users have been that way since time (Linux) began (speaking as a former Debian user) and you're right they do tend to talk down to new users. For years Debian users loved its complication and many saw Ubuntu as a dumbing down rather than a step forward to mass market.

---

### Post by killphil on 2007-07-22
I was hoping that ubuntu/fvwm would be a bit faster.  I downloaded DSL and puppy last night.  I'll have to give them a try.  I'll try dsl first.  Getting fvwm to work was a good experience for me since I've kind of avoided the command line whenever possible.

---

### Post by kerry_s on 2007-07-22
> **killphil said:**
> I tried debian yesterday and couldn't get wireless to work.  The support community(forums)  and documentation just doesn't seem as good as ubuntu.  They don't seem to like answering noob questions without being condesending.  I've only been using linux for a couple of months and it's awesome.  But I still need a lot of help with things that probably seem very stupid to power users.  Gotta start somewhere.  You're right though, debian is much faster.  Even with gnome.  Web browser was ungodly slow, but everything else flew.  I spent all night trying to get wireless to work.  Debian's ndiswrapper documentation blows.  This morning I decided to try the ubuntu mini install to see if I can get it to work.  I'm going to debian on my laptop though.  Plus, I don't get why they bash ubuntu.  I guess it's kind of like high school kids picking on middle school kids.  Seems a bit juvenille, especially when ubuntu is a major stepping stone to debian,arch, or gentoo for people like myself.


try using " ndisgtk " it's the gui for ndiswrapper, you just point and click. somtimes wiresless is just a bit**h, no matter what distro.

---

### Post by kerry_s on 2007-07-22
> **ddrichardson said:**
> Actually if its on an older machine and just for email - try one of the mini distros like [DSL]("http://www.damnsmalllinux.org/"). It supports ndiswrapper and runs fine on older machines, actually very quickly. Also very easy to install and support because its live cd based.

Debian users have been that way since time (Linux) began (speaking as a former Debian user) and you're right they do tend to talk down to new users. For years Debian users loved its complication and many saw Ubuntu as a dumbing down rather than a step forward to mass market.


straight debian is way better than DSL, if you need size than DSL, if you want ease of use, updated software, than debian can give that. and "yes" i do see ubuntu as dumbed down and butchered debian install.   :mad: :lolflag:

---

### Post by ddrichardson on 2007-07-22
:lolflag: The prosecution rests... :lolflag:

---

