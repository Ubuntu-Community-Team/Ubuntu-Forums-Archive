---
title: "[SOLVED] Double Deluge"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by berZirker on 2007-09-28
I'm not sure where I went wrong anymore.  I now have 2 versions of Deluge BitTorrent Client in Applications>Internet.  One of them I can remove with Synaptec, but the other...?  I have uninstalled/reinstalled multiple times trying to break through to either side of having a functional program (there or not there at all.)  Here is the output when I tried to run a recently installed version of deluge from the terminal

no existing Deluge session
/home/berzirker/.themes/DarkCaramel/gtk-2.0/gtkrc:631: Unable to locate image file in pixmap_path: "Mscrollbar/thumb-grip-h-prelight.png"
/home/berzirker/.themes/DarkCaramel/gtk-2.0/gtkrc:634: Overlay image options specified without filename
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin TorrentFiles
Initialising plugin BlocklistImport
Initialising plugin WebSeed
Initialising plugin TorrentCreator
Initialising plugin MoveTorrent
Initialising plugin ExtraStats
Initialising plugin DesiredRatio
Initialising plugin NetworkGraph
Initialising plugin SimpleRSS
Initialising plugin Locations
Initialising plugin WebUi
Initialising plugin EventLogging
Initialising plugin SpeedLimiter
Initialising plugin NetworkHealth
Initialising plugin TorrentSearch
Initialising plugin Scheduler
Initialising plugin TorrentNotification
Initialising plugin TorrentPeers
Applying preferences
Starting DHT...
No DHT file to resume
Segmentation fault (core dumped)

I'm not sure what other information to give, so please let me know what else would help and I'll post it.

I think I'm going to try to get utorrent to work under wine, so I' just want to try to remove/clean up the deluge mess.  Thanks

---

### Post by SpiritIsReality on 2007-09-28
howdy
```
sudo apt-get -s remove --purge deluge
```
that would -s (simulate) the remove and --purge of the package deluge
could you see what that says.
if it doesn't complain or whatever, I don't know what to expect.
I tried it like so
 sudo apt-get -s remove --purge emacs21
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  emacs21-common emacsen-common emacs21-bin-common xaw3dg liblockfile1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  emacs21*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Purg emacs21 [21.4a+1-2ubuntu1.1]
fmat@p3:~$ whereis emacs21
emacs21: /usr/bin/emacs21 /etc/emacs21 /usr/X11R6/bin/emacs21 /usr/bin/X11/emacs21 /usr/share/emacs21
fmat@p3:~$ man apt-get

see what you think, or post the messages back here.

trails

---

### Post by SpiritIsReality on 2007-09-28
howdy
sudo apt-get install -f

might fix the dependencies
see in man apt-get, could try that, it won't hurt?

trails

---

### Post by berZirker on 2007-09-28
So neither copy is real apparently:

berzirker@Godzilla:~$ sudo apt-get -s remove --purge deluge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deluge
berzirker@Godzilla:~$ 

And the dependencies seem to be in order:

berzirker@Godzilla:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
berzirker@Godzilla:~$

---

### Post by SpiritIsReality on 2007-09-28
ok

if I knew bash scripting I could make this easier, but...this is as far as I know...


fmat@p3:~$ man find
Reformatting find(1), please wait...
fmat@p3:~$ sudo find / -name emacs21 (there's a space between / and -)
Password:
/etc/emacs21
/usr/bin/emacs21
/usr/share/emacs21
/usr/share/doc/emacs21
/usr/share/menu/emacs21
fred@p3:~$ echo "cd to files"
cd to files
fmat@p3:~$ echo "rm files or rm -r directories"
rm files or rm -r directories

and , or

fmat@p3:~$ man updatedb
Reformatting updatedb(1), please wait...
fmat@p3:~$ updatedb
updatedb: fatal error: You are not authorized to create a default slocate database!
fmat@p3:~$ sudo updatedb
Password:
fmat@p3:~$ locate emacs21

I just used emacs21 as an example again. I'm readin a beginner's book, and I wouldn't 
mind if it got beat up a bit by mistake. ha

check out the references to terminal commands in the important links thread on the absolute
biginner forum sticky. I hope to get around to it myself. there's a link here to what I think is a
gui find...
[https://help.ubuntu.com/7.04/user-guide/C/nautilus-searching.html](https://help.ubuntu.com/7.04/user-guide/C/nautilus-searching.html)
should probably start nautilus in root, Alt-F2, then run
gksu nautilus
then click up, then the search button?

I surely don't know the ins and outs of aptitude , dpkg. but in there might lie the short answer.
hopefully there's not many directories to have to wipe out.
I've seen in order to make apt work sometimes, they had to go into the ...just a minute I'll check...
/var/lib/dpkg/info and search for the trouble maker package, and either move it or remove it.

see what you find? or locate?

trails

---

### Post by berZirker on 2007-10-15
Well I've ended up having to reinstall ubuntu after a hd failure, so needless to say this problem went away.  Sorry if you were looking for help with a similar problem, I can't help you.

---

