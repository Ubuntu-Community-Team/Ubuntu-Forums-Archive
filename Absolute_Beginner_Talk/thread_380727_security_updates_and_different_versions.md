---
title: "security updates and different versions"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by lynwgnr on 2007-03-10
Hello, I installed Ubuntu 6.06 Desktop because it is LTS which I gather to mean it has 3 entire years of security updates. I read somewhere that 6.10 only has 18 months of security updates. How does this work? Do these two versions point to, and use different repositories for updates? Why can't the 6.10 version be set to point to the 6.06 one so it too will benefit from years of stability? Also, for non-LTS versions, does it mean one has to re-install a new version when the 18 months is up? I am just trying to understand how one uses different versions. 
Thank you!

---

### Post by aysiu on 2007-03-10
They point to different repositories.

You can see the repositories in the /etc/apt/sources.list file. If you're using Dapper, the word *dapper* will appear in almost every line in that file. If you're using Edgy, the word *edgy* will appear in each line.

There's no point in using Dapper repositories in Edgy--you'll just end up with a broken system. I have a feeling anyone who's using Edgy right now isn't concerned with keeping Edgy until April 2008. I'd wager 99% of people using Edgy right now will upgrade to Feisty Fawn within a month or two.

---

### Post by lynwgnr on 2007-03-10
Thanks for the reply! When it is said "people using Edgy right now will upgrade to Feisty Fawn" does 'upgrade' typically mean a complete re-install, or can an Ubuntu release be continuously updated to the latest versions of packages, hence foregoing the need to re-install the entire distribution upon each successive release?
Thanks again!

---

### Post by orb9220 on 2007-03-10
There will probally be a way to upgrade from edgy to fiesty. But the best way in my opion is to have a seprate /home partition so when I do a clean install I still have my installed apps.

Upgrades tend to be problematic for some user's. I like to do a clean to remove any issue's that the developer's might have missed.

---

### Post by aysiu on 2007-03-10
Theoretically, you can keep upgrading *ad infinitum*. 

Theoretically, you could have installed Warty Warthog in October 2004 and have upgraded to Hoary, to Breezy, to Dapper, to Edgy... and still have had the same installation.

A lot of people do clean reinstallations, though, for a variety of reasons:

1. Sometimes, upgrades don't go smoothly.
2. They're curious as to what the new installer looks like.
3. They have all sorts of gunk (stray libraries, modified config files, etc.) and would prefer a clean slate anyway.

As orb9220 says, a [separate /home partition](http://www.psychocats.net/ubuntu/separatehome) is a good idea if you're planning to reinstall.

---

