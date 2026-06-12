---
title: "Security Updates Question"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by WilliamB on 2006-09-12
I'm new to Linux having installed Ubuntu a few weeks ago.

I've enabled some additional repositories in Synaptic and ran across the following when reading the docs:

__

#

To enable the Universe repository, check the Community Maintained (Universe) button.
[Note]     

Adding this repository will mean that the majority of the Free Software universe will be available to install on your system. This software is supported by a carefully selected group of volunteers within the Ubuntu Community, but is not supported by the core Ubuntu development team and may not include security updates.
#

To enable the Multiverse repository, check the Non-free (Multiverse) button.
[Warning]     

Adding this repository will mean that software which has been classified as non-free will be available to install on your system. This software may not be permitted in some jurisdictions. When installing each package from this repository, you should verify that the laws of your country permit you to use it. Again, this software may not include security updates.

__

Since both say that this software may not include security updates, how does one get updates for said software?

Is that saying that it doesn't include the back-ported security updates so you'd need to install a new version for updates or what?

Just wanting to keep my system secure so trying to understand the difference between the back-ported security updates and how to plug any holes for any other apps.

Thanks in advance!

---

### Post by steve.horsley on 2006-09-12
One waits until the people who publish the application in Universe publish the security updates too. Normally, they will. If they get hit by a bus, the update may be delayed.

---

### Post by az on 2006-09-12
Those repositories are community-maintained, and they do get updates.  They are not officially-supported so you probably won't want to rely on them in a production environment.

---

### Post by WilliamB on 2006-09-13
Thanks all.

---

