---
title: "[SOLVED] Distribution upgrade (ppc) from 6.06 to 8.04 with UpdateManager no good"
date: 2008-04-26
forum: Apple Hardware Users
---

### Post by ubuntubrian on 2008-04-26
I tried a dist upgrade with Update manager but it fails due to not finding the correct or non-existent mirror. 
Essentially UpdateManager debug adds a source and then fails to find it when fetching. This is because there is no such address for the debian installer for powerpc though there are for "hppa" and "ia64". Any ideas for a workaround? It would be great to be able to upgrade the UpdateManager way!I have posted this on this thread:
[http://ubuntuforums.org/showthread.php?p=4797154#post4797154](http://ubuntuforums.org/showthread.php?p=4797154#post4797154)


> I'm getting this from the log file but it appears that Update Manager debug is adding a source that it then cannot access, ie,
Code:

DEBUG adding 'deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) dapper-backports main/debian-installer

It then tries to
Code:

ERROR IOError/SystemError in cache.update(): 'Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/dapper-backports/main/debian-installer/binary-powerpc/Packages.gz](http://ports.ubuntu.com/ubuntu-ports/dists/dapper-backports/main/debian-installer/binary-powerpc/Packages.gz) 404 Not Found

there is no
Code:

[http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) dapper-backports main/debian-installer


Thanks

---

### Post by tamoneya on 2008-04-26
I believe canonical ended support for ppc with hardy.  Not positive on this but i believe this means that there is not a work around.  I think they decided that there were not enough users for it to be worth continuing.

---

### Post by stream303 on 2008-04-26
> **tamoneya said:**
> I believe canonical ended support for ppc with hardy.  Not positive on this but i believe this means that there is not a work around.  I think they decided that there were not enough users for it to be worth continuing.

Support is alive and well, although it is "unofficial", meaning volunteer status and if there are any show-stopping bugs, it won't affect the mainstream architectures from being released.  Also, just because it is unofficial, doesn't mean that it is lacking quality.  A few devs are working on a fan situation that happens during install only on G5's as we speak in their free time.

There are PPC Hardy versions available for Ubuntu, Xubuntu, Kubuntu, Server, and Edubuntu - you just need to traverse the "ports" directories, or better yet use a torrent, especially because the ppc Hardy builds are not carried on mirrors to save space and bandwidth:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)
and
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

---

### Post by stream303 on 2008-04-26
> **ubuntubrian said:**
> I tried a dist upgrade with Update manager but it fails due to not finding the correct or non-existent mirror.

I wondered about that - if the /etc/apt/sources.list file would be updated - perhaps not.

Here's mine.  I wouldn't activate the backports just yet.  Be sure to leave a space between "ubuntu-ports/" and "hardy"

```
deb http://ports.ubuntu.com/ubuntu-ports/ hardy main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates main restricted
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb http://ports.ubuntu.com/ubuntu-ports/ hardy universe
## deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ hardy multiverse
# deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ports.ubuntu.com/ubuntu-ports/ hardy-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

# deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security main restricted
# deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security main restricted
# deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security universe
# deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security universe
# deb http://ports.ubuntu.com/ubuntu-ports/ hardy-security multiverse
# deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-security multiverse
```

As I came from an RC, I had to manually modify it per the notice here:

