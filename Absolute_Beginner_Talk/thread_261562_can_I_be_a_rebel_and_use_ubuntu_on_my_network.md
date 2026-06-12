---
title: "can I be a rebel and use ubuntu on my network"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by don bohrer on 2006-09-20
Hi guys. I would like to replace a windows 2000 box that hangs on my network with the latest release (6.06) of Ubuntu. I have found easyubuntu, but am experiencing some of the recent installation bugs with it. 

I need to meet these requirements. 

1. ldap authentication - I could wait on this and use multi user login.
2. play all major audio/vidio formats - media player, realone, quicktime, etc.
3. view flash and java web components
4. run norton antivirus

At local and corporate level I work in an exclusively microsoft environment. I must meet certain requirments for my user base. If ubuntu can bridge this gap I could be a rebel and hang a nice non windows box on my network.

Any and all help to do this would be greatly appreciated.

thanks in advance.

don (el paso) :D

---

### Post by benuski on 2006-09-20
1. With LDAP, I can't think of an example of something that supports it, but I know that there are LDAP clients out there for linux.  I'm probably just brain farting.
2. As long as you go to the [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats") page and install all of the codecs, including the w32codecs, you should be able to play at least the wmv/wma, mp3, RealPlayer, Quicktime, etc.  Alternatively, RealPlayer makes a version spefically for linux, so you can just use that.
3.Also on the Restricted formats page, it tells you how to set it up so you can use Flash and Java.  However, Flash support for linux is only up to Version 7, so if you need anything after that, you won't be able to get it on linux.
4. I'm fairly certain that Norton only runs on Windows machines and  Macs.  However, there is really not a big need for anti-virus software on Ubuntu as no one makes viruses for linux.  Since its open source, the hole that the virus is exploiting could be closed within a matter of hours, or days at the most.

Hope this helps.

---

### Post by philipgm on 2006-09-20
Playing all the video codecs could depend on how tight your company is on non-free codecs, there may be licencing issues. 

Norton Antivirus does not run. ClamAV is the main alternative on ubuntu (now also available for windows)

Frankly, I think your chances are pretty thin. But let us know if you can get them to wear it - I know my network manager is very wary of these things.

Regards

Phil

---

### Post by don bohrer on 2006-09-21
benuski, philipgm. 

Today has been a productive day for setting up ubuntu at work. I found [www.getautomatix.com](www.getautomatix.com) page and tried their installer. This turned out to be a very painless install for a bunch of desired software. I managed to get quiet a bit of media packages installed. 

However I was unable to play embedded media 100% with the correct players, and even though flash was installed some websites didn't detect. 

At this point I think I have to tell ubuntu or firefox what player to use for each media type? Not sure? Of all things my biggest hurdle would be to play most popular formats of embedded media. I don't actually need a stand alone players for this. 

thanks for your help, advice, and thoughts on this. I'll come back here and post my results. 

don (el paso)

---

### Post by CatKiller on 2006-09-21
> **don bohrer said:**
> Of all things my biggest hurdle would be to play most popular formats of embedded media. I don't actually need a stand alone players for this.

The **mozilla-mplayer** plugin will play everything that MPlayer can play, so if you've got all the codecs installed you should be good to go.

With Flash, the latest version is 9, but the latest version for Linux is 7. A number of sites check to see if you have the latest version installed, even though they don't need the latest version. There is a method to make your Flash 7 appear to be Flash 9 so that these sites will work. I don't know what that method is, mind, since I've not yet had to do it, but I read about it on this forum so a search should yield some results.

Good luck!

---

