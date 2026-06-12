---
title: "Installing programs"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by total_absolute_n00b on 2008-02-17
hi'a people i started running xfce a couple of weeks ago and all is good everything fine and dandy I'm running xubuntu Gutsy Gibbon. a normal 32 bit processor etc etc pretty standard i replaced the Abiword it came with open office and added a few other bits of software nothing major. but ne way i wanted to download a web so went to add and remove programs it said my list of available applications was out of date so refreshed them and it came up that
[VERB]
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[\VERB]

and when i went to click on a bit of software to download (pritty much anything

[VERB] Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[\VERB] 
and the same repositories were quoted

so anyway i read a forum about a guy with a similar problem allegedly it shouldn't have been looking for a /web thing in the repository 
[http://ubuntuforums.org/showthread.php?t=642862]("http://ubuntuforums.org/showthread.php?t=642862")

Ne way i tried what was quoted there as a solution un-ticking the CDrom as a source and changing the mirror but alas it had no effect and the same error now persists

Any help would be appreciated. sorry for bugging you guys do you need more info?:KS

---

### Post by erfahren on 2008-02-17
go to Applications > System > Software Sources - make sure all the boxes are checked except "Source Code" (you probably don't need that right now). It will prompt you to reload.

then try this - open up a terminal (Applications > Accessories > Terminal) and enter (just copy and paste it):
```

sudo apt-get install gedit

```
and see if it works (Gedit is just a text editor that is the default text-editor for Ubuntu - it is better than the default text editor in Xubuntu ("mousepad").

---

### Post by 1337455 10534 on 2008-02-17
Have you replaced the sources.list file?
Is your ethernet cord plugged in?
try this in your terminal;
```

ping http://www.google.com/

```
if you get nothing, then your internet connection is messed up. If you do get a good ping, try;
```

vi /etc/apt/sources.list

```
and paste it on this thread.

(and if you do install gedit, which is great, remove mousepad with "sudo apt-get remove mousepad")

---

### Post by erfahren on 2008-02-17
> **1337455 10534 said:**
> Have you replaced the sources.list file?
if you get nothing, then your internet connection is messed up. If you do get a good ping, try;
```

vi /etc/apt/sources.list

```
and paste it on this thread.

(and if you do install gedit, which is great, remove mousepad with "sudo apt-get remove mousepad")
why not just?
```

cat /etc/apt/sources.list

```
why uninstall mousepad?

---

### Post by 1337455 10534 on 2008-02-17
cat /etc/apt/sources.list and vi /etc/apt/sources.list would do the same thing. No really. The exact same thing.

I assume you use Xfce because its lighter. Then why would you let two text editors be on your system?

---

### Post by total_absolute_n00b on 2008-02-19
Thanks guy's i tried re-selected the cdrom as a source in the software sources (ticking all the sources except the source code one) i selected the UK server as apposed to a mirror ad .ox.ax.uk (i assume that doing this would mean it'll just select the fastest UK mirror) anyway it refreshes the software sources. and comes up that it can't download all the repository indexes 
(sorry don't know how to put code in those cool little boxes i assumed that  would distinguish it a little but it didn't so i've enclosed what the computer spews back at me in #################) 
ne way it comes up with this.

########################################

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

##############################################

this looks the same problem as before but it's having trouble with the cdrom too (i put the CD that i intalled gutsy gibson off in the drive while doing this. 

then did put the code in termal to refresh the software sourse. The terminal spewed this back out at me.

#################################################

geoff@geoff-laptop:~$ sudo apt-get install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gedit is already the newest version.
The following packages were automatically installed and are no longer required:
  libkbluetooth0 libqt4-core bluez-utils python-qt4 libqt4-gui python-qt4-dbus
  python-sip4 libbluetooth2 libdbus-qt-1-1c2 libopenobex1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
geoff@geoff-laptop:~$ 

###################################################

so i thought that was all good but then i tried to install
went to add/remove> it through it's "checking dependencies" etc. then told me "The list of available applications is out of date

To reload the list you need a working internet connection." 

so i clicked reload

it downloaded repositrys, (well it managed 35/40) it came up with this message.

#######################################################
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
######################################################

I clicked on bluefish to install (just as an example had a pretty picture) came up with blurb about installing community maintained software so clicked Enable

It went through downloading repository indexes and had no trouble with the first 35 but then couldn't do the rest and came up with 


#####################################################
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
######################################################


then it comes up with 

#############################
Bluefish Editor cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.
###############################


urm my computer isn't too bad it was running XP but it did run slowly it's a Intel celeron M laptop 218.1Mb Ram (ok kinda small...well very) and 2.4Ghz processor.

The internet comes through a wireless adapter and seems to be working fine i can surf the web and download stuff through Firefox and pidgin works fine. 
pinging Google comes out like this:

##########################
geoff@geoff-laptop:~$ ping [www.google.co.uk](www.google.co.uk)
PING [www.l.google.com](www.l.google.com) (66.249.93.104) 56(84) bytes of data.
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=1 ttl=246 time=37.9 ms
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=2 ttl=246 time=47.4 ms
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=3 ttl=246 time=29.6 ms
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=4 ttl=246 time=36.5 ms
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=5 ttl=246 time=42.4 ms
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=7 ttl=246 time=29.4 ms
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=8 ttl=246 time=30.9 ms
64 bytes from ug-in-f104.google.com (66.249.93.104): icmp_seq=9 ttl=246 time=42.2 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
9 packets transmitted, 8 received, 11% packet loss, time 8017ms
rtt min/avg/max/mdev = 29.485/37.105/47.491/6.282 ms
geoff@geoff-laptop:~$ 
###########################

it didn't work when i prefaced the www. with http:// but i don't think that means my internet is messed up.

Urm I'm baffled it look like gutsy (from things I've read on the internet, but i know nothing) that it seems to be looking in the wrong place for the last 3 repositories (it adds an extra sub folder '/web') but that doesn't seem to explain why it can't even update from the CD ugh i dunno...if you guy's have no idea do you think reinstalling linux would solve the problem. and if it comes to that would there be a better distribution but to be honest i really like gutcy coz it runs fast and does everything i want from it...except download programs...(it does let me install updates to itself, you know when it comes up saying there are important updates) anyway any suggestions would be greatly appreciated, Thanks a lot guys Geoff


:popcorn:

---

### Post by Crooksey on 2008-02-19
> **1337455 10534 said:**
> cat /etc/apt/sources.list and vi /etc/apt/sources.list would do the same thing. No really. The exact same thing.



I dont use cat to edit my files.

--

Try opening your sources.list, deleting it all, then replace with..

```

deb http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

DE servers work fine for UK users, now to update...

```

sudo apt-get update

```

Should do it.

---

### Post by total_absolute_n00b on 2008-02-19
hi soz to sound like a (be a total) n00b but how do i delete and replace the  sources.list, 
btw i changed to the German servers using the software sources app under applications> system. and still have the same stupid problem. bringing up the software source list i now get
########

geoff@geoff-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy main restricted web
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted web
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-security main restricted web
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) gutsy-security multiverse


###################################

which looks like what you told me to replace it with (just about to check it word for word but it's easier to do when both bits are next to each other on the forum (i'll post in 5 min  after i checked to see if there is a difference)

I really don't mind re-installing gutsy (as it'd sort out the prob (hopefully)) ans i wouldn't be bugging you guys
But thanks for your help so far. :)

---

### Post by timbounceback on 2008-02-19
don't reinstall yet; the problem is the random "web"s at the end of the entries. Instead, run the following (one command): ```
gksudo echo "deb http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse" > /etc/apt/sources.list
``` Then change it so it uses the repos for your locality.

---

### Post by Crooksey on 2008-02-19
```

gedit /etc/apt/sources.list
```

Or if gedit is not installed, use nano.

---

### Post by total_absolute_n00b on 2008-02-19
k yeah there not the same at all loads of differences...

---

### Post by timbounceback on 2008-02-19
report back once you have changed the repositories to match those posted

---

### Post by 1337455 10534 on 2008-02-19
Gedit will not let you modify your sources.list without root access, so try;
gksudo gedit /etc/apt/sources.list

and do whatever you need to.
A word on your computer type;
Bluefish probably didnt install because you don't have an x86 computer. Are you using a 64-bit or an high-end AMD computer? Dobt it but just checking.. it may be possible that you have 64-bit repos, though Ive never heard of that happening.

To do the cute code boxes, you need to put your info within two brackets, eg
"[ c o d e ] random stuff [/ c o d e]"
without the quotes or spaces.

---

### Post by total_absolute_n00b on 2008-02-21
Thank you so much guy's worked a treat :)

---

### Post by Attila2452 on 2008-03-08
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
Type  :quit<Enter>  to exit Vim

---

