---
title: "Official &quot;I got an iPod for Christmas, how do I make it work w/ Ubuntu?&quot; thread"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by woodsonoversoul on 2007-12-26
I'm sure this has been touched on elsewhere but I thought I'd wrap all the questions (and hopefully answers) in one place.


I got an 8 gig Nano for christmas and have been playing around w/ different audio players tring to connect to it, and none have really worked. I've been using rhytmnbox, I'd like to switch over to banshe or amarok (I don't like the way gtkipod looks). In the course of messing around with these programs I've managed to put music on my iPod that the iPod software can't see. I can explore the device through nautilus and see my music files but once I disconnect the iPod from my machine it says it has no music. Can anyone explain why/help? Thanks

---

### Post by superm1 on 2007-12-26
Please set up the ppa repository as described on this page: 

[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

It works for the newer nanos and classics as well.  You don't need to do all the iPhone/iPod touch related stuff though.

---

### Post by rye_ on 2007-12-26
[ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod](ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod)

download libgpod2.
I've done this and it works great.  

Ryan

---

### Post by rye_ on 2007-12-26
I probably ought to mention that I use rhythmbox rather than gtkpod to manage my ipod, which is a recent classic 160GB.

Ryan

---

### Post by buccaneere on 2007-12-26
[IMG]http://www.corvetteforums.com/upfiles/smiley/boohoo.gif[/IMG]

I didn't get one.

All I wanted was a flux capacitor. (didn't get that one either[IMG]http://www.corvetteforums.com/upfiles/smiley/boohoo.gif[/IMG]

---

### Post by woodsonoversoul on 2007-12-26
I think maybe it got formatted wrong? I originally hooked it up to a windows machine to charge it. The computer didn't have Itunes, so I didn't go through anykind of setup process.

---

### Post by LowSky on 2007-12-26
> **woodsonoversoul said:**
> I think maybe it got formatted wrong? I originally hooked it up to a windows machine to charge it. The computer didn't have Itunes, so I didn't go through anykind of setup process.

format has nothing to do with it as PC based Ipods all use FAT32 as the fileformat and Linux can read that no porblem. The newer ipod (released this year) are still not working with Linux all too well yet, give it time. Its Apple's fault as they do not support Linux Users, so as a community we have to make our own.

---

### Post by woodsonoversoul on 2007-12-26
gtkpod is saying that it can't find any ipods and amarok says it finds them just fine. The apple software does'nt see it though

---

### Post by LowSky on 2007-12-26
have you tried Rye_'s suggestion?

> **rye_ said:**
> [ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod](ftp://64.22.103.45/packages/ubuntu/gutsy/libgpod)

download libgpod2.
I've done this and it works great.  

Ryan

---

### Post by hollowhead on 2007-12-26
See this thread 
[http://ubuntuforums.org/showthread.php?t=619615&page=9](http://ubuntuforums.org/showthread.php?t=619615&page=9)

follow the link posted by siwilson or me and follow the instructions it will work see my post for variations......

---

### Post by raul_ on 2007-12-26
I have a classic 80gb iPod. 
Install latest libgpod and gtkpod and then you need to do this trick:

> The 2nd method requires more manual intervention. First, you need to get your
    firewire id manually. To do that, run &#8220;sudo lsusb -v | grep -i Serial&#8221; (without
    the &#8220;&#8221;) with your iPod plugged in, this should print a 16 character long string
    like 00A1234567891231. Once you have that number, create/edit
    /mnt/ipod/iPod_Control/Device/SysInfo (if your iPod is mounted at /mnt/ipod).
    Add to that file the line below:
    FirewireGuid: 0xffffffffffffffff
    (replace ffffffffffffffff with the string you obtained at the previous step)
    Save that file, and you should be all set. Be careful when using apps which
    lets you manually specify which iPod model you own, they may overwrite that
    file when you do that. So if after doing that libgpod still seems to write
    invalid content to the iPod, double-check the content of that SysInfo file to
    make sure the FirewireGuid line you added isn&#8217;t gone. If that happens, readd it
    to the end of the file, and make sure libgpod rewrite the iPod content.

Restart Amarok or whatever your audio program is.

[http://neoaddict.wordpress.com/2007/09/26/updating-libgpod/]("http://neoaddict.wordpress.com/2007/09/26/updating-libgpod/")

---

