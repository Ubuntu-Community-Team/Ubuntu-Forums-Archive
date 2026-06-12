---
title: "Completely remove kde4 stable"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-01-13
I need to know.

I use ubuntugeek.com instructions to install the kde4-core and I also installed "aptitude install kde4" (all the rest of the programs).

Since alot of programs crash and the bottom panel (kicker?) isn't viewable I want to remove every single piece of it to try an clean reinstall.

How should I do that?

(it needs to be 100% gone)

---

### Post by billgoldberg on 2008-01-13
bump

---

### Post by maya9 on 2008-01-13
I had a similar problem and was helped by this post by TBerben:
------------------------------------------------------
Removing kubuntu-desktop will not result in removing KDE 4 from your computer as kubuntu-desktop depends on the KDE 3 packages. To remove KDE 4 remove the KDE 4 ppa repository from /etc/apt/sources.list and run:
Code:

sudo aptitude remove kde4-core kdm-kde4

that should remove the KDE 4 core packages, to make sure you've got everything gone run:
Code:

aptitude search kde4

And make sure that none of the packages with 'kde4' in the name have an i in front of their names.

Then run:
Code:

sudo dpkg-reconfigure gdm

To give you the menu in which you can choose your session manager

-----------------------------------------------
Perhaps it will help you.

---

### Post by SOULRiDER on 2008-01-13
Just do
```
 sudo aptitude purge kde4 kde4-core
```

---

### Post by kinkdxm on 2008-01-20
> **maya9 said:**
> I had a similar problem and was helped by this post by TBerben:
------------------------------------------------------
Removing kubuntu-desktop will not result in removing KDE 4 from your computer as kubuntu-desktop depends on the KDE 3 packages. To remove KDE 4 remove the KDE 4 ppa repository from /etc/apt/sources.list and run:
Code:

sudo aptitude remove kde4-core kdm-kde4

that should remove the KDE 4 core packages, to make sure you've got everything gone run:
Code:

aptitude search kde4

And make sure that none of the packages with 'kde4' in the name have an i in front of their names.

thanks seems to run great.
i also ran
```
sudo aptitude update
sudo aptitude upgrade
```
after

---

### Post by rosegarden78 on 2008-01-20
> **billgoldberg said:**
> I need to know.

I use ubuntugeek.com instructions to install the kde4-core and I also installed "aptitude install kde4" (all the rest of the programs).

Since alot of programs crash and the bottom panel (kicker?) isn't viewable I want to remove every single piece of it to try an clean reinstall.

How should I do that?

(it needs to be 100% gone)

It sounds like you messed up something.  I prefer clean installs rather than hair-pulling and climbing the walls all night.  It sounds like your kernel and software is obsolete.  Backup your /home folder and any other partitions you use for storage.

When you burn an Ubuntu Gutsy Gibbon 7,10 disc - ITS CRUCIAL TO USE THE SLOWEST BURN SPEED OR 4X.  Otherwise you will get errors from shallow pits regardless of the checksum.

Always install Windows or OSX before Ubuntu to dual-boot.

It's messed up good don't bother fixing it.  I think mine says KDE 3.5 and that's the standard right now I guess.  I'll tell you what I did:

1)  I installed Ubuntu Gutsy first
2)  I typed 
  sudo aptitude install kde 
  or added KDE from Synaptic.
3)  I installed XFCE from Synaptic.

Don't worry about disk space.  It's better to have GNOME, KDE and XFCE installed than to risk program errors due to missing dependencies.  Personally, I use XFCE as default session then load "nautilus" on Startup.  That's my fastest environment.

---

### Post by kinkdxm on 2008-01-20
I checked out the live cd and liked it of kde4
then I found this
[http://www.kubuntu.org/announcements/kde4-rc2.php](http://www.kubuntu.org/announcements/kde4-rc2.php)
which said how to install it in ubuntu.
it was horrible.

---

### Post by lucky.developer on 2008-07-16
hey.. installed kde4 and then again removed(i guess so) it some hours after the install cos i didn't like it.
but when i run 

'sudo-dpkg-reconfigure gdm'

the following message comes

 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.


is anything wrong here ? if yes.. what shoud i do?

---

### Post by Reiger on 2008-07-16
Depends. If the gdm thing does its job OK regardless... *shrugs*

Anyway, if you must (and you need to have ethernet connection for that or have your /etc/apt sources.list file set up to include (is commented out by default IIRC) the ISO image you used to install *buntu with) you can still do:
```

sudo aptitude purge ubuntu-desktop
sudo aptitude install ubuntu-desktop

```

Right?

---

