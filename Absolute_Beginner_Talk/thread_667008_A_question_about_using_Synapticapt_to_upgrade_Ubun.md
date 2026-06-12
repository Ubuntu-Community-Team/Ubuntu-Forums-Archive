---
title: "A question about using Synaptic/apt to upgrade Ubuntu versions and software packages"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by laptoplinux on 2008-01-13
At the moment, I'm still running Feisty, and since Hardy is only a few months away and I am involved with work that would make a major system upgrade inconvenient at the moment, I'll just wait until the summer.  

My question is two-fold, dealing mainly with what happens to people who, like me, may not be able to jump instantly to the next release once it's out, or who might even have to only jump every other release or more.

1)  How safe is using synaptic to upgrade a distro (from Feisty to Gutsy, Gutsy to Hardy, etc.) really?  Every time a new version is officially released, the forums always tend to show a mixed bag for those that perform a synaptic upgrade instead of a clean install.  For every user who performs a Synaptic upgrade without a hitch, there seems to be another one or more users who wind up with strange, random breakage in their system that can only be fixed by a clean install.  If using synaptic is going to force a clean install to recover functionality and stability, I might as well do that from the start.  At the moment, I do not have a separate /home partition and do not plan on creating one unless a system failure forces me to reorganize the partition setup anyway.

2.)  What is the Ubuntu policy about releasing updates to software packages for versions behind the current one but still within the support timeframe (like Feisty is now)?  For example, Open Office.  This program isn't tied down to the Gnome framework, so it shouldn't be an issue to release an update for it even after a new version of Ubuntu is released.  But I could find no way to upgrade to OpenOffice 2.3 in Feisty through synaptic/apt.  I eventually found a script online that uninstalled the Feisty version of OpenOffice 2.2 and automatically installed and integrated OpenOffice 2.3.  But why couldn't something like that have been done in the repositories?  As another example, Mplayer or some other desktop environment neutral software.  Some of these programs have advanced quite a bit since Feisty was released, but there are no updates for them that I can see.  Is there some other repository that I don't know about that I should add?  I already have a couple of Feisty backport repos.  In general, what exactly is Ubuntu's policy on updating the packages in older releases?  Are all updates stopped as soon as the next version is released?  What about for LTS releases?  I just need to know so that I can plan ahead on upgrading in the future.

---

### Post by sumguy231 on 2008-01-13
1.) You're definately safer doing a clean install. I've seen upgrades go both ways personally, it is more likely to work if you haven't tweaked the system much or used a lot of third party repositories which might end up replacing stock Ubuntu packages. For the time being I keep a separate home partition for clean installs, but there's a feature spec in Hardy for a feature that would let you keep your home directory after a clean install even without a separate partition.

---

