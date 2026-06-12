---
title: "Problems with upgrading Ubuntu 6.06"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by obliviousdream on 2008-02-07
Everytime I try to upgrade my Ubuntu, After I put in: gksu "update-manager -c -d" it gives me the option to upgrade to 8.04, but after the "setting new software channels" step I get this error message:

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

Have any ideas about what could be wrong, or any way to update instead of using the CD? (It always stops downloading about halfway through)

---

### Post by bumanie on 2008-02-07
you cannot upgrade more than one distro in front of the one  you are using. You would be best to do a new install of a later distro.

---

### Post by obliviousdream on 2008-02-07
That makes sence...Then how can I choose to upgrade to the next one?

It only gives me the choice to upgrade to 8.06

---

### Post by spiderbatdad on 2008-02-07
of course a working internet connection on the computer being upgraded.

---

### Post by obliviousdream on 2008-02-07
I have an internet connection.

It also tells me I don't have the repositories added, but I added all I could find.

Might that have anything to do with it?

Actually...It won't let me add repositories....>_>

---

### Post by taurus on 2008-02-07
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by obliviousdream on 2008-02-07
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper multiverse universe main restrictedbrent@brent-laptop:~$

That's what I got. Does it help at all?

---

### Post by bodhi.zazen on 2008-02-07
That is not true, there is a plan to allow direct updating 6.06 -> 8.04 (LTS ot LTS)

However, 8.04 is in alpha an I would wait if you are on a production machine.

If you are not on a production machine you need to update 6.06 -> 6.10 -> 7.04 -> 7.10

Like this :

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)
[https://wiki.ubuntu.com/HardyHeron/Alpha4](https://wiki.ubuntu.com/HardyHeron/Alpha4)

If you want to update to 7.10 or 8.04 Alpha, I suggest it will be much easier to backup your data and do a fresh install of 7.10 or 8.04 alpha.

---

### Post by bumanie on 2008-02-07
If you want the next distro after your present one, go here [http://old-releases.ubuntu.com/releases/edgy/](http://old-releases.ubuntu.com/releases/edgy/) The following one from here
[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/) or the present release from here
[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)
If your computer is a few years old, I would personally suggest not going past 7.04. 7.10, although it worked well for many users, there were more difficulties with it than other releases. But that is just my personal opinion. I have an old socket A amd board and 7.10 did work, but it required quite a bit of configuring, whereas, 7.04 worked with ease. The decision is entirely up to you as to which one you try.

---

### Post by obliviousdream on 2008-02-07
I just ran the code to try to upgrade to 6.10, and all it did was open my update manager.

There was no update notice...

@ Bumanie: Do you know of a way to do it without the iso?

---

### Post by bodhi.zazen on 2008-02-07
Look up ^^^

---

### Post by obliviousdream on 2008-02-07
I'm kinda slow....What am I looking for?

---

### Post by bumanie on 2008-02-07
Sorry, I don't. I would think that the iso is probably the only way. Canonical probably can't afford to have all their previous distro's available for upgrades - too much bandwidth and maintenance to keep old distro's active indefinitely. It is also the case that the majority of users upgrade within a couple of weeks of a new release, therefore, there would be minimal demand for 18 months old. In fact your 6.06 is a distro with long term support ie three years. The next release (8.04) will also have three years support. All the distro's in between are limited to 18 months support.

---

### Post by bodhi.zazen on 2008-02-07
My first post, it links to the wiki pages that will walk you through the updates. Manually editing your /etc/apt/sources.list is not advised and the most error prone upgrade will be to Edgy.

---

### Post by obliviousdream on 2008-02-07
Oh! So that's what that is ^_^

Okay. Well, is there anything special I need to do after downloading the ISo and burning it? (I completely wiped my windows xp)


@bodhi.zazen: I tried to use the Update manager code, but all it did was open my Update Manager. It didn't offer an upgrade...

---

### Post by bodhi.zazen on 2008-02-07
Try this :

> Upgrading using Update Manager

If you want to upgrade from 6.06 LTS to 6.10, run the following command (either via ALT-F2 or a terminal):

gksu "update-manager -c" 

The -c (or equivalently --check-dist-upgrades) switch instructs Update Manager to look for upgrades. By default, the Ubuntu 6.06 LTS release will not offer that automatically because of its long support cycle and high stability.

If you have a working network connection, it should then inform you about a new release and offer to upgrade your system.

If you have the Edgy Alternate Install CD (not the Desktop CD), you can save bandwidth by using:

gksu "sh /cdrom/cdromupgrade" 

That gksu "sh /cdrom/cdromupgrade" command may need to be modified, depending on where your cd is monted, to something like

gksu "sh /media/cdrom/cdromupgrade"

Not sure ...

---

### Post by bumanie on 2008-02-07
Just download the iso, right click on it when its finished and select burn to disc. The only precaution is to choose a slow burn speed to reduce the chance of errors, say burn at 4x. You could also check the md5 checksum after download to ensure it was a clean download. This link tells you how to do that 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Let us know how it goes.
PS: bodhi.zazen  seems to know more about this than me re how to upgrade. Personally, I would do a fresh install, but that's up to you. Good Luck.

---

### Post by obliviousdream on 2008-02-07
@bodhi.zazen: I did though. When I typeed: gksu "update-manager -c"  in the terminal, it asked to be granted admin powers (Or whatever it's called...) and then pulls up my Update Manager.

But it says my computer is up to date. There's nothing to install

---

### Post by bumanie on 2008-02-07
If you have the bandwidth available to download an iso, I would still do that. Again, I personally would try 7.04 and then may be wait a couple of months after 8.04 is relesed and if everything seems to be OK with it, then try it as it has long-term support.

---

### Post by obliviousdream on 2008-02-07
Well, I'm gonna try at least.

>_> I think there's something wrong with my repositories though, because everytime I try to add the Universe and the Non-free, they won't save.

They just go back to being un-checked

---

### Post by bodhi.zazen on 2008-02-07
> **obliviousdream said:**
> @bodhi.zazen: I did though. When I typeed: gksu "update-manager -c"  in the terminal, it asked to be granted admin powers (Or whatever it's called...) and then pulls up my Update Manager.

But it says my computer is up to date. There's nothing to install

You can burn the iso to disk, check the integrity, and then put the disk in the CDROM, then try the command I gave you.

If that fails we will need to add the CDROM to your sources list, and can do that via synaptic.

Alternately, if you do not want to burn a disk, you can mount the .iso and try the commands / snyaptic from there :

```
sudo mount -o loop -t iso9660 /path_to/alternate.iso /media/cdrom
```

You may or may not need to make a mount point :

```
sudo mkdir /media/cdrom
```

---

### Post by obliviousdream on 2008-02-07
^_^ Oh, okay.

I think that should work. I'll report back if it doesn't.

Thanks so much!!

---

### Post by bodhi.zazen on 2008-02-07
kk, I gotta run. I will check in later, post if you need further assistance.

---

