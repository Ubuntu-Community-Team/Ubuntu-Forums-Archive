---
title: "Clearning Ubuntu?"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2006-01-04
Yeah, was kinda wondering what the Ubuntu equivalent of the normal Windows cleanup tools where, if they exist....
Things like a disk defrag and cleanup, registry cleaner? 

And, downloaded and installed ET....Was a .run. How do I un-install it now?

Thanks

---

### Post by Lord Illidan on 2006-01-04
Disk defrag? We don't need that with our file systems.
And as for the registry, we don't have one either.

I remember a cleanup tool reviewed in Linux Format.. I'll try and find it.

---

### Post by KingBahamut on 2006-01-04
Dont need to defrag, though occasion fsck's arent a bad idea. ( I usually force every 20 or so Reboots ) 

Clean up, you can run a cron job to remove the stuff that collects in /tmp. 

Registry Clearner - no such animal here. 

Alternately you can run apt-get autoclean to clear out your apt cache.

---

### Post by Jimmey on 2006-01-04
That's a relief.

How to uninstall ET? There's a directory for it in /home/james/.etwolf, but I'm not sure that's all of them. Should I just delete them anyway, or is there a way to uninstall the application?

---

### Post by dcraven on 2006-01-04
There is an uninstall script in /usr/local/games/enemy-territory/etf/ assuming you installed to the default target. Modify the path if necessary. This script will not (at least it **better** not) remove your user configuration files in your home directory. Therefore, you will manually need to delete ~/.etwolf if you want to get rid of it. This is safe to do, and would just get regenerated the next time you run the game anyways with default values.

HTH,
~djc

---

### Post by Jimmey on 2006-01-04
Didn't find that path - /usr/local/games/enemy-territory/ 's there....But...No etf?

---

### Post by phido on 2006-01-04
Just remove the enemy-territoy folder, and the ~/.etwolf
IMO

By the way the /etf folder is from ETF mod and so the uninstall entry.

---

### Post by dcraven on 2006-01-04
[QUOTE=phido]By the way the /etf folder is from ETF mod and so the uninstall entry.[/QUOTE]
Oops, my bad. I got confused and forgot that ETF was a different game (or mod). My apologies to the original poster.

As far as I know, you can delete the /usr/local/games/enemy-territory/, ~/.etwolf, /usr/local/bin/et, and /usr/local/bin/etded paths and be clean.

Cheers,
~djc

---

