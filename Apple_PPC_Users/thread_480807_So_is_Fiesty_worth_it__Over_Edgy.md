---
title: "So is Fiesty worth it?  Over Edgy???"
date: 2007-06-21
forum: Apple PPC Users
---

### Post by magnolia fan on 2007-06-21
As a G4 PPC user running 6.10 with a video card that can't do 3D acceleration, I'm wondering if I should hit that upgrade button I see on the Update Manager.  Is there any benefit in going from a supposedly official and supported version to an unsupported version?  Do I have anything to gain?  Do I have anything to lose?  I would love to hear the thoughts of the PPC community on this.  --thanks

---

### Post by Auria on 2007-06-21
> **magnolia fan said:**
> As a G4 PPC user running 6.10 with a video card that can't do 3D acceleration, I'm wondering if I should hit that upgrade button I see on the Update Manager.  Is there any benefit in going from a supposedly official and supported version to an unsupported version?  Do I have anything to gain?  Do I have anything to lose?  I would love to hear the thoughts of the PPC community on this.  --thanks

It has been reported that many PPC bug have been fixed in the Kernel, which most likely means more stability for you

The support means you can no more call Canonical to get help, that's pretty much all for now

You should always back up important files before update is there is no garantee it will go all fine.

It is unlikely that your graphics card will suddenly be working.

You will have access to more recent versions of applciations in the repositories

hope it helps :)

---

### Post by magnolia fan on 2007-06-21
I don't expect the NVidia card to ever work, so modern GUI advances are out of the question.  I'm also not having a problem with stability.  I would like to have access to package updates, but how will newer versions of applications function with an old Ubuntu distro?  I assume that since the PPC platform is no longer supported there won't be a future version of Ubuntu for the PPC beyond 7.04.  Am I wrong?

---

### Post by stmiller on 2007-06-22
> **magnolia fan said:**
> I don't expect the NVidia card to ever work, so modern GUI advances are out of the question.  I'm also not having a problem with stability.  I would like to have access to package updates, but how will newer versions of applications function with an old Ubuntu distro?  I assume that since the PPC platform is no longer supported there won't be a future version of Ubuntu for the PPC beyond 7.04.  Am I wrong?

This has been discussed at length here. Ubuntu will continue to release PowerPC isos, including package updates, security updates, etc. They dropped technical support. So you cannot call 1-800-xxxxx to get paid support from Canonical. You have to come to this forum.

There is an open source project working on 3D drivers for Nvidia. I suggest you check out their homepage to find out about progress.

[http://nouveau.freedesktop.org/](http://nouveau.freedesktop.org/)

If you /etc/X11/xorg.conf file has 

Driver "nv"

in the devices section, then that is the correct driver to use for now. It is 2D and stable.

---

### Post by jimwg on 2007-06-22
> **magnolia fan said:**
> I don't expect the NVidia card to ever work, so modern GUI advances are out of the question.  I'm also not having a problem with stability.  I would like to have access to package updates, but how will newer versions of applications function with an old Ubuntu distro?  I assume that since the PPC platform is no longer supported there won't be a future version of Ubuntu for the PPC beyond 7.04.  Am I wrong?

Well, there's always Leopard... :)

James Greenidge

---

### Post by Auria on 2007-06-22
> **magnolia fan said:**
> I don't expect the NVidia card to ever work, so modern GUI advances are out of the question.  I'm also not having a problem with stability.  I would like to have access to package updates, but how will newer versions of applications function with an old Ubuntu distro?  I assume that since the PPC platform is no longer supported there won't be a future version of Ubuntu for the PPC beyond 7.04.  Am I wrong?

Ubuntu PPC is community maintained - it will still exist as long as volunteers will be working on it.

And "modern GUi advances" as you call them (Beryl?) are not even installed by default so that's not a problem

The bottom is, i think, if your current system does all you want and you're happy with it, stick with it. If you need something, even small, that is not Edgy but is in Feisty then it IS worth the install, just back up important files.

---