[http://www.xubuntu.org/news/hardy/ports](http://www.xubuntu.org/news/hardy/ports)

Once I edited this file, I manually ran
```
sudo apt-get update

sudo apt-get upgrade
```

I wonder if you'd have better luck modifying your sources.list file, doing an apt-get update, apt-get upgrade, and then apt-get dist-upgrade?  There are probably better ways to do this, I don't know since I haven't done this on anything but Debian Lenny.

Also note that my repositories all show up in "3rd-party", and not in the main tab.  In the main tab of software sources, I have all of them UNchecked.

I'm still doing some research about the ubuntu-ports, and wonder if it will be normal for us to only use "3rd-party" repos, even if in this case they come from Ubuntu.

---

### Post by ubuntubrian on 2008-04-26
Thanks for the responses.
Unfortunately in Dapper 6.06 I don't have the 3rd party option in Synaptic repositories, just "Installation Media-Channels". I know that Hardy has 3rd party, etc. as it runs on my other PowerBook (Lombard).
I'm not sure it's possible to do a direct apt upgrade from 6.06 to 8.o4 and that's why I was excited about UpdateManager figuring it all out.
Also, it is UpdateManager that creates the repository that it then fails to connect to-a Catch 22.

---

### Post by ssam on 2008-04-26
probably some artifact of powerpc moving from the main server to the ports server between dapper and hardy.

you ought to file a bug.

if you can't wait then you may have to do a clean install of hardy. the new desktop installer can install over an existing partiton preserving the home folder. make sure you have a back up though. you will still need to reinstall all your applications.

---

### Post by ubuntubrian on 2008-04-26
Thanks Ssam! I was pretty much thinking that would be the way I'd have to go. I read about the /home preservation installation that Hardy provides and if I have to I'll go that route. I will file the bug and see if that heads anywhere first. I'm not in a real hurry to upgrade, just a perceived one!
:popcorn:

---

### Post by vnevoa on 2008-05-03
Hi. I've got the same problem on an Old World PowerMac G3... can't upgrade to Hardy.

I'm stuck at 6.06, because I can't do a full CD install of anything later than 5.10 (long story, has to do with the "BootX" bootloader not loading the newer ramdisk images).

I filed a bug report ([226217]("http://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/226217")). I'd like to know the official position on this subject. Is there a "dapper-backports" repo or not?... Is it possible to upgrade dapper on a powerpc, or is it required to be a fresh install?

---

### Post by slacka-vt on 2008-05-03
OK, give this a shot.

```
sudo nano /etc/apt/sources.list
```

This is what my sources.list looks like and works as of 2008-05-03
So try adding those url's to your sources.list

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


deb http://ports.ubuntu.com/ hardy main restricted
deb-src http://ports.ubuntu.com/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ports.ubuntu.com/ hardy-updates main restricted
deb-src http://ports.ubuntu.com/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ports.ubuntu.com/ hardy universe
deb-src http://ports.ubuntu.com/ hardy universe
deb http://ports.ubuntu.com/  hardy-updates universe
deb-src http://ports.ubuntu.com/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ports.ubuntu.com/ubuntu-ports/ hardy multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy multiverse
deb http://ports.ubuntu.com/ubuntu-ports/ hardy-updates multiverse
deb-src http://ports.ubuntu.com/ubuntu-ports/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ports.ubuntu.com/ hardy-backports main restricted universe multiverse
deb-src http://ports.ubuntu.com/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://ports.ubuntu.com/ hardy partner
deb-src http://ports.ubuntu.com/ hardy partner
```


next try

```
sudo aptitude update
sudo aptitude dist-upgrade
```

~s

---

### Post by vnevoa on 2008-05-04
I think I found the workaround.
I added this to sources.list:
```
deb http://archive.ubuntu.com/ubuntu dapper-backports main/debian-installer

```
and the upgrader is finally pumping away... :)
Let's see if it finishes correctly.

---

### Post by vnevoa on 2008-05-08
I confirm that the workaround is good.
The upgrade went slightly wrong, but for entirely different reasons (hardy HAL bugs).

---

### Post by ubuntubrian on 2008-08-02
A long time in replying but I finally checked back to this post (to which I had subscribed but didn't get any notifications!) I used the workaround and it works! I had some HAL issues as well as dpkg but they hadnothing to do with updatemanager. the Upgrade crapped out after all the dpkg dependency errors and packages that could be installed were. I needed to purge some python packages and the build continued in terminal. reinstalled the python packages and rebooted-perfect! No sound or power issues. Everything works!!:guitar:

---

### Post by jazzop on 2008-09-20
> **vnevoa said:**
> I think I found the workaround.
I added this to sources.list:
```
deb http://archive.ubuntu.com/ubuntu dapper-backports main/debian-installer

```
and the upgrader is finally pumping away... :)
Let's see if it finishes correctly.

I can add that this worked for me as well, upgrading from 6.0.6 to 8.04, as of the date of this post.

---

### Post by fisheatdog on 2008-10-09
For some reason I can't get it to work. Can someone post up a copy of their source.list?
Thanks.

---

### Post by rnoboa on 2009-01-12
I'm having the same issue. It's not letting me upgrade from Dapper to Hardy. I'm running a G4 Cube.

---

