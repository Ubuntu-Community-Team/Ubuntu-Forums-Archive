---
title: "Almost ready to walk away from Ubuntu :-("
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by KeyboardJockey on 2006-02-15
Help!

I've been trying since the 6th Feb to get Ubuntu to work properly and I'm almost ready to walk away in disgust.

I've never had to use a terminal window before.  

I can't install software  (well I managed to install aMule and XMMS but that is all)
I can't upgrade from Hoary to Breezy 
I can't remove software 
I can't get it to play mpg's and it won't print.

I get a constantly recurring libcurl2 error  and a terminal window that I cannot make sense of whatsoever.  

I don't want to have to go back to windows but I'm so so frustrated by this.

Below is a sample of the sort of stuff that has been coming back from the Terminal Window.....

I do hope someone can help me.   Its a total mess.  :( 


myrealname@ubuntu:~$ sudo apt-get remove mplayer-386 mplayer-fonts mozilla-mplayer
Password:
Sorry, try again.
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
Package mplayer-386 is not installed, so not removed
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  amule: Depends: libcurl2 (>= 7.11.2-1) but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
myrealname@ubuntu:~$


myrealname@ubuntu:~$  sudo apt-get remove mplayer-custom mplayer-fonts mozilla-mplayerReading Package Lists... Done
Building Dependency Tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  amule: Depends: libcurl2 (>= 7.11.2-1) but it is not going to be installed
  xmms-xmmplayer: Depends: mplayer
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
myrealname@ubuntu:~$


myrealname@ubuntu:~$ sudo apt-get remove vlc 
Reading Package Lists... Done
Building Dependency Tree... Done
Package vlc-plugin-arts is not installed, so not removed
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  amule: Depends: libcurl2 (>= 7.11.2-1) but it is not going to be installed
  gnome-vlc: Depends: vlc (= 0.7.2.final-3) but it is not going to be installed
  vlc-plugin-esd: Depends: vlc (= 0.7.2.final-3) but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
myrealname@ubuntu:~$


myrealname@ubuntu:~$ sudo apt-get remove vlc
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  amule: Depends: libcurl2 (>= 7.11.2-1) but it is not going to be installed
  gnome-vlc: Depends: vlc (= 0.7.2.final-3) but it is not going to be installed
  vlc-plugin-esd: Depends: vlc (= 0.7.2.final-3) but it is not going to be installed
  wxvlc: Depends: vlc (= 0.7.2.final-3) but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
myrealname@ubuntu:~$




myrealname@ubuntu:~$ sudo updatedb
myrealname@ubuntu:~$ locate libcurl3
/var/lib/dpkg/info/libcurl3.shlibs
/var/lib/dpkg/info/libcurl3.list
/var/lib/dpkg/info/libcurl3.postinst
/var/lib/dpkg/info/libcurl3.postrm
/var/lib/dpkg/info/libcurl3.md5sums
/usr/share/doc/libcurl3
/usr/share/doc/libcurl3/BINDINGS
/usr/share/doc/libcurl3/README
/usr/share/doc/libcurl3/FEATURES
/usr/share/doc/libcurl3/BUGS
/usr/share/doc/libcurl3/changelog.gz
/usr/share/doc/libcurl3/KNOWN_BUGS
/usr/share/doc/libcurl3/THANKS
/usr/share/doc/libcurl3/VERSIONS
/usr/share/doc/libcurl3/copyright
/usr/share/doc/libcurl3/FAQ.gz
/usr/share/doc/libcurl3/TODO.gz
/usr/share/doc/libcurl3/changelog.Debian.gz
myrealname@ubuntu:~$
myrealname@ubuntu:~$





E: /var/cache/apt/archives/libcurl2_7.12.0.is.7.11.2-1_i386.deb:  trying to overwrite `/usr/share/curl/curl-ca-bundle.crt', which is also in package libcurl3








myrealname@ubuntu:~$ sudo apt-get -libcurl2
E: Command line option ‘l’ [from -libcurl2] is not known.
myrealname@ubuntu:~$ sudo apt-get remove libcurl2
Reading Package Lists... Done
Building Dependency Tree... Done
Package libcurl2 is not installed, so not removed
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies:
  amule: Depends: libcurl2 (>= 7.11.2-1) but it is not going to be installed
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a solution).
myrealname@ubuntu:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
myrealname@ubuntu:~$ sudo apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libcurl2
Suggested packages:
  libcurl2-gssapi ca-certificates
The following NEW packages will be installed:
  libcurl2
0 upgraded, 1 newly installed, 0 to remove and 360 not upgraded.
39 not fully installed or removed.
Need to get 0B/223kB of archives.
After unpacking 549kB of additional disk space will be used.
Do you want to continue? [Y/n] y

Preconfiguring packages ...
(Reading database ... 59291 files and directories currently installed.)
Unpacking libcurl2 (from .../libcurl2_7.12.0.is.7.11.2-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libcurl2_7.12.0.is.7.11.2-1_i386.deb (--unpack):
 trying to overwrite `/usr/share/curl/curl-ca-bundle.crt', which is also in package libcurl3
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libcurl2_7.12.0.is.7.11.2-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
myrealname@ubuntu:~$

---

### Post by chimera on 2006-02-15
Welcome to dependency hell, enjoy your stay.

To get out, I'd reccomend you reinstall ubuntu and don't mess with repositories and remove semi-random packages until you know what you're doing.

---

### Post by Vengeful Cynic on 2006-02-15
This is the part where you take three deep breaths.  Got it?  Good.

Now, it looks like you tried to install Breezy and then upgrade from Breezy to Hoary.  Is that right?

Is there any particular reason that you can't just wipe what you've got and try running a clean install of Hoary?

What kind of hardware are we looking at, there may be something that someone can help with?

Last and not least, try to relax, man (or woman, as the case may be.)  We want to help... it looks like you've had a frustrating week of trying to go this on your own.  Keep coming back to the forums and talk this over with us and we'll be more than happy to work you through getting your Ubuntu up and running smoothly... you just have to have a little patience and be willing to sit back, calm down, and try to let us help you learn this.

-Vengeful Cynic

---

### Post by mednamot on 2006-02-15
first off, it appears you're trying to remove things that aren't there...

if you're trying to install them, don't use the "remove" portion of the apt-get direction.

secondly, you could just use synaptec.

Thirdly, if you are able to get Breezy loaded, then you could just use automatix to get some of your stuff

---

### Post by rfruth on 2006-02-15
Don't give up keyboard !  I don't have all the answers but try to tackle one problem at a time, as for installing software does Synaptic run ?  Was Hoary ok and now Breezy is giving you fits ?  What program are you trying to play mpg's (mp3 ?) with, what kind of printer and is it listed in System > Printers  :confused:

---

### Post by KeyboardJockey on 2006-02-15
[QUOTE=chimera]Welcome to dependency hell, enjoy your stay.

To get out, I'd reccomend you reinstall ubuntu and don't mess with repositories and remove semi-random packages until you know what you're doing.[/QUOTE]

Upgrade to Breezy 

Doesn't work  :-(


I did the following 

sudo apt-get update (hit enter and got a list of stuff and then rebooted computer with TW open)  No update.

---

### Post by bluevoodoo1 on 2006-02-15
[QUOTE=KeyboardJockey]I did the following 

sudo apt-get update (hit enter and got a list of stuff and then rebooted computer with TW open)  No update.[/QUOTE]

You know, that won't upgrade you to Breezy, that will only refresh any updates made to your /etc/apt/sources.list

---

### Post by KeyboardJockey on 2006-02-15
[QUOTE=Vengeful Cynic]This is the part where you take three deep breaths.  Got it?  Good.

Now, it looks like you tried to install Breezy and then upgrade from Breezy to Hoary.  Is that right?[/QUOTE]


I started on Hoary, had problems and then friend told me to upgrade to Breezy went through the upgrade instructions but zilch result.
[QUOTE=Vengeful Cynic]
Is there any particular reason that you can't just wipe what you've got and try running a clean install of Hoary?[/QUOTE]

Part ofthe problem is that I don't wantto lose the aMule prog that I've managed to get running and I've got data on there which won't fit on a CDROM.



[QUOTE=Vengeful Cynic]
What kind of hardware are we looking at, there may be something that someone can help with?[/QUOTE]


CPU: Advanced Micro Devices Duron Spitfire 804.8 MHz (Family: 6, Stepping: 1)
Detected cache-line size is 64 bytes
3DNow supported but disabled
3DNowExt supported but disabled
CPUflags: MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 0 SSE2: 0
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

[QUOTE=Vengeful Cynic]

Last and not least, try to relax, man (or woman, as the case may be.)  We want to help... it looks like you've had a frustrating week of trying to go this on your own.  Keep coming back to the forums and talk this over with us and we'll be more than happy to work you through getting your Ubuntu up and running smoothly... you just have to have a little patience and be willing to sit back, calm down, and try to let us help you learn this.

-Vengeful Cynic[/QUOTE]

Many thanks - I really don't want to have to go back to Windoze.

---

### Post by KeyboardJockey on 2006-02-15
[QUOTE=bluevoodoo1]You know, that won't upgrade you to Breezy, that will only refresh any updates made to your /etc/apt/sources.list[/QUOTE]

Aha! so what DO I do when I get the TW full of the upgrade data?  I tried hitting Enter and all I got was the 

myrealname@ubuntu:~$ 

come up.

---

### Post by arctic on 2006-02-15
If you want to upgrade from one release to the next, boot up the system, change your repositories in synaptic from e.g. hoary to breezy, now log out and log into the secure shell mode (don't login into Gnome again). Now run:

sudo apt-get clean all
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by aysiu on 2006-02-15
Something's wrong with your sources.list.
Can you post the output of this command? ```
cat /etc/apt/sources.list
```

---

### Post by lemmy999 on 2006-02-15
1. Install Breezy
2. Read the howto for Automatix/EasyUbuntu and install the programs you want.
3. Enjoy!

Hope this helps- all i can say is take your time and do things a step at a time. If you hit a problem with anything post the output here. This forum is probably the best thing about Ubuntu!! ( apart from the OS itself)

---

### Post by Protostar on 2006-02-15
Instead of trying to upgrade to Breezy, why not go boot to Windows and download the Breezy .iso, burn it, and install Breezy that way (I'm assuming you still have a dual boot system)?

---

### Post by KeyboardJockey on 2006-02-15
[QUOTE=mednamot]first off, it appears you're trying to remove things that aren't there...

if you're trying to install them, don't use the "remove" portion of the apt-get direction.

secondly, you could just use synaptec.

Thirdly, if you are able to get Breezy loaded, then you could just use automatix to get some of your stuff[/QUOTE]


The problem is I follow this circular pattern:

I select the progs in Synaptic, I hit apply then I get a error window.  I close the error window and close Synaptic and get a message saying 'If you close SPM changes will not be applied'  so I go to the Ubuntu help sites cut and paste some code into TW which falls over.

I've been following the same pattern and getting the same result.

---

### Post by Protostar on 2006-02-15
[QUOTE=lemmy999]1. Install Breezy
2. Read the howto for Automatix/EasyUbuntu and install the programs you want.
3. Enjoy!

Hope this helps- all i can say is take your time and do things a step at a time. If you hit a problem with anything post the output here. This forum is probably the best thing about Ubuntu!! ( apart from the OS itself)[/QUOTE]


I don't know about Automatix. Everytime I've used that I've always had to do a reinstall. I recommend doing it the manual way, as it doesn't break anything and plus you learn more about the OS in the process. Just my2cents.

---

### Post by aysiu on 2006-02-15
[QUOTE=KeyboardJockey]The problem is I follow this circular pattern:

I select the progs in Synaptic, I hit apply then I get a error window.  I close the error window and close Synaptic and get a message saying 'If you close SPM changes will not be applied'  so I go to the Ubuntu help sites cut and paste some code into TW which falls over.

I've been following the same pattern and getting the same result.[/QUOTE] I repeat: something is wrong with your sources.list. Please post the output of this command: ```
cat /etc/apt/sources.list
```

---

### Post by aysiu on 2006-02-15
[QUOTE=Protostar]I don't know about Automatix. Everytime I've used that I've always had to do a reinstall. I recommend doing it the manual way, as it doesn't break anything and plus you learn more about the OS in the process. Just my2cents.[/QUOTE] According to [this poll](http://www.ubuntuforums.org/showthread.php?t=123569) 115 out of 139 Automatix users had no problems with Automatix whatsoever. It means most of the time, it works just fine. It also means sometimes... it doesn't.

---

### Post by bluevoodoo1 on 2006-02-15
[QUOTE=Protostar]I recommend doing it the manual way, as it doesn't break anything and plus you learn more about the OS in the process. Just my2cents.[/QUOTE]

Agreed.

---

### Post by KeyboardJockey on 2006-02-15
[QUOTE=Protostar]Instead of trying to upgrade to Breezy, why not go boot to Windows and download the Breezy .iso, burn it, and install Breezy that way (I'm assuming you still have a dual boot system)?[/QUOTE]

I don't feel that I really want to go in to Win XP as I've got a perm online connection and it is a barebones installation with no FW or AV installed on the XP partition.

---

### Post by KeyboardJockey on 2006-02-15
[QUOTE=aysiu]I repeat: something is wrong with your sources.list. Please post the output of this command: ```
cat /etc/apt/sources.list
```[/QUOTE]

OK I've done this and this is what I get.  


myrealname@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
myrealname@ubuntu:~$

---

### Post by arctic on 2006-02-15
If you read it carefully, you will notice that you have BOTH some warty and some hoary repos enabled. uncomment the warty repos, activate the hoary repos and change the name "hoary" to "breezy". Then run apt-get as I told before.

---

### Post by aysiu on 2006-02-15
Yeah, that sources.list is your problem.
You have duplicate repositories and a mix of Hoary and Warty repositories.

See the first link of my signature and **follow the instructions _exactly_ as written**. Pick Hoary if you want Hoary and Breezy if you want Breezy. Then after you finish, type ```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by KeyboardJockey on 2006-02-15
[QUOTE=arctic]If you read it carefully, you will notice that you have BOTH some warty and some hoary repos enabled. uncomment the warty repos, activate the hoary repos and change the name "hoary" to "breezy". Then run apt-get as I told before.[/QUOTE]


'scuse the idiot comment but what does 'uncomment' mean?

---

### Post by bonzodog on 2006-02-15
eep..that sources.list is seriously screwed. 
first enter this into a terminal:
```
$sudo gedit /etc/apt/sources.list
```

You should now have the list open in a text editor. If i was you I would delete all text in the file and replace it with these six lines exactly as written:

```

deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe mulitiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-update main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

```

Then, save the file. When you have done this, still in the terminal, enter:
```
 
$sudo apt-get clean
$sudo apt-get update
$sudo apt-get dist-upgrade

```
It will tell you it's reading the currently installed list and then tell you it has to install ALOT of files, well over 100MB, and also remove alot of stuff. answer 'Y' to this question. The system will then commence the upgrade process, and I would go make a cup of tea or coffee...it will probably take a couple of hours depending on how big your internet link is.
Any further probs, ask here.

---

### Post by KeyboardJockey on 2006-02-15
[QUOTE=bonzodog]eep..that sources.list is seriously screwed. 
first enter this into a terminal:
```
$sudo gedit /etc/apt/sources.list
```

You should now have the list open in a text editor. If i was you I would delete all text in the file and replace it with these six lines exactly as written:

```

deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe mulitiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-update main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

```

Then, save the file. When you have done this, still in the terminal, enter:
```
 
$sudo apt-get clean
$sudo apt-get update
$sudo apt-get dist-upgrade

```
It will tell you it's reading the currently installed list and then tell you it has to install ALOT of files, well over 100MB, and also remove alot of stuff. answer 'Y' to this question. The system will then commence the upgrade process, and I would go make a cup of tea or coffee...it will probably take a couple of hours depending on how big your internet link is.
Any further probs, ask here.[/QUOTE]


I get a window called *sources.list  I pasted the stuff into the window and selected Save and got a error message saying 'Cannot Save /etc/atp/spurces.list

---

### Post by Protostar on 2006-02-15
Did you type sudo before gedit? Editing the sources list requires administrative (read: root) access.

---

### Post by bonzodog on 2006-02-15
you did put that first command EXACTLY as I pasted it? with the sudo first? it should ask for your password, then present you with the old, screwed up list in a text editor.
delete all the old stuff, and paste in the six lines I put up for you there. there is a button at the top of gedit with 'save' written on it. click this and it should just save the file.

---

### Post by KeyboardJockey on 2006-02-15
[QUOTE=bonzodog]you did put that first command EXACTLY as I pasted it? with the sudo first? it should ask for your password, then present you with the old, screwed up list in a text editor.
delete all the old stuff, and paste in the six lines I put up for you there. there is a button at the top of gedit with 'save' written on it. click this and it should just save the file.[/QUOTE]

Right I managed to get the filled window as pointed out - I've pasted over the new text and managed to save it

Do I close the window before entering he text into the text editor as I tried to do it withthe window opened and nothing seemed to happen?

---

### Post by Protostar on 2006-02-15
[QUOTE=KeyboardJockey]Right I managed to get the filled window as pointed out - I've pasted over the new text and managed to save it

Do I close the window before entering he text into the text editor as I tried to do it withthe window opened and nothing seemed to happen?[/QUOTE]

If by the window you mean the terminal window, no. If you close the terminal window you will also close gedit as you are running gedit from the terminal. Issue the command, copy and paste into gedit, and save the new source list.

---

### Post by KeyboardJockey on 2006-02-15
The recommended procedure 

Gives me..........


marc@ubuntu:~$ sudo apt-get clean
marc@ubuntu:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release [26.2kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release [16.8kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release [16.8kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages [490kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages [84.2kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages [3809B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources [20.0kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources [840B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages [57.0kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources [8315B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages [4374B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources [175kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources [1320B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages [2169kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources [857kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages [88.4kB]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources [48.4kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages [18.6kB]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages [14B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Sources [5489B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Sources [14B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/main Packages [11.6kB]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/restricted Packages [14B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/universe Packages [26.3kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse Packages [1549B]
Fetched 4148kB in 38s (108kB/s)
Reading Package Lists... Done
marc@ubuntu:~$ sudo apt-get dist-upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies:
  amule: Depends: libcurl2 (>= 7.11.2-1) but it is not installed
E: Unmet dependencies. Try using -f.
marc@ubuntu:~$

---

### Post by bonzodog on 2006-02-15
You need to alter the list to read breezy not hoary
You've not done something right. 
when you put in that first command in the terminal, it should open anew window called the gedit text editor with the old sources.list file. transfer my six new lines into that, and erase all the old stuff, and click save, then close the text editor. THEN issue those commands in the terminal.

---

### Post by aysiu on 2006-02-15
Or just see the first link of my signature.

---

### Post by arctic on 2006-02-15
[QUOTE=KeyboardJockey]'scuse the idiot comment but what does 'uncomment' mean?[/QUOTE]
Uncommenting is: removing the "#" at the beginning of a line in the configuration files of your system. Commenting is adding the "#". ;)

PS: I should explain a bit more, I guess. If you uncomment lines in a confi-file, the system will not "read" those lines that begin with "#" or "##" or "###". It will skip them. If you remove the "#", the line of the config-file will be readable by the system again. That way, you can play around with different options without the need to delete the entrys and rewrite them later. It saves you lots of time.

---

### Post by deBaas on 2006-02-15
[QUOTE=bonzodog]eep..that sources.list is seriously screwed. 
first enter this into a terminal:
[/quote]
```
sudo apt-get install ubuntu-desktop
```
then:
> 
```
$sudo gedit /etc/apt/sources.list
```

You should now have the list open in a text editor. If i was you I would delete all text in the file and replace it with these six lines exactly as written:

```

deb http://archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted universe mulitiverse
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-update main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse

```

Then, save the file. When you have done this, still in the terminal, enter:
```
 
$sudo apt-get clean
$sudo apt-get update
$sudo apt-get dist-upgrade

```
It will tell you it's reading the currently installed list and then tell you it has to install ALOT of files, well over 100MB, and also remove alot of stuff. answer 'Y' to this question. The system will then commence the upgrade process, and I would go make a cup of tea or coffee...it will probably take a couple of hours depending on how big your internet link is.
Any further probs, ask here.
Follow this and it should give you a fresh, good breezy install.

---

### Post by Edward The Bonobo on 2006-02-16
As an observation:

There does seem to be a crying need for a 'Basic Guide to Ubuntu Concepts'.  Who would ever guess, for example, that there is something called Synaptic that will download software from a bunch of places and make sure that you have all the components that you need to make it work?  Even something like a 'Basic Features' list, with some plain English description would help.

Maybe I'll get around to it when my life is a shade less busy.

But I will *refuse* to call it an Idiot's Guide or Ubuntu for Dummies.  People who are making the effort to educate themselves are not dumb idiots.

---

### Post by BoyOfDestiny on 2006-02-16
[QUOTE=Edward The Bonobo]As an observation:

There does seem to be a crying need for a 'Basic Guide to Ubuntu Concepts'.  Who would ever guess, for example, that there is something called Synaptic that will download software from a bunch of places and make sure that you have all the components that you need to make it work?  Even something like a 'Basic Features' list, with some plain English description would help.

Maybe I'll get around to it when my life is a shade less busy.

But I will *refuse* to call it an Idiot's Guide or Ubuntu for Dummies.  People who are making the effort to educate themselves are not dumb idiots.[/QUOTE]

Does anyone remember how synaptic was before (I think in warty it was like this), where you could get the sources list in a window, and merely uncheck a box to "uncomment"...

Forgive me if there is a gui way to still do it, but I just edit the sources.list... I can't figure out why universe is not enabled by default... Is it for security? I don't think it's just keep non-free stuff out... Since restricted is enabled by default... I can understand multiverse not being listed (although backports has it, commented... but still there)

I think there should be an easy way to enable the repos and update to the next release (I believe the update thing is in the works). I personally love using terminal (I seem to learn something new everytime I use it), but it just seems some of the gui tools are still inadequate.

---

### Post by Madpilot on 2006-02-16
[QUOTE=Edward The Bonobo]As an observation:

There does seem to be a crying need for a 'Basic Guide to Ubuntu Concepts'.[/QUOTE]

Here you go:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

This is the Breezy version, the one that will come out with Dapper in April is considerably improved.

The current Dapper version is at [http://doc.ubuntu.com/ubuntu/desktopguide/C/index.html](http://doc.ubuntu.com/ubuntu/desktopguide/C/index.html) but please note the big DRAFT notices on it!

If you want to help improve Ubuntu's docs further, please volunteer! [Ubuntu DocumentationTeam]("https://wiki.ubuntu.com/DocumentationTeam") is our main page; here's our [contact page]("https://wiki.ubuntu.com/DocumentationTeam/Contact"). We do most of our communication through our mailing list, and #ubuntu-doc on Freenode IRC.

---

### Post by nocturn on 2006-02-16
[QUOTE=aysiu]According to [this poll](http://www.ubuntuforums.org/showthread.php?t=123569) 115 out of 139 Automatix users had no problems with Automatix whatsoever. It means most of the time, it works just fine. It also means sometimes... it doesn't.[/QUOTE]

That's still a 17.3% failure rate.

---

### Post by KeyboardJockey on 2006-02-16
OK I'm going to try a different tack.

I'm going to assume that my 5.04 Hoary Hedgehog install is irrepairablly (for me at least) corrupted.

I've taken a risk and gone back into Windoze and downloaded Breezy Badger 5.10.

How do I get it to overwrite the HH 5.04 installation tht I've got at the moment?

I've got the BB 5.10 on a CD at the moment and it is sitting inthe burner drive (I've got two drives one CD Reader and one CD writer)  I tried rebooting and selecting burner drive as the first boot device but it automatically opens HH 5.04.

I spoke to a friend who is a linux bod last night and he said that 5.10 would probably be the way to sort the problem out.

I didn't pay enough attention when he installed HH 5.04 :(  (yes I know I should have done :D )

---

### Post by Clark Nova on 2006-02-16
All you'll need to do is reboot your computer with the Breezy CD in the drive and boot from that. It will overwrite your Hoary installation completely and leave you with a nice fresh installation of Ubuntu. \\:D/

---

### Post by KeyboardJockey on 2006-02-16
Whooo hoo! :)    Things appear to be happening.

Breezy seems to be installing in the Terminal Window.  I went over and over the procedures where I went wrong yesterday and it seems to be updating from Hoary to Breezy.  What do I do when if finishes scrolling out and loading inthe Terminal Window.

Doesn't look like I need to use the CD after all.


When it finishes coming down do I close the terminal window and reboot?

---

### Post by Estariel on 2006-02-16
[QUOTE=KeyboardJockey]Whooo hoo! :)    Things appear to be happening.

Breezy seems to be installing in the Terminal Window.  I went over and over the procedures where I went wrong yesterday and it seems to be updating from Hoary to Breezy.  What do I do when if finishes scrolling out and loading inthe Terminal Window.

Doesn't look like I need to use the CD after all.


When it finishes coming down do I close the terminal window and reboot?[/QUOTE]

yes, but only when it has really finished (i.e. when it says "Done").

---

### Post by KeyboardJockey on 2006-02-16
[QUOTE=Estariel]yes, but only when it has really finished (i.e. when it says "Done").[/QUOTE]

Thank you that has been bothering me a lot what to do when if finally downloads.

I must say this is one of the most helpful computer forums I have ever come across.

And I'm determined NOT to have to go back to Windoze. :)

---

### Post by Estariel on 2006-02-16
[QUOTE=KeyboardJockey]Thank you that has been bothering me a lot what to do when if finally downloads.

I must say this is one of the most helpful computer forums I have ever come across.

And I'm determined NOT to have to go back to Windoze. :)[/QUOTE]

Oh, by the way, when booting you might be presented with some more boot options (since breezy installs a newer linux kernel.) Make sure, you pick the newest kernel (i.e. the one with the highest version number).

You can uninstall all other kernels later.

---

### Post by KeyboardJockey on 2006-02-16
[QUOTE=Estariel]Oh, by the way, when booting you might be presented with some more boot options (since breezy installs a newer linux kernel.) Make sure, you pick the newest kernel (i.e. the one with the highest version number).

You can uninstall all other kernels later.[/QUOTE]


Thats good to know.  So I need to look for 5.10 in the boot version list?  Is that correct?

Thanks.

---

### Post by Gustav on 2006-02-16
No, I don't think it will say what ubuntu version to load, just what linux kernel. It's usually the one on top. 

But it's not that critical you'll probably not notice any difference if you chose some older kernel.

---

### Post by Edward The Bonobo on 2006-02-16
> **Madpilot]Here you go:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

This is the Breezy version, the one that will come out with Dapper in April is considerably improved.

The current Dapper version is at [http://doc.ubuntu.com/ubuntu/desktopguide/C/index.html](http://doc.ubuntu.com/ubuntu/desktopguide/C/index.html) but please note the big DRAFT notices on it!

If you want to help improve Ubuntu's docs further, please volunteer! [Ubuntu DocumentationTeam]("https://wiki.ubuntu.com/DocumentationTeam") is our main page said:**
> contact page[/URL]. We do most of our communication through our mailing list, and #ubuntu-doc on Freenode IRC.

(In response to my idea of a 'Basic Concepts' guide)

That sort of stuff is all very good...but I have in mind something even more basic.  Maybe a couple of A4 pages in length, maximum - introducing some basic concepts to the newbie and linking to the excellent help pages already there.  'Ubuntu for the Bewildered' - how to make the transition from other OS's where people will have learnt entirely different concepts.

Yes I *will * volunteer - eventually.  When my life allows me.  Meantime...suggestions for what people need to know?
[LIST]
[*]There's these things called Desktops.  Usually you'll get Gnome of KDE - but if they make your machine go too slow, there's something called xcfe
[*]There's this thing called Synaptic which downloads software for you and makes sure all the little bits and pieces it needs are included.
[*]There's lots of help around on the wiki, in the forums...it might take you a while to understand some of the answers you get...but don't panic.
[*]Very often, you'll be directed to type strange looking stuff in a thing called a 'Terminal'.  Don't worry - you'll get used to it
[*]....any other ideas?
[/LIST]

---

### Post by KeyboardJockey on 2006-02-16
It didn't upgrade :( 

If fell over on something called 'locales' and I rebooted as it certainly looked like it had frozen.  The non functioning Mplayer is still in the Apps menu, it still won't play mpgs, And I got this when I tried to download VLC using apt-get after rebooting.

marc@ubuntu:~$ sudo apt-get vlc
Password:
E: Invalid operation vlc
marc@ubuntu:~$ sudo apt-get install vlc
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
marc@ubuntu:~$ sudo dpkg --configure -a
Setting up dash (0.5.2-5) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Setting up libfreetype6 (2.1.7-2.4ubuntu1) ...

Setting up libxml2 (2.6.21-0ubuntu1) ...

Setting up cpp-4.0 (4.0.1-4ubuntu9) ...
Setting up lsb-release (1.4-8ubuntu3) ...
Installing new version of config file /etc/lsb-release ...
dpkg: dependency problems prevent configuration of dpkg-dev:
 dpkg-dev depends on dpkg (>= 1.13.1); however:
  Version of dpkg on system is 1.10.26ubuntu1.
dpkg: error processing dpkg-dev (--configure):
 dependency problems - leaving unconfigured
Setting up libmagic1 (4.12-1ubuntu1) ...

Setting up libaspell15 (0.60.3-5) ...

Setting up file (4.12-1ubuntu1) ...
Setting up html2text (1.3.2a-2build1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Setting up libtext-iconv-perl (1.4-1) ...
Setting up libexpat1 (1.95.8-3) ...

Setting up libperl5.8 (5.8.7-5ubuntu1.2) ...

Setting up libaudiofile0 (0.2.6-6) ...

Setting up libdb4.2 (4.2.52-19ubuntu4) ...
Setting up net-tools (1.60-15ubuntu2) ...
Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on ubuntu-minimal; however:
  Package ubuntu-minimal is not installed.
 ubuntu-base depends on ubuntu-standard; however:
  Package ubuntu-standard is not installed.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
Setting up libgcj-common (4.0.1-4ubuntu9) ...
Setting up cpp (4.0.1-3) ...
Setting up libncursesw5 (5.4-9ubuntu4) ...

Setting up liblocale-gettext-perl (1.05-1) ...
Setting up iputils-ping (20020927-2ubuntu1) ...
Setting up libc6-i686 (2.3.5-1ubuntu12) ...

Setting up cpio (2.5-1.2ubuntu1.1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Setting up xrgb (0.99.0-5) ...
Setting up binutils (2.16.1-2ubuntu6) ...

Setting up libglib2.0-0 (2.8.3-0ubuntu1) ...

Setting up libtext-charwidth-perl (0.04-2) ...
Setting up libwrap0 (7.6.dbs-8) ...

Setting up libtext-wrapi18n-perl (0.06-2) ...
Setting up libc6-dev (2.3.5-1ubuntu12) ...
Setting up libglib2.0-data (2.8.3-0ubuntu1) ...
Setting up libidl0 (0.8.6-0ubuntu1) ...

Setting up initrd-tools (0.1.78ubuntu2) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Setting up libgcj6 (4.0.1-4ubuntu9) ...

Setting up liborbit2 (2.12.4-0ubuntu1) ...

Setting up libatk1.0-0 (1.10.3-0ubuntu2) ...

Setting up perl-modules (5.8.7-5ubuntu1.2) ...
Setting up libbonobo2-common (2.10.1-0ubuntu1) ...
Setting up libbonobo2-0 (2.10.1-0ubuntu1) ...

Setting up debconf-i18n (1.4.56ubuntu2) ...
Setting up perl (5.8.7-5ubuntu1.2) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Setting up debconf (1.4.56ubuntu2) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Setting up libssl0.9.7 (0.9.7g-1ubuntu1.1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Setting up ifupdown (0.6.7ubuntu1) ...
Installing new version of config file /etc/init.d/ifupdown ...
Installing new version of config file /etc/init.d/ifupdown-clean ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

Setting up adduser (3.64ubuntu1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Setting up locales (2.3.5-1ubuntu12) ...
Installing new version of config file /etc/locale.alias ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_GB:en_US:en_GB:en",
        LC_ALL = (unset),
        LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.

Setting up debconf-utils (1.4.56ubuntu2) ...

Setting up dictionaries-common (0.49.2ubuntu1) ...
Updating OpenOffice.org's dictionary list... done.
Removing obsolete /var/cache/dictionaries-common/emacsen-aspell-equivs.el

Setting up libsasl2-modules (2.1.19-1.5ubuntu4) ...
Setting up libsasl2 (2.1.19-1.5ubuntu4) ...

Setting up aspell (0.60.3-5) ...

Setting up tcpd (7.6.dbs-8) ...

Setting up netbase (4.21ubuntu3) ...
Installing new version of config file /etc/rpc ...
Installing new version of config file /etc/services ...
Installing new version of config file /etc/init.d/networking ...

Errors were encountered while processing:
 dpkg-dev
 ubuntu-base
marc@ubuntu:~$




What do I do now??

---

### Post by KeyboardJockey on 2006-02-16
Ubuntu will not load at all now.  Having to come on here via MS XP.

I've even lost the GUI.

How do I install and boot from the CD?  The update didn't work.

---

### Post by arctic on 2006-02-16
Oooh, this is ugly...

If you have an old ubuntu install CD at hand (if it's 5.10, even better), set your computer-bios to boot from the cd first, before it selects the harddisk. Save and exit, pop in your ubuntu-CD, follow the install instructions and when you get to the partitioning stage, do manual partitioning if you want to save the data on /home. Once everything is finished, simply reboot and you are done.

---

### Post by Connollyir on 2006-02-16
[QUOTE=arctic]Oooh, this is ugly...

If you have an old ubuntu install CD at hand (if it's 5.10, even better), set your computer-bios to boot from the cd first, before it selects the harddisk. Save and exit, pop in your ubuntu-CD, follow the install instructions and when you get to the partitioning stage, do manual partitioning if you want to save the data on /home. Once everything is finished, simply reboot and you are done.[/QUOTE]

In my opinion I think you should go with a fresh install like artic said, but I would just choose automatic partitioning instead of manual partitioning to make things easier (I'm assuming you didn't get very far with Ubuntu this time around and you wont have a whole lot on your hard disk worth saving). Also be careful you don't tell the partitioner to take out your Windows disk unless you want to... that could be bad if Windows is your only working OS. 

Some things are not going to work right out of the box, mpeg files and most media content for example will not work because they fall under "restricted content" in the Ubuntu playbook. Don't worry though - there are ways to make them work and the wikis and howtos are generally painless once you get used to them. 

For right now you should concentrate on getting a stable install under you (I recommend Breezy 5.10) and then focus on the rest of what you want to do on a one-on-one basis.

We are here if you need us.

-Ian

---

### Post by KeyboardJockey on 2006-02-16
YES!!

I managed to install Breezy Badger.

Still a few glitches.  amule is working.  VLC is playing mp3 and mpg but no mpg sound, no DVD and no live radio feed from the BBC from the BBC URL [www.bbc.co.uk/radio4/archers](www.bbc.co.uk/radio4/archers).  I'm sure there is a simple set up procedure for this.

Thank you all so much for helping me get Breezy started. :)

---

### Post by KeyboardJockey on 2006-02-16
I'm really really pleased I stuck with this.

---

### Post by Lord Illidan on 2006-02-16
[quote=KeyboardJockey]YES!!

I managed to install Breezy Badger.

Still a few glitches.  amule is working.  VLC is playing mp3 and mpg but no mpg sound, no DVD and no live radio feed from the BBC from the BBC URL [www.bbc.co.uk/radio4/archers]("http://www.bbc.co.uk/radio4/archers").  I'm sure there is a simple set up procedure for this.

Thank you all so much for helping me get Breezy started. :)[/quote]

Congrats! Regarding DVD, perhaps you need to install libdvdcss2?

---

### Post by Coelocanth on 2006-02-16
Hooray for Keyboardjockey! I was quite frustrated only a day or so ago just as you were, but I got some excellent advice and help here and now I'm really loving it too. Glad to see it's worked out for you.

---

### Post by KeyboardJockey on 2006-02-16
[QUOTE=Lord Illidan]Congrats! Regarding DVD, perhaps you need to install libdvdcss2?[/QUOTE]

So if I go to the Terminal Window and enter:

sudo apt-get libdvdcss2  and wait till it says DONE it should solve my problem??

---

### Post by Lord Illidan on 2006-02-16
I should have explained better, forgive me:

Have a look at this site : [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Jason_25 on 2006-02-16
[This]("https://wiki.ubuntu.com/RestrictedFormats") page should be useful to you.  Try this to get libdvdcss2. ```

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```

---

### Post by KeyboardJockey on 2006-02-16
[QUOTE=Jason_25][This]("https://wiki.ubuntu.com/RestrictedFormats") page should be useful to you.  Try this to get libdvdcss2. ```

sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```[/QUOTE]


Apparantly sudo apt-get install libdvdred3 is already there.

---

### Post by chaumurky on 2006-02-16
Search in this forum for Automatix. All you need is there from hereon. Just download the deb (as shown in the bottom of the first thread) and install it with **sudo dpkg -i <foo>.deb** (replcace <foo> with the name of the file you downloaded). Then run Automatix, tick the boxes of stuff you need and off you go. Windows was never so simple...

---

### Post by handy on 2006-02-17
[QUOTE=Protostar]I don't know about Automatix. Everytime I've used that I've always had to do a reinstall. I recommend doing it the manual way, as it doesn't break anything and plus you learn more about the OS in the process. Just my2cents.[/QUOTE]

It's just that sometimes, the last thing you need is more arcane steps when you are new to an OS.  You just need to get past whatever the problems are & onto a plateau where you can take a breather & get ready for the next steep bit.

Now we got 4 cents! :KS

---

### Post by LxP on 2006-02-19
There's some slight terminology confusion in this thread as far as un/commenting goes, so for the benefit of those not familiar with the concept:

> **arctic]Uncommenting is: removing the "#" at the beginning of a line in the configuration files of your system. Commenting is adding the "#".  said:**
> 
This is correct.

[QUOTE=arctic]PS: I should explain a bit more, I guess. If you uncomment lines in a confi-file, the system will not "read" those lines that begin with "#" or "##" or "###". It will skip them. If you remove the "#", the line of the config-file will be readable by the system again. That way, you can play around with different options without the need to delete the entrys and rewrite them later. It saves you lots of time.
The paragraph above should probably be reworded.

*Uncommented* lines are those that do *not* begin with a # symbol; those lines that do begin with a # have been *commented out*.

If you uncomment lines in a configuration file, the system *will* process those lines. If you comment them out, the system will skip over them and *not* process them.

---

### Post by arctic on 2006-02-19
English is not my native language. Sorry. :D

---

### Post by LxP on 2006-02-19
[QUOTE=arctic]English is not my native language. Sorry. :D[/QUOTE]
I wouldn't have guessed this; you write English excellently!

Probably better than me in fact -- English is my native language but I often convey things the wrong way and others misinterpret what I mean as a result. :oops:

---

