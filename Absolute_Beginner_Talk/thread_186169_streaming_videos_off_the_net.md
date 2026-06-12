---
title: "streaming videos off the net"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Vega on 2006-06-01
which apps are neeeded to install in dapper for streaming vids(incl w32 codecs)?


Thanks in advance as usual ^^"

---

### Post by bruenig on 2006-06-01
1.Make sure extra repositories are enabled [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

2.Depending on what media player you have, you will probably use one of the following. If you are unsure the Totem Gstreamer is probably the one you want since it is the default player for ubuntu.

For the Totem Gstreamer plugin install the totem-gstreamer-firefox-plugin package.
```
sudo apt-get install totem-gstreamer-firefox-plugin
```

For the Totem Xine plugin, install the totem-xine-firefox-plugin package.
```
sudo apt-get install totem-xine-firefox-plugin
```

For the Mplayer plugin, install the mozilla-mplayer package.
```
sudo apt-get install mozilla-mplayer
```

---

### Post by Vega on 2006-06-01
> redsteel@redsteel-d5150:~$ sudo apt-get install totem-gstreamer-firefox-plugin
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  totem-gstreamer
The following packages will be REMOVED:
  totem-xine
The following NEW packages will be installed:
  totem-gstreamer totem-gstreamer-firefox-plugin
0 upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 1078kB of archives.
After unpacking 65.5kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main totem-gstreamer 1.4.1-0ubuntu4 [1056kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe totem-gstreamer-firefox-plugin 1.4.1-0ubuntu4 [22.7kB]
Fetched 1078kB in 3s (304kB/s)
dpkg: totem-xine: dependency problems, but removing anyway as you request:
 totem depends on totem-gstreamer (>= 1.4.1-0ubuntu4) | totem-xine (>= 1.4.1-0ubuntu4); however:
  Package totem-gstreamer is not installed.
  Package totem-xine is to be removed.
(Reading database ... 78744 files and directories currently installed.)
Removing totem-xine ...
Selecting previously deselected package totem-gstreamer.
(Reading database ... 78619 files and directories currently installed.)
Unpacking totem-gstreamer (from .../totem-gstreamer_1.4.1-0ubuntu4_i386.deb) ...Selecting previously deselected package totem-gstreamer-firefox-plugin.
Unpacking totem-gstreamer-firefox-plugin (from .../totem-gstreamer-firefox-plugin_1.4.1-0ubuntu4_i386.deb) ...
Setting up totem-gstreamer (1.4.1-0ubuntu4) ...

Setting up totem-gstreamer-firefox-plugin (1.4.1-0ubuntu4) ...
redsteel@redsteel-d5150:~$ sudo apt-get install totem-xine-firefox-plugin
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  totem-xine
The following packages will be REMOVED:
  totem-gstreamer totem-gstreamer-firefox-plugin
The following NEW packages will be installed:
  totem-xine totem-xine-firefox-plugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 31.2kB/1096kB of archives.
After unpacking 45.1kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe totem-xine-firefox-plugin 1.4.1-0ubuntu4 [31.2kB]
Fetched 31.2kB in 1s (28.9kB/s)
(Reading database ... 78744 files and directories currently installed.)
Removing totem-gstreamer-firefox-plugin ...
dpkg: totem-gstreamer: dependency problems, but removing anyway as you request:
 totem depends on totem-gstreamer (>= 1.4.1-0ubuntu4) | totem-xine (>= 1.4.1-0ubuntu4); however:
  Package totem-gstreamer is to be removed.
  Package totem-xine is not installed.
Removing totem-gstreamer ...
Selecting previously deselected package totem-xine.
(Reading database ... 78619 files and directories currently installed.)
Unpacking totem-xine (from .../totem-xine_1.4.1-0ubuntu4_i386.deb) ...
Selecting previously deselected package totem-xine-firefox-plugin.
Unpacking totem-xine-firefox-plugin (from .../totem-xine-firefox-plugin_1.4.1-0ubuntu4_i386.deb) ...
Setting up totem-xine (1.4.1-0ubuntu4) ...

Setting up totem-xine-firefox-plugin (1.4.1-0ubuntu4) ...
redsteel@redsteel-d5150:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
redsteel@redsteel-d5150:~$



mmk.. this is the output I got from Terminal. What's next?

---

### Post by bruenig on 2006-06-01
did it not work when you tried to view a video online?

---

### Post by dvarsam on 2006-06-01
I will give you a couple of Examples:

1. To view this [http://www.pixar.com/featurefilms/ts/theater/index.html](http://www.pixar.com/featurefilms/ts/theater/index.html)
Toy story video...

You need to install the package "mozilla-mplayer".

2. To view this [http://www.intel.com/products/motherboard/d865perl/index.htm](http://www.intel.com/products/motherboard/d865perl/index.htm) Mobo Picture...

You need to install the package "j2re1.4-mozilla-plugin".

3. To view this [http://www.nokia.com/](http://www.nokia.com/) Nokia Mobile phone Pics...

You need to install the package "flashplayer-mozilla".

4. For the package "w32codecs", I do NOT have any example to offer, but you will need it for some sites/reasons...
(I hope somebody in this forum can offer a web address as an example where "w32codecs" are required...)

Good Luck with your installations,

dvarsam

---

### Post by Vega on 2006-06-01
meh. it didn't work"click here to download plugin". I have flash and java installed, flash player works.

---

### Post by dvarsam on 2006-06-01
Which does not work, Number1 (mozilla-mplayer)?

---

### Post by Vega on 2006-06-01
[QUOTE=dvarsam]Which does not work, Number1 (mozilla-mplayer)?[/QUOTE]
no it dosen't work. no player shows up, just a white box with a green puzzle piece.

---

### Post by dvarsam on 2006-06-02
[QUOTE=Vega]no it dosen't work. no player shows up, just a white box with a green puzzle piece.[/QUOTE]

Make sure, your file "sources.list" lying inside "/etc/apt/" includes the following Repos (you can copy & paste the following to your "sources.list" file):

> # For Ubuntu v6.06 - Dapper Drake:
# -------------------------------

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-updates main restricted


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper universe


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


## This was added (as  asked)
## Multiverse

deb [http://gr.archive.ubuntu.com/ubuntu](http://gr.archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse


## Backports:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

When finished, open Synaptic Package Manager & perform a "Reload" (similar to running "apt-get update" from the Terminal).

Then perform a search for "mozilla-mplayer"...

You should now be able to find it!

Then go ahead, download & install the package!

Good Luck!!!

P.S.> If you do NOT have the correct Repos activated (the correct lines in your "sources.list" file), you will not be able to perform a search, locate & install the package you are looking for...

---

### Post by cowley on 2006-06-02
hi try using automatix - this downloaded and installed everything i needed for media etc

simon

---

### Post by Vega on 2006-06-02
[QUOTE=cowley]hi try using automatix - this downloaded and installed everything i needed for media etc

simon[/QUOTE]
automatix for dapper dosen't work for me though(as far as installing codecs and mozilla plugins for streaming media)

---

### Post by Rackerz on 2006-06-02
[QUOTE=Vega]automatix for dapper dosen't work for me though(as far as installing codecs and mozilla plugins for streaming media)[/QUOTE]

You will need to install w32codecs and this package, totem-xine-firefox-plugin.

---

### Post by patrick295767 on 2006-06-02
You can also try my script multimedia.sh in my signature ... 
Greetz !!

Pat'

---

### Post by dvarsam on 2006-06-02
[QUOTE=Rackerz]You will need to install w32codecs and this package, totem-xine-firefox-plugin.[/QUOTE]

I confirm that:

Installing the Package "totem-xine-firefox-plugin" lets your Totem play DVD Movies.

Hopefully you should get the same result.

Good Luck.

---

