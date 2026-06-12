---
title: "Compiz Fusion on PowerBook G4"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by Apple Guy on 2008-04-25
I just installed Hardy Heron PPC on my PowerBook G4.  I would like to enable the desktop effects but can't find the driver.

Every time I try to enable it, it just says "Desktop Effects could not be Enabled"

On 7.10 it had the driver preinstalled or something (it worked right after the install)
------------------------------------------------------------------------------------------------------
My Specs are:
1.5 GHz PowerPC G4
2 GB of RAM
32 MB VRAM
ATI Mobility Radeon 9600
------------------------------------------------------------------------------------------------------
I hope you guys can help!:)

---

### Post by Rocket2DMn on 2008-04-25
I don't have any experience dealing with Apples, but here is a short guide to enabling Compiz if you have the open source ati drivers: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
If you run
```
compiz --replace
``` right now and it tells you it's aborting because you have open source ati drivers, then that is the problem and can likely be fixed by the link above.  It would look something like this:
```
Checking for Xgl: not present.
Found laptop using ati driver.
aborting and using fallback: /usr/bin/metacity
```

---

### Post by Apple Guy on 2008-04-25
Ok, I got Compiz working.  But it's as slow as hell!!!

On 7.10 it was wicked fast!  Is there any way to get the same speed on 8.04?

---

### Post by Rocket2DMn on 2008-04-25
I'm still trying to figure out the new X server in Hardy.  You can post your xorg.conf file, but I don't think there will be anything useful there since the new version of X relies more on autodetection.
```
cat /etc/X11/xorg.conf
```
Your card is borderline on which driver you can use.  Go to System->Administration->Hardware Drivers and see if it wants to use restricted drivers for your card.  If so, give them a try.

---

### Post by Apple Guy on 2008-04-25
> **Rocket2DMn said:**
> I'm still trying to figure out the new X server in Hardy.  You can post your xorg.conf file, but I don't think there will be anything useful there since the new version of X relies more on autodetection.
```
cat /etc/X11/xorg.conf
```
Your card is borderline on which driver you can use.  Go to System->Administration->Hardware Drivers and see if it wants to use restricted drivers for your card.  If so, give them a try.

I will try that tomorrow.  I just turned it off and it takes a few minutes to boot up and such.  I'm too inpatient right now

---

### Post by Apple Guy on 2008-05-02
I still can't get very fast framerates.

Certain things work very well such as the cube effect.  But any window effects are very choppy.  Anyone know how to fix this?

---

