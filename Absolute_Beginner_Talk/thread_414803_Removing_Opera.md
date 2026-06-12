---
title: "Removing Opera"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-04-20
Opera browser stopped working when I tried an update this week. Since then I can't open Opera at all, so I've  removed it from my system using "add and remove" and this appeared to work.   Unfortunately, when I  try a new install, I get a broken link message and  can't install the new version. 

Is it possible to I rid my system of all remnants of the old Opera using the command line please?

---

### Post by webjames on 2007-04-20
you could try going into synaptic package manager, and right clicking on opera and selecting

"completely remove" then try installing it again?

hope this helps,

---

### Post by a.v.l on 2007-04-20
> **webjames said:**
> you could try going into synaptic package manager, and right clicking on opera and selecting

"completely remove" then try installing it again?

hope this helps,

Thanks for that, but would that also remove it from Synaptic too?  I ask because I don't know for sure.

---

### Post by petersjm on 2007-04-20
No, it will stay in Synaptic for later installation.

---

### Post by raspark on 2007-04-20
My Opera broke when I had a failed upgrade earlier tonight.  

Yes,
going into synaptic and removing it, re-installing it does work.  That's what I did.

---

### Post by a.v.l on 2007-04-20
> **petersjm said:**
> No, it will stay in Synaptic for later installation.

Unfortunately after doing a complete removal in Synaptic I am still unable to reinstall I get this message from Synaptic when I try.

Quote:

COULD NOT MARK ALL PACKAGES FOR INSTALLATION OR UPGRADE

The following packages have unresolvable dependencies. Make sure that all required repositories are added in the preferences.
opera:
  Depends: libc6 (>=2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
  Depends: libgcc1 (>=1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
  Depends: libqt3-mt (>=3:3.3.8really3.3.7) but 3:3.3.6-3ubuntu3.1 is to be installed
  Depends: libstdc++6 (>=4.1.2) but 4.1.1-13ubuntu5 is to be installed

 I have multiverse and universe already installed.

---

### Post by raspark on 2007-04-20
OK try this:

In synaptic are there two versions of Opera?  I know mine had two earlier.

Choose to install the opera (static) and see if that works.  That opera version has it's own dependencies mostly met in the downloaded file.

---

### Post by Bachstelze on 2007-04-20
a.v.l : You're using Edgy and the Opera you're trying to install is for FEisty. I guess you know what you need to do now ;)

---

### Post by a.v.l on 2007-04-20
All seems well again thanks for the help.

---

