---
title: "Desktop effects and Nvidia driver issues"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by screamindaemon on 2008-03-29
Hi there.  I am a brand spanking new user, and this is my first post.

I loaded Ubuntu off of a live disk, and there were no issues in installation.

I'm currently trying to enable desktop effects, and whenever I click 'yes' to enabling the driver, nothing happens.  It tells me to run desktop effects again after restarting.  I restart, and nothing changes.

I even go to the hardware manager to enable the driver, and nothing happens.  

Do I have faulty hardware?  Can anybody give me a hand please?

Thanks
-Cam

---

### Post by virtuallinux on 2008-03-29
Which model of card do you have?

---

### Post by screamindaemon on 2008-03-29
Oh sorry, that probably would have been useful.  It's Nvidia GeForce4 420

---

### Post by virtuallinux on 2008-03-29
When you say you've enabled drivers, do you mean that you've done it with the restricted drivers manager? (System > Administration > Restricted Drivers Manager)

---

### Post by virtuallinux on 2008-03-29
Well, turns out I'm headed to bed, and it may be a while before I'm back. Hopefully I can pick this up tomorrow or someone else can pick this up where I left of (which admittedly wasn't very far).

---

### Post by screamindaemon on 2008-03-29
Yes, that's correct.    It's status is "Not in use".  And when I try to enable it, it returns to that screen of "Enable the driver?"  To which I click yes to, and nothing changes.  Even after multiple reboots.

---

### Post by PmDematagoda on 2008-03-29
Can you please post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by screamindaemon on 2008-03-29
cameron@cameron-laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by PmDematagoda on 2008-03-29
Could you please the specifications of your VGA card.

---

### Post by screamindaemon on 2008-03-29
GeForce4 4200 Go     Fill Rate:                             1.6 billion texels/sec.
                                       GPU Core Clock:               200 MHz
                                       Memory Clock :                 200 MHz
                                       Memory Bandwidth:         6.4GB/sec.
                                       Memory:                             32MB

---

### Post by m60dude5 on 2008-03-29
Don't do this yet, but someone correct me if I'm wrong, doesn't he need to download the xgl (or whatever they are) restricted drivers for an Nvidia card? 

If you open the appearance settings, and click the visual effects tab there are some radio buttons with options. Click the one that says extra and it should ask you if you want to download the xgl drivers. Click yes, and if you have internet connection, it should install them for you. Then restart.

---

### Post by virtuallinux on 2008-03-29
Well, it looks to be an older card, and I'm not sure which cards are actually supported by the Nvidia restricted drivers.  So that could be the problem.

---

### Post by m60dude5 on 2008-03-29
True. With only 32 MB of gpu memory, you may not be able to use advanced effects.

---

### Post by Cope57 on 2008-03-29
Here is your legacy driver you would need.

[http://www.nvidia.com/object/linux_display_x86_96.43.05.html](http://www.nvidia.com/object/linux_display_x86_96.43.05.html)

But as for some effects, it is highly unlikely you would get to much better than a default XP install without drivers.

Since the video card you have is legacy based, maybe switching to a minimal desktop environment might be better for you. FVWM-Crystal, XPde, EDE, and others to choose from. Or you could just use a different window manager like [THESE](http://www.linux.org/apps/all/GUI/Window_Managers.html).

---

