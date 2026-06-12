---
title: "Problem upgrading from 7.04 to 7.10"
date: 2008-03-30
forum: Apple PPC Users
---

### Post by LaSelvaBeach on 2008-03-30
Howdy again,

I checked out quite a few other forums that mention this, but none seem to really touch on what's going on in my scenario.  I'm running Xubuntu 7.04 on my G3 iMac.

When I go into the system -- updates and click on the update to 7.10 button, the update starts out okay.  While in the "modification of repositories" (excuse the bizarre translations if they're there, my system is in french) the status bar says downloading 49 of 60 files and just stops there indefinitely (well, the longest that I've waited for it thus far is around 40 minutes).  When I click on the cancel button and try to start over (or restart/shut off my computer) i get the following message:

"Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://ports.ubuntu.com/dists/gutsy/Release.gpg](http://ports.ubuntu.com/dists/gutsy/Release.gpg) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy/main/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy/main/i18n/Translation-fr.bz2) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy/universe/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy/universe/i18n/Translation-fr.bz2) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy/multiverse/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy/multiverse/i18n/Translation-fr.bz2) 
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-updates/Release.gpg](http://ports.ubuntu.com/dists/gutsy-updates/Release.gpg) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-updates/main/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy-updates/main/i18n/Translation-fr.bz2) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-updates/main/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy-updates/main/i18n/Translation-fr.bz2) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-updates/multiverse/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy-updates/multiverse/i18n/Translation-fr.bz2) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-updates/universe/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy-updates/universe/i18n/Translation-fr.bz2) 
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-security/Release.gpg](http://ports.ubuntu.com/dists/gutsy-security/Release.gpg) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-security/main/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy-security/main/i18n/Translation-fr.bz2) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-security/universe/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy-security/universe/i18n/Translation-fr.bz2) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-security/multiverse/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy-security/multiverse/i18n/Translation-fr.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-backports/Release.gpg](http://ports.ubuntu.com/dists/gutsy-backports/Release.gpg) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-backports/main/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy-backports/main/i18n/Translation-fr.bz2) 
Failed to fetch [http://ports.ubuntu.com/dists/gutsy-backports/multiverse/i18n/Translation-fr.bz2](http://ports.ubuntu.com/dists/gutsy-backports/multiverse/i18n/Translation-fr.bz2) 
Failed to fetch http://ports.ubuntu.com/dists/gutsy-backports/universe/i18n/Translation-fr.bz2"

I think that I may be missing something.  I am new to this...

thanks!

---

### Post by LaSelvaBeach on 2008-03-31
ah well, I just switched my xubuntu to Ubuntu and did the updates through that.  worked fine.

---

### Post by Midwest-Linux on 2008-04-02
I also upgraded from 7.04 to 7.10 and I am stuck at initramfs. 7.10 won't work on this, guess I'll have to re-install 7.04. I am using a IMac PPC slot loader.

---

### Post by avtolle on 2008-04-02
Hey, Midwest, have you tried: at the prompt:
```
 modprobe ide-core
exit

``` 
to see if your machine will continue booting? I

---

### Post by Midwest-Linux on 2008-04-03
> **avtolle said:**
> Hey, Midwest, have you tried: at the prompt:
```
 modprobe ide-core
exit

``` 
to see if your machine will continue booting? I

 I first tried to upgrade directly without the disc...updating directly, after the upgrade I ended up in busy box at initramfs. I didn't mess around further ..so then I'd stop there and just did a fresh new install using the 7.10 alternate text installer, so I wiped the hard drive and did a fresh install of 7.10.

After all that  I ended up again at busy box with the initramfs. Did some looking around , saw something about the date bug issue (my computer says 1903... yes dead battery but why should that affect 7.10 but not 7.04 ?) 

Tried the mod-core ide. And other commands including trying  to reset the time. I had to walk away from it and now reinstalling 7.04 and I am leaving it at Feisty. Right now I don't have time to sort out all this out. 

 I only tried to upgrade because I was unable to enable the Flash plug ins in Firefox with 7.04 so I could watch some streaming video.  I clicked the Firefox prompt for the plugins and could not install flash. I thought maybe with 7.10 I would be able to get flash or watch some videos. I didn't have this problem with Linux Mint 4.0 or Freespire 2.0.

 I wish I had more time to devote right now to try to resolve this. But I wanted to use this G3 I-Mac slot loader in another part of the house to  do basic internet functions watch some streaming video or you tube stuff. Its not a priority that I use this machine, I have a spare PC with Linux that I could use instead,... but the built in monitor with the I-Mac makes it a bit easier since I wouldn't have to use a extra monitor with it.

---

### Post by megarner on 2008-04-03
Hi Midwest--I too have a Imac slot loader.  I updated from 7.04 to 7.10 and got the same symptoms you described but after using: modprobe ide-core  followed by: exit when that was done caused the gui to load and I'm back in business with 7.10.

---

### Post by stream303 on 2008-04-03
To make that ide-core permanent so you don't have to go through this all the time, be sure to:

```
sudo update-initramfs -u
```

and you should be good to go from there on out...

---

### Post by Midwest-Linux on 2008-04-03
> **stream303 said:**
> To make that ide-core permanent so you don't have to go through this all the time, be sure to:

```
sudo update-initramfs -u
```

and you should be good to go from there on out...

 From what I have read so far, flash is a problem with Ubuntu PPC. But no problem with Ubuntu on PC's. I read about installing GNASH as a possible substitute for flash on PPC. Before I attempt that approach, maybe I need to see more threads on it before I even attempt it.


 So now my question is... should I do the (sudo update-initramfs -u ) before I attempt another 7.10 PPC installation? Or after, when the busybox initramfs bug shows up?

 Does the "time bug" really make that much of a difference with 7.10? Does not affect installation of 7.04 at all.

 If anyone asks How come I don't just wait for Hardy and upgrade then. I'd rather do the upgrade through the Ubuntu updates. From what I understand so far...there are two upgrade paths from 7.04.

1. Upgrade to 7.10 and then to 8.04 (from what I read you can't jump from 7.04 to 8.04 unless you do a clean install of 8.04.

2. The other upgrade path of course would be to do a clean new install of 8.04.

 In all cases I use the alternate text installer CD burned at the lowest speed using the best media I could find.

---

### Post by stream303 on 2008-04-04
> **Midwest-Linux said:**
> From what I have read so far, flash is a problem with Ubuntu PPC. But no problem with Ubuntu on PC's. I read about installing GNASH as a possible substitute for flash on PPC.

The gnash devs are working as hard as they can - the best bet for us would probably be to hang in for Hardy release, or be sure to enable the backports repository in software sources and hope for new releases to show.  Results are still not perfect.

> So now my question is... should I do the (sudo update-initramfs -u ) before I attempt another 7.10 PPC installation? Or after, when the busybox initramfs bug shows up?

Only when you need to do any modprobe commands manually, like ide-core to make it permanent.  If it shows up again after an install, you'll know you need to update initramfs just once more again.

> Does the "time bug" really make that much of a difference with 7.10? Does not affect installation of 7.04 at all.

Only if you really have that bug to begin with.  Usually it is a case of a failing motherboard battery.  Don't know why it wouldn't show on Feisty but does on Gutsy for you.

You've got the upgrade path scenario right.  Some would suggest that since Hardy is an LTS that incorporates so many changes, it might be wiser to just do a clean install rather than upgrade so things don't crawl out from under the woodwork months down the road. :)

---

### Post by Midwest-Linux on 2008-04-04
> **stream303 said:**
> The gnash devs are working as hard as they can - the best bet for us would probably be to hang in for Hardy release, or be sure to enable the backports repository in software sources and hope for new releases to show.  Results are still not perfect.



Only when you need to do any modprobe commands manually, like ide-core to make it permanent.  If it shows up again after an install, you'll know you need to update initramfs just once more again.



Only if you really have that bug to begin with.  Usually it is a case of a failing motherboard battery.  Don't know why it wouldn't show on Feisty but does on Gutsy for you.

You've got the upgrade path scenario right.  Some would suggest that since Hardy is an LTS that incorporates so many changes, it might be wiser to just do a clean install rather than upgrade so things don't crawl out from under the woodwork months down the road. :)

 I am going to wait for Hardy, good advice and I will do a clean install with it after I see some  comments on the final release of  Hardy on PPC.  Right now 7.04 is working good for the most part.  I can listen to streaming audio and do pretty much everything except the flash video player. But I have Linux Mint 4.0 on my other PC that can do all that. I appreciate all the work everyone does here on these forums....

---

