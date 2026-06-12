---
title: "Minimal Installation Questions"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by mbechdel on 2007-02-13
Ok so, I just installed ubuntu on my main PC but now I'm trying to figure out if it is possible to install ubuntu on my old ghetto computer. It has 512mb RAM and 1.2gb of hard disk space. Therefore it meets the requirements for an ubuntu install without the desktop interface.

However, this is where I get confused, would it be possible for me to install X11 only and not gnome/kde/etc. Reason being, I'm short on HD space but want a graphical user interface.

The goal of this setup is to read data(music/movies) from other computers in my house and play it in my living room.

---

### Post by chris.snafu on 2007-02-13
if you could somehow get .3 more HD space, check out Xubuntu, only takes 1.5, and its not too shabby, or else you could always try out DSL (damn small linux) but thats tricky to get it the way you want, but it only takes 50 MBs of space.

---

### Post by lucia_engel on 2007-02-14
How about installing xorg and fluxbox (or other lightweight WM)? It shouldn't take that much space.

[https://help.ubuntu.com/community/Installation/LowMemorySystems]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

### Post by kerry_s on 2007-02-14
That's more than enough room for a system with the works. Start by doing a command-line/server install then build up from there. Here's what you should do->

command-line install
login
sudo su
nano /etc/apt/sources.list
comment(#) out the cdrom and uncomment all the repos
ctrl and x and y and enter to save
apt-get update
apt-get dist-upgrade
apt-get install x-window-system-core gdm fluxbox synaptic
type> reboot
select fluxbox from session menu and login
open synaptic and start trimming it down further, you want to get rid of what you don't need,fonts,extra xserver-drivers for cards you don't have,all the raid stuff,etc...
After you do that install a filemanager,editor,eterm->
sudo apt-get install emelfm leafpad eterm

These are very small, once those install, launch> sudo emelfm /usr/share
go into the /doc and /man folders and delete everything, that will give you even more space then start building the rest->
apt-get install firefox dillo xmms mplayer mozilla-mplayer flashplugin-nonfree

That will give you 2 web browsers 1 regular and 1 built to be fast, players for your music and movies,you will still need to install the w32codecs->
wget -c [http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.0_i386.deb)
sudo dpkg -i w32codecs_20061022-0.0_i386.deb

You might also need libdvdcss2-> 
wget -c [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
sudo dpkg -i libdvdcss2_1.2.5-1_i386.deb

That will be a very basic system and if you clean up the /doc and /man again you should still have just under a gig of space to play with.

---

### Post by mbechdel on 2007-02-14
Sweet, thanks for the info, I'll work from there. :)

---

