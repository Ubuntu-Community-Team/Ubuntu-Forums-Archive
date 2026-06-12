---
title: "update hoary to dapper?"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-01-05
I can't quite get my head around the differences between update, upgrade and dist-upgrade.

I'm on Hoary now, and because I'm on dialup, I want to wait for Dapper so I can get it through Shipit. But, is it too much of a jump? Will I have to install Dapper (and have to back up all my configurations & personal data) or is it possible to upgrade (i.e., get newer versions of the programs, and new programs) from the CD?

---

### Post by welsh_spud on 2006-01-05
I believe that when you get a Dapper CD from shippit, you can add the CD as a reppo in Synaptic.

From there i'm assuming you can do a dist-upgrade

---

### Post by chimera on 2006-01-05
Just a recommendation, Dapper is currently still in the development stage, the official release will be sometime in april 2006, I'd wait until than if I was you, because in the development version everything might not work like it's supposted to, so unless you need something only Dapper has, right now right here, and seeing as how you're posting a question in this section, I'm guessing you don't.

---

### Post by az on 2006-01-05
Sure, you can upgrade from Hoary to breezy or from hoary to Dapper. If you have packages from other repositories than the cd, be sure to change "hoary" to "breezy" (or Dapper) for each of them.  Update your sources and then upgrade from the cd. That way, you will only have to fetch packages from the internet that are not on the cd you get.


If you just pop in the cd and upgrade following the instructions in the diaolg box, you may have some packages from other repositories removed because their older versions are no longer compatible.

But, yes, you can upgrade easily.

---

### Post by towsonu2003 on 2006-01-05
> **editrix]I can't quite get my head around the differences between update, upgrade and dist-upgrade.[/quote] apt-get update will update the local (ie in your computer) list of packages available to you said:**
> 
I'm on Hoary now, and because I'm on dialup, I want to wait for Dapper so I can get it through Shipit. But, is it too much of a jump?  no

[QUOTE=editrix]Will I have to install Dapper (and have to back up all my configurations & personal data) [/quote] yes
if you have a separate /home partition, you would not have to deal with this to a degree (still need to backup files though)

[QUOTE=editrix]or is it possible to upgrade (i.e., get newer versions of the programs, and new programs) from the CD?[/QUOTE]
yes but it break the system of some people... a fresh install is always better, to me...
I have breezy but I still will install dapper fresh...

---

### Post by editrix on 2006-01-06
Thanks for the info, guys.

So, to make sure I (and other newbies) have it clear:

> apt-get update will update the local (ie in your computer) list of packages available to you

No programs actually get changed. Just the *list* of what's available.

> upgrade will update your packages

This will actually change versions of the installed programs.

> dist-upgrade will upgrade your xxx (hoary) to yyy (breezy)

This will make so many changes to both the installed programs and the list of what's available that it constitutes a distro change.

dist-upgrade will not wipe out personal files, but it's not recommended. A full install will wipe out personal files, but is better.

I'm assuming the fresh install is better because, with so many changes, a lot of the configurations will not be relevant, or won't work, or will actually "break" something?

>   If you just pop in the cd and upgrade following the instructions in the diaolg box, you may have some packages from other repositories removed because their older versions are no longer compatible.

Ah. Didn't know there was an upgrade option--I've only ever done one install, some months ago.

No intention of installing Dapper yet. I'll wait till April.

Thanks again.

---

