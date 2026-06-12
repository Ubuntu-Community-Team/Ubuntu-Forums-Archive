---
title: "followed instruction to enable multi-media, but still nothing"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by mgh on 2007-06-13
Hi All,

Still stuck trying to get 7.04 to play a DVD.

I followed the instructions on the post at the beginning of this forum, but still get the message:  "there is no plugin to handle this movie".

Not sure where to turn to next, and for certain do not know how to undo what I just did!

Before this I tried following instruction from WIKI, but got the same result.

Thanks for any help.

---

### Post by Seisen on 2007-06-13
Exactly what have you tried, can you post the links.

---

### Post by mgh on 2007-06-13
this is the first post I tried, and here is the commands I tried and replies.  [http://www.reviewlinux.com/index.php?m=show&id=6034](http://www.reviewlinux.com/index.php?m=show&id=6034)

mike@mike-desktop:~$ sudo apt-get install ubuntu-restricted-extras libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer 
Password: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
gstreamer0.10-plugins-base is already the newest version. 
gstreamer0.10-plugins-good is already the newest version. 
E: Couldn't find package gstreamer 
mike@mike-desktop:~$ sudo apt-get install w32codecs 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Package w32codecs is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 
E: Package w32codecs has no installation candidate 
mike@mike-desktop:~$ sudo apt-get install libdvdread3 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
libdvdread3 is already the newest version. 
libdvdread3 set to manual installed. 
The following packages were automatically installed and are no longer required: 
  libktoblzcheck1c2a libgwenhywfar-data libaqbanking-data 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
mike@mike-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh 
--19:12:26--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb) 
           => `/tmp/dvdcss-Ll7973/libdvdcss.deb' 
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198 
Connecting to www.dtek.chalmers.se|129.16.30.198|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 25,178 (25K) [text/plain] 

100%[====================================>] 25,178        39.28K/s             

19:12:27 (39.23 KB/s) - `/tmp/dvdcss-Ll7973/libdvdcss.deb' saved [25178/25178] 

Selecting previously deselected package libdvdcss2. 
(Reading database ... 123901 files and directories currently installed.) 
Unpacking libdvdcss2 (from .../dvdcss-Ll7973/libdvdcss.deb) ... 
Setting up libdvdcss2 (1.2.5-1) ... 

mike@mike-desktop:~$ sudo apt-get install totem-xine 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  libktoblzcheck1c2a libgwenhywfar-data libaqbanking-data 
Use 'apt-get autoremove' to remove them. 
The following packages will be REMOVED: 
  totem-gstreamer 
The following NEW packages will be installed: 
  totem-xine 
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded. 
Need to get 1343kB of archives. 
After unpacking 180kB disk space will be freed. 
Do you want to continue [Y/n]? y 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe totem-xine 2.18.1-0ubuntu3 [1343kB] 
Fetched 1343kB in 18s (74.2kB/s)                                               
dpkg: totem-gstreamer: dependency problems, but removing anyway as you request: 
 totem-mozilla depends on totem-xine (>= 2.18.1-0ubuntu3) | totem-gstreamer (>= 2.18.1-0ubuntu3); however: 
  Package totem-xine is not installed. 
  Package totem-gstreamer is to be removed. 
 totem depends on totem-gstreamer (>= 2.18.1-0ubuntu3) | totem-xine (>= 2.18.1-0ubuntu3); however: 
  Package totem-gstreamer is to be removed. 
  Package totem-xine is not installed. 
(Reading database ... 123909 files and directories currently installed.) 
Removing totem-gstreamer ... 
Selecting previously deselected package totem-xine. 
(Reading database ... 123726 files and directories currently installed.) 
Unpacking totem-xine (from .../totem-xine_2.18.1-0ubuntu3_i386.deb) ... 
Setting up totem-xine (2.18.1-0ubuntu3) ... 

mike@mike-desktop:~$ sudo apt-get install libdvdcss2 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
libdvdcss2 is already the newest version. 
The following packages were automatically installed and are no longer required: 
  libktoblzcheck1c2a libgwenhywfar-data libaqbanking-data 
Use 'apt-get autoremove' to remove them. 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 


After this did not work, I tried following the instructions here:  [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Same results.

Thanks for the reply.

---

### Post by zvacet on 2007-06-14
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Gmbrdilos on 2007-06-14
DVD codecs are not free which is why it is not supplied with ubuntu by default. You can install it through automatix but as far as I know that's illigal for US residents.

---

### Post by NeoLithium on 2007-06-14
There's also a good walkthrough on [http://www.ubuntuguide.org](http://www.ubuntuguide.org) For getting the restricted formats, though as stated above, they're basically use at your own risk due to legality in certain jurisdictions.

---

### Post by jcronkhite on 2007-06-14
Download [Automatix 2]("http://getautomatix.com/") and [VLC Player]("http://www.videolan.org/").  I'd install the codecs first with Automatic, then install VLC (I think you can install VLC with Automatix, can't remember).  Anyway, give that a shot.

---

### Post by jfoobar on 2007-06-14
I followed the command line instructions posted elsewhere and had the same problem with Totem.  However, I installed VLC Player and had no problems.

I used to run VLC on a Win32 laptop in lieu of paying for PowerDVD or something like that and it works fine, it just isn't as full-featured as I would like.

---

### Post by mgh on 2007-06-14
Thanks for the replies!

VLC is not able to play DVD either.

This is not a huge issue for me, mostly trying to understand what is going on, and if it is a hardware issue, or software/codec thing.

I am also having trouble with grip reading that drive to rip audio CDs, even though sound juicer will read the same drive and function properly.

Should I resolve the drive mounting or naming before working more on multi-media support?

Thanks a lot for the help.

---