### Post by Rocket2DMn on 2008-05-02
I don't know how to fix the problem, but you can disable the effects that don't work correctly.  Install the configuration tool for compiz (if you haven't already)
```
sudo apt-get install compizconfig-settings-manager
```
then you can access it from System->Preferences->Advanced Desktop Effects Settings.  From here you can disable what doesn't work.  A number of other users have been claiming problems with 9600 cards, so it seems to be a generalized problem, not specific to your computer or the fact that it is an apple.

---

### Post by Apple Guy on 2008-05-02
Does anyone else know how to fix this?  What I don't understand is why it worked perfectly on 7.10 and not on 8.04.

I would go back but I had the issue where all the windows appear in the upper left hand corner.

Actually I will go back and check the Xorg.conf and what driver it is using.  That might help!  I will post back soon with results

---

### Post by Apple Guy on 2008-05-02
That didn't help.  I just used the live cd and took the xorg from that.  The effects work on that.

Can you tell me how to downgrade compiz to 0.6.2.  I think that might work

---

### Post by Rocket2DMn on 2008-05-02
Normally you go to Synaptic Package Manager, search for compiz, select it and go to Package->Force Version.  However, it doesn't seem to be allowing me to do that.  You may be able to if you uninstall it first, then force the version you want.  Otherwise, you may have to install that compiz version manually.
If that version is not available for Hardy, you may have to enable repos for Gutsy and force the version from there.  DON'T FORGET to disable that repo when you are done.  While it is available, do not run apt-get upgrade or install any other packages.

---

### Post by Apple Guy on 2008-05-02
How do I enable gutsy repos?

---

### Post by Apple Guy on 2008-05-02
You there still?  How do you enable the Gutsy repos to get the 0.6.2 version?

---

### Post by Apple Guy on 2008-05-02
If you don't answer soon I am about to wipe out Ubuntu for good on my PowerBook.  Maybe it just won't ever work.  I have it on my iMac and it works perfectly.  I don't even know why I put it on there in the first place

---

### Post by Apple Guy on 2008-05-02
I'm uninstalling...now!

Sorry but I'm tired of all the problems.  But I still have ubuntu on my iMac!

---

### Post by cyberdork33 on 2008-05-03
> **Apple Guy said:**
> If you don't answer soon I am about to wipe out Ubuntu for good on my PowerBook.  Maybe it just won't ever work.  I have it on my iMac and it works perfectly.  I don't even know why I put it on there in the first place
too bad. sorry you were so impatient.

---

### Post by Rocket2DMn on 2008-05-03
> **Apple Guy said:**
> I'm uninstalling...now!

Sorry but I'm tired of all the problems.  But I still have ubuntu on my iMac!

Sorry I couldn't get back to you sooner, I can't be on the forums 24/7.  Nobody here is going to try and force you to use Ubuntu, you should use whatever works for you.  Sorry we couldn't nail down the problem, best of luck in your computer adventures!

---

### Post by stream303 on 2008-05-03
> **Apple Guy said:**
> Sorry but I'm tired of all the problems.  But I still have ubuntu on my iMac!

We've all been there - believe me.  It's a shame that nvidia and ati don't make it easier for the devs by providing all the necessary info about their ppc cards - or so I'm told.

Anyway, take a break, and if you come back, check this out - maybe something here can get things back on track:

[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

I'm reminded something of a spirit that existed during my dial-up BBS days on Fidonet when I was running a node in the late 80's - early 90's timeframe, (on a Mac-512K no less) and kind of relates to the Ubuntu spirit, only in a very raw form:

"Don't Be Annoying" - and conversely, and *just as important* - "Don't Be Easily Annoyed"

I have forgotten both of these time and again since we are all human.  Hope to see you back.

---

### Post by ssam on 2008-05-03
in hardy the compiz startup script stops if it finds a mobile radeon card.
[http://ubuntuforums.org/showthread.php?t=762885](http://ubuntuforums.org/showthread.php?t=762885)

the slowness may be due exa not being enabled. see which of these 2 commands give output

```

grep -i exa /var/log/Xorg.0.log
grep -i xaa /var/log/Xorg.0.log

```

to enable exa, you need to edit the device section of the xorg.conf. add the line
```

Option "AccelMethod" "exa"

```

---

### Post by Apple Guy on 2008-05-03
> **ssam said:**
> in hardy the compiz startup script stops if it finds a mobile radeon card.
[http://ubuntuforums.org/showthread.php?t=762885](http://ubuntuforums.org/showthread.php?t=762885)

the slowness may be due exa not being enabled. see which of these 2 commands give output

```

grep -i exa /var/log/Xorg.0.log
grep -i xaa /var/log/Xorg.0.log

```

to enable exa, you need to edit the device section of the xorg.conf. add the line
```

Option "AccelMethod" "exa"

```

If this works I'll reinstall!  I'll try it on the live cd now

---

### Post by SunnyRabbiera on 2008-05-03
Remember with ubuntu power PC was dropped, in fact many distributions have dropped support for Power PC.
perhaps for your Powerbook you should try debian instead and dont use desktop effects.
Your other Mac might be fine as it's probably a intel mac.

---

### Post by Apple Guy on 2008-05-03
Didn't work.  Sorry

---

### Post by ssam on 2008-05-03
did you restart the X server after editing the xorg.conf?

@SunnyRabbiera,
ubuntu have not dropped powerpc. the have stopped official support, and moved the ISOs and debs to the ports server. hardy is a pretty good release on powerpc. there is good community here (should get better if the mod split powerpc and macintels back into separate forums).

---

### Post by stream303 on 2008-05-03
> **SunnyRabbiera said:**
> Remember with ubuntu power PC was dropped, in fact many distributions have dropped support for Power PC.

Testing my Ubuntu spirit, right? :)

As a Debian-Lenny user on my G5 iMac, you might find it odd that I can say touting only the "corporate" line from Canonical in no way helps those of us that want to run the "community" (aka users AND devs) versions of Ubuntu which are readily available.

By all means try Debian, Gentoo, Fedora, and all the others that provide *community-based* ppc support, but I think it would be of little use to say that all their problems would be solved by just jumping to another distro.

As an example, let's take a look at the Debian-PPC port archives:
[http://lists.debian.org/debian-powerpc/2008/03/threads.html](http://lists.debian.org/debian-powerpc/2008/03/threads.html)

Enough has been said on this topic that there is no need to continue, and I'm sure that many are pretty tired of reading the same old arguments over and over.

Please, as a Debian-user, it does not help the ppc community *as a whole* to merely state that jumping to another distro will magically fix all your problems.  We need unity, NOT division.

---

