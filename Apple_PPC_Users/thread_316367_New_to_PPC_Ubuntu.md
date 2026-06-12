---
title: "New to PPC Ubuntu"
date: 2006-12-10
forum: Apple PPC Users
---

### Post by Ubunto&amp;XP&gt;98&gt;Mac7&gt;ST&gt;994a on 2006-12-10
I am sure this is located some where, but I am very busy and going to rudely ask away.  :p 

I have just recieved an iBook G3 with 256 Ram and 14 GB HD.  I have installed OS X 10.4 and X windows, also I am able to boot in to OS 9.2.2.  I have an old program that requires to boot into OS 9.  I have about 7 GB left.

If I install Ubuntu 6.10, how much hard drive space do I need to give up to linux.  I formatted the drive for HFS+.  I assume I need to make a new partition for linux.  Had I used the Unix File system, would I have had to make a new partition to run both OS X and Ubuntu?  

How easy is it to dual boot with PPC.  I use GRUB on an AMD Athlon and it's not too bad to use and the guides are good enough to get me around.

Even though I have a 64-bit CPU I use the 32 bit Ubuntu b/c of the plug-in and codec issues.    How much is not going to be there on the PPC side of Ubuntu as far as program, plug-ins and codecs availablity. 

Thanks so much.:D :D

---

### Post by ssam on 2006-12-12
2gb is a sensible minimum for an ubuntu install (it will have very little space for documents). it will need to be on a new partition in ext3 format (if you want to use the apple partitioner leave some disk as unallocated, the ubuntu installer can then create the partition). you will also need a swap partition (to be used as virtual memory) 512mb to 1gb would be enough. dont bother with the 'unix file system' that mac os x offers, it does not help with linux.

the dual boot is set up by the installer.

with powerpc you not be able to use flash.
there is java, see [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
there is no w32codecs, but all the gstreamer codecs can handle most things.
there is a realplayer package but i have found it buggy.
no proprietry graphics drivers, the open source radeon driver is good though.

---

### Post by stmiller on 2006-12-13
> **ssam said:**
> 

with powerpc you not be able to use flash.
there is java, see [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
there is no w32codecs, but all the gstreamer codecs can handle most things.
there is a realplayer package but i have found it buggy.
no proprietry graphics drivers, the open source radeon driver is good though.

You can now view flash video in PPC Linux with the latest VLC player. 0.8.6. It plays flash video, though you must extract the video file from youtube, etc. first with something like this:
[http://1024k.de/bookmarklets/video-bookmarklets.html](http://1024k.de/bookmarklets/video-bookmarklets.html)

The latest mplayer and vlc plays all windows codecs. Everything you could imagine. Even WMV9 content with the latest VLC.

[http://www.videolan.org/vlc/features.html](http://www.videolan.org/vlc/features.html)

The realplayer program from the Helix Community site works fine for me, and is not buggy at all. What problems are you having?

There is a mplayer plugin for firefox. I can watch the HD movie trailers from apple.com with no problem. 

I haven't run into any problems with codecs, though java is a pain at times.

---

### Post by 3rdalbum on 2006-12-14
I don't believe you can install Ubuntu in 2 gigabytes, unless you install Ubuntu Server and customise on top of that. 3 gigabytes may be a little too small for an Ubuntu Desktop install, when you include swap space. 3.5 gigs should be okay.

For some people, the Realplayer package just crashes if you try to play a Realmedia file.

Yaboot should automatically detect your OS X, but it might not. If you can edit the GRUB configuration file, you should be fine with the Yaboot one.

---

### Post by calum on 2006-12-23
> **Ubunto&XP>98>Mac7>ST>994a said:**
> I assume I need to make a new partition for linux.  Had I used the Unix File system, would I have had to make a new partition to run both OS X and Ubuntu? 


FWIW, yes, you would still have had to make a new partition.

---

