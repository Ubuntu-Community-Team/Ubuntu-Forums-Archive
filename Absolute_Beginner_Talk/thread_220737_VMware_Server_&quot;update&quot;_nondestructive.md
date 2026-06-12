---
title: "VMware Server &quot;update&quot; nondestructive"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by fjm03 on 2006-07-22
Updating from VWware Server 1.0.-build 24927, the original, evaluation freebee, to the present, still free as in beer, stable release (build 28343) is a simple process that doesn't destroy existing virtual machines or alter custom settings.

28343, unlike 24927, offers a liscense that doesn't expire. The included, perl installer recognizes the existence of 24927 and simply updates the necessary files.

A new set of VMware Tools is required for the new release and those Tools must be updated as well, through a manual install option buried in the host application's menu bar. Again, the *Install Tools* process automatically removes the old tools and installs the new, while preserving the custom settings.

My biggest problem, as a linux newbie, was figuring out that "./" was the linux command syntax to run the file *vmware-install.pl.*

I'm a happy camper. I can still use lightScribe and don't have to ever again worry about August 8. In a perfect world, virtual machines would recognize LTP ports and I'd have the use of my old CanoScan FB 602P on Dapper.

---

### Post by rbmorse on 2006-07-22
Excuse my ignorance, but what happens(ed) on 8 Aug?

---

### Post by PriceChild on 2006-07-22
Virtual Machines can recognies LTP ports...

---

### Post by fjm03 on 2006-08-05
> **rbmorse said:**
> Excuse my ignorance, but what happens(ed) on 8 Aug?

The licensing on the beta offerings all expire on August 8, 2006. Just as in the intro to the old TV series, Mission Impossible, the software apparently goes *poof* on the 9th.

---

