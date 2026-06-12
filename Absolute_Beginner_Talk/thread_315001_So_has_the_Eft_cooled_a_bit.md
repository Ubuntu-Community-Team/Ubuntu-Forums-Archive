---
title: "So has the Eft cooled a bit?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by cdi3d on 2006-12-08
Finally managed to upgrade my laptops HDD and now I have Kubuntu Dapper working on it nice and proper. 

During the interim however apparently Edgy was released. I did a bit of looking (and read the link here: [http://www.ubuntuforums.org/showthread.php?t=286209](http://www.ubuntuforums.org/showthread.php?t=286209)) and found that the upgrade has a lot of issues. Still being a newbie to *buntu Im more than a bit hesitant about upgrading. 

Has the Edgy upgrade smoothed out now? If so is Aptitude the recommended app for the upgrade?

Thanks for any assist.

---

### Post by taurus on 2006-12-08
If you want to upgrade from Dapper to Edgy, follow this guide...

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by _simon_ on 2006-12-08
I think the least problematic way to "upgrade" is to do a fresh install, in fact that way should be problem free.

Personally I always do a fresh install, to be sure everything will (hopefully) work!

---

### Post by cdi3d on 2006-12-08
Ah ha. Ok. Ill try and burn an ISO before I leave work. Thanks.

---

### Post by P235 on 2006-12-08
I am already using Edgy, but hypothetically, when the next release comes out and I decide sometime afterwards to upgrade via ISO CD how would I go about it?  I have /home on a separate partition so could I just tell the installer to clear out the '/' partition only?  Also, how do you back up '/' just in case an upgrade doesn't work out?

---

### Post by taurus on 2006-12-08
Just tell installer to format / but mount whatever partition $HOME is to /home, without formatting.  That why, you can keep all your personal settings.  And if you need to back up the system, you probably only need to backup the /etc directory...

---

### Post by P235 on 2006-12-08
I see, do I have to worry about file permissions?  I think I read somewhere that you have to add users in the same order they were added before or else the file permissions will be messed up.

---

### Post by taurus on 2006-12-08
Nope.  Just create the same user during installing and you are all set with permissions and everything.

---

### Post by brt on 2006-12-08
hmmm i was doing upgrades keeping all my settings from warty->hoary->breezy->edgy

well sometimes there were issues with upgrades but mostly it was because i had installed something which didnt came with the official repos. like binary nvidia driver, so e.g. once X didnt start up after the upgrade, but i was always able to fix the problem from command line. (or using live cd browsing ubuntuforums for the problem)

once i also did a fully reinstall like this:

sudo dpkg --get-selections > pkg.list

this makes a textfile with all your installed packages, save it to a place which will not be wiped during the install.
(you may also edit the file and remove some lines for some particular packages if you do not want them to be installed)

i put /home on a seperate partition so it wont be wiped during an install. this is were i also place the packagelistfile.

you may do also a backup of your /etc folder so you can easyly restore things you have changed there.

after you have installed you new ubuntu just mount your home partition and: 

sudo dpkg --set-selections < pkg.list

sudo aptitude dist-upgrade

and the system will reinstall any software you had installed before and all your settings will be just like you had them before. if you want some personal program settings to be reset to the default just remove the hidden configuration folder/files in your home directory, e.g. using: rm -r ~/.gnome* if you want to delete your old gnome configuration.

well i really like to mess around with my system and sometimes it was really bad. in the beginning of my linux experience i also used to do it the "fresh install from scratch" way, but with the time i noticed that it is not needed in most cases.

if you ever mess up your system, try to add a new user and login. if the problem is fixed within the new users account try moving settings directories from your homefolder (the hidden ones with the dot at the beginning) to a backup dstination and see if it fixes the problem.

---

### Post by P235 on 2006-12-08
Thanks, upgrades don't seem too daunting anymore.  I was a tad curious when I read of people having difficulties with apt or the gksu "update-manager -c" command.

---

### Post by redDEADresolve on 2006-12-08
There are no real advantages of upgrading to edgy if you don't have too.
I've experienced more problems in Edgy then I did in Dapper.
I didn't need to upgrade but I did, now I'm thinking of going back to Dapper.

P.S. Fresh Install is the best way to go hands down.

---

### Post by BackInTimeMan on 2006-12-08
> **taurus said:**
> 

[...]

And if you need to back up the system, you probably only need to backup the /etc directory...

I'm puzzled by this statement taurus, maybe I'm misunderstanding what you mean but would you explain how backing up the /etc directory would back up the entire system?

---

### Post by P235 on 2006-12-09
I started with 6.10 so I can't say if 6.06 is more stable, but I can say that when 6.10 is misbehaving it requires several restarts before it runs properly again.  Sometimes my laptop freezes completely, leaving me no other choice but to pull the power.  Yes, it's one of the great sins I'd rather not do, but I have little choice when I need to use it.  

However, as an upgrade no longer sounds difficult, I can theoretically downgrade my laptop with the same procedure?

---

### Post by andb on 2007-03-07
Backintimeman,

Probably the reason that taurus recommends backing up the /etc dir is that while it is easy to reinstall the packages that you previously had, it is tedious to properly configure them again. You'll find all of your configs either in your home directory or in /etc (I really cant think of an exception, if there is, let me know...) As brt said, sudo dpkg --get-selections > pkg.list will give you a file that you can use to rebuild your whole system really fast, add /etc and you have system-wide configs that you've done (like your firewall, samba shares, ssh setup, etc) and with your home directory for your user configs and data, and you ave your system back. Unless you are doing some crazy compiling from source,   /etc , ~/ and package list will give you your system back in the event of a system failure.

---

