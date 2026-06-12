---
title: "Fiesty upgrade"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by BillGod on 2007-02-28
I know it's still in dev.  There are a couple of features I am looking for that are in fiesty.  I want to uprade from edgy.  If I loose all my data that fine.  No I dont want to install from scratch.  Ok that should cover 99% of the comments.  I need to know how to upgrade to fiesty.  I would like to do it through apt.

Thanks

---

### Post by astoltz on 2007-02-28
I only know how to do it from the command line...

```
sudo nano /etc/apt/sources.list
```Change everything that references "edgy" to "fiesty".  Save the file and quit nano. Then:
```
sudo apt-get update
sudo apt-get dist-upgrade
```Cross your fingers and press the enter button...
And let us know how it went

---

### Post by ThrobbingBrain66 on 2007-02-28
or you can open a terminal and type ```
update-manager -c -d
```
just a little faster than the above method

---

### Post by BillGod on 2007-02-28
my sources.list looks like this.

#  fiesty Final Release Repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) fiesty main restricted universe

# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) fiesty main restricted universe multiverse

# fiesty Security Updates
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) fiesty-security main restricted universe

# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) fiesty-security main restricted universe multiverse

# fiesty Bugfix Updates
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) fiesty-updates main restricted universe


Apt-get wont update cant find anything.

bill@Ubuntu-Bill:~$ sudo apt-get update


Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates/universe Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty/main Packages
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty/restricted Packages
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security/main Packages
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security/restricted Packages
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-security/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates/main Packages
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates/restricted Packages
  404 Not Found [IP: 91.189.89.6 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) fiesty-updates/universe Packages
  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/fiesty/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/fiesty/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/fiesty/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/fiesty/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/fiesty/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/fiesty/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/fiesty-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/fiesty-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/fiesty-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/fiesty-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/fiesty-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/fiesty-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/fiesty-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/fiesty-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/fiesty-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/fiesty-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/fiesty-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/fiesty-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.6 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


bill@Ubuntu-Bill:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by ThrobbingBrain66 on 2007-02-28
you spelled feisty wrong ;)

---

### Post by BillGod on 2007-02-28
AHHH spelling never was my strong side!!   k will let you know how i end up.. if I can still access the net  :)

---

### Post by SunnyRabbiera on 2007-02-28
I would personally wait if I were you as feisty isnt even ready yet.
If your upgrade fails just use edgy until Feisty is out of the oven

but please for the love of mike and the rest of the beatles back up your data!

---

### Post by Quillz on 2007-02-28
> **SunnyRabbiera said:**
> I would personally wait if I were you as feisty isnt even ready yet.
If your upgrade fails just use edgy until Feisty is out of the oven

but please for the love of mike and the rest of the beatles back up your data!
I don't know about you, but for me, Herd 4 has been extremely stable, even more so after last night's updates.
 
Alternatively, if you want a hard copy to upgrade with, just grab a Herd 4 torrent and burn the .iso to a CD.

---

### Post by astoltz on 2007-02-28
Did a little more searching and found [this link]("https://help.ubuntu.com/community/FeistyUpgrades").  Should be helpful upgrading to Feisty

---

### Post by BillGod on 2007-03-01
Just a quick note to everyone.  Upgrade complete and working.   little issues with beryl but got them resolved.  Other than that looking good so far.  I gotta give my props to Team Ubuntu.  I upgraded to edgy about a month before release and never regretted it.  Looks like this is going to be about the same.

Thanks guys

BillGod

---

### Post by maprx on 2007-03-04
> **astoltz said:**
> Did a little more searching and found [this link]("https://help.ubuntu.com/community/FeistyUpgrades").  Should be helpful upgrading to Feisty

that link did nothing see the result

mike@mike-desktop:~$ gksu mkdir /root/.gnupg
mike@mike-desktop:~$ gksu "update-manager -d"
warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

