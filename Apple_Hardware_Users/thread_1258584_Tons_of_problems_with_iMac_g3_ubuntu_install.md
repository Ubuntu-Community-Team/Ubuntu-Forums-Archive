---
title: "Tons of problems with iMac g3 ubuntu install"
date: 2009-09-05
forum: Apple Hardware Users
---

### Post by CV 4 Lyfe on 2009-09-05
Its a g3 iMac with 64MB of ram powerpc 750 cpu @400mhz and a 10.2GB hard drive.

I currently have Cli-powerpc installed but my problem is I cannot download any of the new packages so I can get and install xorg and every thing els I would need to get a gui 

I am a windows person so please dumb every thing down as much as possible I have used ubuntu before and I am a little fimalure with most basic things but its been some time and I just want this at this point STUPID! iMac to work.

Iv wasted about 20 CD-R's burning differnt copys of "OS" and none of them work at all but all the linux disks I burnt with out a hitch so basically if you can help me in the picture will show you where I am stuck at.

*and yes I am sure I was getting the correct copies of "OS" but iv given up on any kind of apple software it has to be some kinda of linux distro or this POS is hitting CL*


[http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934) 

Iv been trying that guide with 100% no luck at all if it where not for all the other people saying it works i'd say it was a lie... just like the cake.

And iv also just noticed that the date stamp on my camera=fail.

The second picture is all that happens when I try to boot a cd.

[IMG]http://i100.photobucket.com/albums/m31/oooooooooo32/DSCI1698.jpg[/IMG]

[IMG]http://i100.photobucket.com/albums/m31/oooooooooo32/DSCI1710.jpg[/IMG]

---

### Post by rjcalifornia on 2009-09-05
Hey, I see your problem: 64 MB of RAM. Even if you get to install it correctly, it will be useless. Try Xubuntu 6.10...

I know how you feel about the cd's wasted, right now I find myself without Linux ... It's exasperating....

---

### Post by CV 4 Lyfe on 2009-09-05
> **RandyVanBuren said:**
> Hey, I see your problem: 64 MB of RAM. Even if you get to install it correctly, it will be useless. Try Xubuntu 6.10...

I know how you feel about the cd's wasted, right now I find myself without Linux ... It's exasperating....

I couldn't find a download of it but at the time I didn't look very hard so a link would help but ill google some more.

---

### Post by ssam on 2009-09-05
you probably have no network connection.

assuming you are plugged into ethernet try:
```

sudo dhclient eth0

```
then do
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xubuntu-desktop
sudo reboot

```

also upgrade the ram.

---

### Post by CV 4 Lyfe on 2009-09-05
> **ssam said:**
> you probably have no network connection.

assuming you are plugged into ethernet try:
```

sudo dhclient eth0

```then do
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xubuntu-desktop
sudo reboot

```also upgrade the ram.

I know that its connected because I can ping any thing I want just fine but every time I try to update,upgrade, or download any kind of package I get the error E: Couldn't find package xubuntu-desktop

I also cannot update or upgrade because of the same error.

Found it and I get the same boot error as almost every thing els I try so far the only thing I can get to boot from cd is Debian and ubuntu. tried every apple OS supported they don't boot.

---

### Post by 3rdalbum on 2009-09-06
Well, you're trying to use Ubuntu 6.10, which is why you can't get any packages. Ubuntu 6.10 is End Of Life as of mid-2008, so the repositories are not at the usual place.

Try the community build of Ubuntu 9.04 or 8.04.

Alternatively, I believe there might be a repository archive hosted somewhere, that stores packages from old Ubuntu releases. This would involve changing the contents of your /etc/apt/sources.list file to point to the new archive. After changing the list, you would need to run:

```
sudo apt-get update
```

to get the list of available packages from the archive repository.

Frankly, I'd be tremendously surprised if you can run anything more than a CLI Ubuntu system on 64 megabytes of RAM. Ubuntu is just not that lightweight, and there are no actual lightweight PowerPC-based distros out there.

---

### Post by CV 4 Lyfe on 2009-09-06
> **3rdalbum said:**
> Well, you're trying to use Ubuntu 6.10, which is why you can't get any packages. Ubuntu 6.10 is End Of Life as of mid-2008, so the repositories are not at the usual place.

Try the community build of Ubuntu 9.04 or 8.04.

Alternatively, I believe there might be a repository archive hosted somewhere, that stores packages from old Ubuntu releases. This would involve changing the contents of your /etc/apt/sources.list file to point to the new archive. After changing the list, you would need to run:

```
sudo apt-get update
```to get the list of available packages from the archive repository.

Frankly, I'd be tremendously surprised if you can run anything more than a CLI Ubuntu system on 64 megabytes of RAM. Ubuntu is just not that lightweight, and there are no actual lightweight PowerPC-based distros out there.


I can give that a try iv done edited the sources list before.

---

### Post by cptfx on 2009-09-06
I'm far from experienced user, but I'm playing around with Ubuntu on a G3.  I had 6.10 on there for awhile so I came across the sources.list problem.  I couldn't find anything that had updates for Edgy (only looked at archives.ubuntu and ports.ubuntu,  there maybe be more out there..?).  Dapper and Hardy are there but no Edgy

So now I'm running 9.04, although I'm in much better shape with 256MB of ram.  But I did come across[ this]("https://help.ubuntu.com/community/Installation/LowMemorySystems") (help.ubuntu.com) in my search.  Maybe that will help.

---

