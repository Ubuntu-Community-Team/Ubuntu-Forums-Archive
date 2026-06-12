---
title: "USB ADSL Modem problems"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Sonic Alpha on 2006-07-09
Hi all,

I'm completely new to Ubuntu, and managed to install without a problem... well except one.

I can't seem to detect my USB ADSL modem.  I did a little googling, and found [this]("http://eciadsl.flashtux.org/tutorial.php?lang=en"), which seems to be the answer (I have a BT Voyager 100 ADSL modem, which it supports).

However, as there is no .rpm file available for Ubuntu, I'm unsure of what to do (this is all the tutorial covers).

Could someone help me, please?

---

### Post by %hMa@?b&lt;C on 2006-07-09
sudo apt-get install alien
sudo alien -di nameofpackage.rpm
that will install the rpm, so you can skip to this step 
Disable or delete dabusb module:
If /etc/hotplug/blacklist exists, edit it and add a line containing the word 'dabusb' (without the quotes) to it. Restart Linux.
Otherwise, type :
# modprobe -r dabusb && rm -f $(modprobe -l | grep dabusb) && depmod -a

---

### Post by Sonic Alpha on 2006-07-09
I tried the first step but got the following message from the terminal box: -

E: Couldn't find package alien

---

### Post by christhemonkey on 2006-07-09
```
sudo dpkg -i alien 
```

It should install it fine.
If not check your repositories 
```
gksudo gedit /etc/apt/sources.list
```
And make sure they are all uncommented (#s are comments)

---

### Post by Sonic Alpha on 2006-07-09
> **christhemonkey said:**
> ```
sudo dpkg -i alien 
```

It should install it fine.
If not check your repositories 
```
gksudo gedit /etc/apt/sources.list
```
And make sure they are all uncommented (#s are comments)

Thanks, I tried your steps, and still no luck :(

[QUOTE=Error Text]dpkg: error processing alien (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 alien[/QUOTE]

-------

[QUOTE=source file]deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[/QUOTE]

---

### Post by christhemonkey on 2006-07-09
Sorry stupid me.
Not dpkg, apt-get
```
sudo apt-get install alien
```
*Should* work and install alien.


And maybe you should change all the gb.archive to just archive;
```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted 
```

It may be because the ubuntu gb servers havent been synced recently.

---

### Post by Sonic Alpha on 2006-07-09
> **christhemonkey said:**
> Sorry stupid me.
Not dpkg, apt-get
```
sudo apt-get install alien
```
*Should* work and install alien.

I tried that after the first post, it didn't work :(

---

### Post by christhemonkey on 2006-07-09
Did you try the second bit of my post?
(it was an edit, didnt think about it till i posted that)


PS My 700th post!

---

### Post by Sonic Alpha on 2006-07-09
Doesn't that assume I'm already connected to the net with ubuntu?

---

### Post by christhemonkey on 2006-07-09
Aaah.
Yes it does.

But how did you get the rpm and google for it in the first place?

If its with a different pc, the just visit packages.ubuntu.com and search for alien and download it and all of its dependencies (listed below it).
Dont forget to get the dependencies of the dependencies and so on... :D

Then copy all the files onto a usbstick or something and do this:
```
cd /media/usbdisk/folderwithpackagesin/
sudo dpkg -i ./*.deb 
```

[http://packages.ubuntu.com/dapper/admin/alien](http://packages.ubuntu.com/dapper/admin/alien)

---

### Post by Sonic Alpha on 2006-07-09
I'm dual booting with XP, which means I can still connect to the net ;)

Is the package on the CD?

---

### Post by christhemonkey on 2006-07-09
Well, if you have the cd added as a repository, then you can check.

I cant seem to find a list of the default installed packages anywhere!
Probably just my bad googleing.

---

### Post by Sonic Alpha on 2006-07-09
lol, well I tried downloading the alien package as you suggested.

[QUOTE=Error Report]Selecting previously deselected package alien.
(Reading database ... 69523 files and directories currently installed.)
Unpacking alien (from ./alien_8.64_all.deb) ...
dpkg: dependency problems prevent configuration of alien:
 alien depends on debhelper (>= 3); however:
  Package debhelper is not installed.
 alien depends on rpm (>= 2.4.4-2); however:
  Package rpm is not installed.
 alien depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 alien depends on make; however:
  Package make is not installed.
dpkg: error processing alien (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 alien
[/QUOTE]

I'm just not having a good day, huh? :lol:

---

### Post by christhemonkey on 2006-07-09
As i said you need to download all the listed dependencies!

---

### Post by Sonic Alpha on 2006-07-09
D'oh, I missed that line.  I'll get right on it and let you know how it goes.

Thanks for all your help :)

---

### Post by christhemonkey on 2006-07-09
No problem. Let us know if it is ok.

---

### Post by Sonic Alpha on 2006-07-09
Eventually got it all working.  Thanks a lot for all your time and patience.


My only problem now is that I can't seem to enter an empty password for my internet account (this was default from the service provider, and I don't think I can change it).

---

