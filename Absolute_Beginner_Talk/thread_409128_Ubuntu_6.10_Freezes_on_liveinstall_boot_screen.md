---
title: "Ubuntu 6.10 Freezes on live/install boot screen"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by redsfans4 on 2007-04-14
Hi,

When I boot from the live CD, it freezes at the screen where the orange thing is going back and forth, it goes from right to left, left to right the on the third round or whatever, it freezes a little before midway point but doesn't move (I left my PC on all night and when I got up it was still there.)

MD5 for the ISO download checked out.  Burned the CD at 8X on Windows Using Infra Recorder on Memorex media.  I'm pretty sure by now It's not the CD, since this is the fifth burn I've done, twice on Generic Media, twice on HP Media and first on Memorex.  CD Check checks out fine.  This doesn't happen to me on 6.04 or 7.04, however using 7.04 really isn't an option as my video drivers aren't supported yet and I need them to play Counter-Strike: Source in crossover.  I'd prefer not to have to use 6.04 because 6.10 is better supported here at least it seems to me and my drivers are supported in 6.10.  If there is a way I can upgrade from 6.04 to 6.10 without having to boot from CD, I could try that.

PC Specs:

eMachines W3400

AMD Athlon 64 3000+

512MB RAM

ATI Radeon Xpress 200 128MB Shared Integrated Graphics

I'm using 32 Bit Ubuntu because it seems better supported, some things don't run on 64 Bit I think.

Any help is appreciated.

Thanks.

---

### Post by metol on 2007-04-14
I had problems with my 6.10 Live/CD during installation.  I was able to install 6.06 though.  So, I just installed 6.06 and updated to 6.10 using:

```
gksu "update-manager -c"
```

There is a community doc on upgrading [here]("https://help.ubuntu.com/community/EdgyUpgrades") There is probably a more graceful approach to do this, but I am a noob.

---

### Post by redsfans4 on 2007-04-14
> **metol said:**
> I had problems with my 6.10 Live/CD during installation.  I was able to install 6.06 though.  So, I just installed 6.06 and updated to 6.10 using:

```
gksu "update-manager -c"
```

There is a community doc on upgrading [here]("https://help.ubuntu.com/community/EdgyUpgrades") There is probably a more graceful approach to do this, but I am a noob.

Thank you for the help![http://ubuntuforums.org/newreply.php?do=newreply&p=2451780](http://ubuntuforums.org/newreply.php?do=newreply&p=2451780)
Ubuntu Forums - Reply to Topic

Unfortunately

```
gksu "update-manager -c"
```

Kept telling me I was up to date, but I clicked on your link for the upgrade document and inserted my CD and ran:

```
gksu "sh /cdrom/cdromupgrade"
```

Ubuntu is upgrading as we speak!

Thanks for the help, will report back if it was successful or not or if I had problems.

---

