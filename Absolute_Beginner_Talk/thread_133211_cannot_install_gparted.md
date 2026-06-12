---
title: "cannot install gparted"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by regiemon on 2006-02-19
how do i install gparted?

if i click add applications then check the gparted,

error says that the application cannot be found in your archive.this usually means that it is not available for your hardware platform.

any advices? thank you.

---

### Post by regiemon on 2006-02-19
when i type 
sudo apt-get install gparted

error says: coudn't find package gparted.

---

### Post by SickTwist on 2006-02-19
[QUOTE=regiemon]when i type 
sudo apt-get install gparted

error says: coudn't find package gparted.[/QUOTE]

Try running this first to get an updated list of all the available packages:
[B]
sudo apt-get update[/B]

Then try to install it again:
[B]
sudo apt-get install gparted[/B]

If that doesn't work, run this command and show us the output:
[B]
cat /etc/apt/sources.list[/B]

---

### Post by regiemon on 2006-02-19
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe


what the problem? because i couldnt install gparted.i cant partition my hard drive so i could install windows xp.

---

### Post by SickTwist on 2006-02-19
You have almost every repository disabled. Is there a reason for that? Do you have Internet access on the Ubuntu machine?

If you do have Internet access on the Ubuntu machine, type this command:

**sudo gedit /etc/apt/sources.list**

And make it look like this:

```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://ph.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

## breezy updates
deb http://ph.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

## backports
# deb http://ph.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://ph.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## security updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted universe multiverse
```

Save the file and close gedit. Then update your package list again:

**sudo apt-get update**

And try to install again:

**sudo apt-get install gparted**

---

### Post by regiemon on 2006-02-20
ok now.i already installed the gparted.thank you very much.

but how do i use this.because i want to create a new partition but i click partition menu the new button is gray and cannot be click.why is that?

---

### Post by Herman on 2006-02-20
It might be because you have not yet selected an area of free space for you new partition to go.
If you just right-click on an area of free space you should get a right-click menu with the 'New' option activated.

If you have no free space on your disk you may need to resize (shrink) one of other partitions to leave an area of free space vacant for creating your new partition on.
Your Windows partition is a perfect choice. :-D
You may need to unmount it first though, the option for that is also on the right-click menu.

If it is your Ubuntu partition itself that you need to resize, you will need to use GParted on the Breezy live CD to do that with, or GParted on its own live CD. (because you can't unmount the partition while it is being used).
Happy Gpartitioning! :-D (Herman)

---

### Post by SickTwist on 2006-02-20
I agree -- it's probably a better idea to edit partitions from a live CD if you are trying to edit partitions on the same drive on which Ubuntu is installed.

Gparted can be installed the same way on the Ubuntu live CD (although it is just installed temporarily in RAM) or follow Herman's suggestion and try the official [Gparted live CD]("http://gparted.sourceforge.net/livecd.php").

---

### Post by regiemon on 2006-02-20
thank you very much guys....

---

