---
title: "&quot;Click here to download plugin&quot;"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by hodad on 2007-08-05
... along with a green puzzle piece, has been driving me nuts for about a year!

Can anyone point me to the proper directions for how to play these video clips, as I  can't figure out what I need to install to be able to play them. Have tried all sorts of things thru Synaptic installer.

Info on my pc:
Feisty Fawn
AMD-64 processor (about 2 years old)

Thanks for your help!

---

### Post by arijarot on 2007-08-05
What type of video clips do you want to play?

---

### Post by jfinkels on 2007-08-05
If you need to install the flash plugin, simply type:```
sudo aptitude install flashplugin-nonfree
``` in the terminal.

You can also try the vlc-plugin for mozilla. Of course, we need to know what exactly you are trying to play.

---

### Post by hodad on 2007-08-08
Hi,
Thanks for your responses...

I did "sudo aptitude install flashplugin-nonfree" and got the following:

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "flashplugin-nonfree"
The following packages have been kept back:
  firefox firefox-gnome-support gimp gimp-data gimp-python libgimp2.0
  libnspr4 libnss3 libpoppler1 libpoppler1-glib libqt3-mt locales
  poppler-utils popularity-contest tcpdump
0 packages upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

***************

Do I need to download "flashplugin-nonfree" from somewhere?

I don't know what type of video clips they are.  FOr instance, I just went to You Tube and it said "Java is turned off, or you need to install the newest Flash player.  I think they some of them may be Windows formatted clips (wmv?).

---

### Post by alienexplorers on 2007-08-08
To view YouTube videos I have Flash and Java loaded and they run like a charm.

---

### Post by splintercellguy on 2007-08-08
Are you using the 64-bit version of Ubuntu? In that case, you'll need nspluginwrapper: [http://ubuntuforums.org/showthread.php?t=425672](http://ubuntuforums.org/showthread.php?t=425672)

---

### Post by jfinkels on 2007-08-09
To install the flash plugin, you need to enable the "multiverse" repository. To do that, go to "System > Administration > Software Sources" and enable the checkbox next to the multiverse repository, then run the following command:```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

Click the first link in my signature to learn more about installing software.

---

### Post by hodad on 2007-08-31
Here's what I get, and Flash still doesn't work:

me@mydesktop:~$ sudo aptitude update && sudo aptitude install flashplugin-nonfree
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]

Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 6B in 1s (3B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

*******************

Any ideas?
Thanks!

---

### Post by illu45 on 2007-08-31
It looks like some other program is using the administrative packages. Make sure that Synaptic and the Add/Remove Programs applications are closed before you try running the command. If there are no other programs running and you still get the same error, try to reboot and run the commands again.

---

### Post by trak87 on 2007-08-31
"Could not get lock /var/lib/dpkg/lock" means you have more than one package installation program open at the same time. Only one program can get an exclusive lock on files at a time. So close one (or both) of the programs (like Synaptic, etc) and try again.

---

### Post by hodad on 2007-08-31
Hi!
THnaks for your quick responses.  I closed out all other programs, and the "lock" error went away, but I went to "You Tube" to try out flash, and got the same message:
"Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player."

I went into the JavaScript Console, and had about 30 messages messages of the following type:
Error: Error in parsing value for property 'width'.  Declaration dropped.
Source File: [http://www.youtube.com/watch?v=Fj08LvJpKWk](http://www.youtube.com/watch?v=Fj08LvJpKWk)
Line: 0

I'll try rebooting, and let you know if anything happened...

---

### Post by hodad on 2007-08-31
I closed out all programs and tried again.  The "lock" error went away, but I still get the following error message on You Tube:

Hello, you either have JavaScript turned off or an old version of Macromedia's Flash Player. Get the latest Flash player

Also, I went into the JavaScript console, and got about thirty messages like the following:

Error: Error in parsing value for property 'padding-top'.  Declaration dropped.
Source File: [http://www.youtube.com/css/styles_yts1187851135.css](http://www.youtube.com/css/styles_yts1187851135.css)
Line: 845

Any ideas?

Thanks again!

---

### Post by bignelly on 2007-08-31
I am a total amateur so set me strait if im totaly off the ball on this one but.......... I installed ubuntu on my laptop and it appeared to work fine but wierd error messages would pop up now and then and, i couldn't download plugins and other essential programs,(it appeared to download them but they would not work).  I started asking questions  on the forums and the suggested courses of action were having little or no positive effect. I eventually came to the conclusion that there was something fundamentally wrong with my ubuntu, re-burned the cd image (at the suggested speed ;8X:) re-installed my ubuntu from scratch and all my problems dissapeared, it played videos from youtube and many others when previously it was selective about what it would or would not play.

it sounds a little extereme, but for me it was easier than trying to diagnose then fix the problem

---

### Post by alienexplorers on 2007-08-31
When you load the plugins for flash and java and you are running firefox, make sure the plugins are listed in your plugin directory in your /mozilla profile directory.

---

### Post by trak87 on 2007-08-31
> **alienexplorers said:**
> When you load the plugins for flash and java and you are running firefox, make sure the plugins are listed in your plugin directory in your /mozilla profile directory.

You can also surf to "about&#58;plugins" without the quotes in Firefox.

---

### Post by hodad on 2007-08-31
"When you load the plugins for flash and java and you are running firefox, make sure the plugins are listed in your plugin directory in your /mozilla profile directory."

The above sounds intriguing, but I'm afraid I need a little more help implementing the suggestion.  What exactly do I look for, and if somethings missing from that directory, how do I add it?

Also I looked into about: plugins, and it told me about nswrapper, but I'm not sure the instructions would work for my AMD machine (K8 Athlon 64). Could this be a non-compatability issue with the Athlon processor?

Thanks

---

### Post by hodad on 2007-08-31
I didi some more reading, and downloaded nspluginwrapper 0.0.01.5.tar.bz2, but don't what directory to extract it into, or whether it will automatically install into the mozilla directory mentioned earlier (?).

---

### Post by hodad on 2007-09-16
I tried it again, and this time got:

sudo aptitude update && sudo aptitude install flashplugin-n onfree
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release [50.9kB]
Get:6 [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release.gpg [189B]
Hit [http://ubuntu.moshen.de](http://ubuntu.moshen.de) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages [120kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources [24.2kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages [7541B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources [979B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages [67.5kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources [8759B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages [2823B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources [778B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
99% [Connecting to [www.getautomatix.com](www.getautomatix.com) (216.120.255.9)]
99% [Connecting to [www.getautomatix.com](www.getautomatix.com) (216.120.255.9)]
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.9), connection timed out
Fetched 283kB in 2m0s (2351B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "flashplugin-nonfree"
The following packages have been kept back:
  firefox firefox-gnome-support gimp gimp-data gimp-python kdebase-bin kdebase-data kdelibs-bin kdelibs-data kdelibs4c2a kicker language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base libgimp2.0 libjasper-1.701-1 libkonq4 libkrb53 libnspr4 libnss3 libpoppler1
  libpoppler1-glib libqt3-mt libvorbis-dev libvorbis0a libvorbisenc2 libvorbisfile3 linux-amd64-generic linux-image-amd64-generic
  linux-restricted-modules-amd64-generic linux-restricted-modules-common locales poppler-utils popularity-contest rsync tar tcpdump vim vim-common
  vim-runtime
0 packages upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

***********

Process seemed to croak on the line:

"99%..." , as if it couldn't find the "getautomatix" site (?).  Maybe the site is down?

Any ideas on how to proceed?

Thanks!

---

