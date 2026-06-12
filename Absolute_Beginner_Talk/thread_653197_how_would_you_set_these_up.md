---
title: "how would you set these up?"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by randomjohn on 2007-12-29
I have 
2 old PCs - 1 has gutsy desktop already the other has xp for now,
1 new PC running Vista
1 laptop running xp
2 xboxes running xbmc.  

I want the 2 old PCs to be fileservers.  I have them set up right now as just regular pcs with the drives shared.  They're mapped on xp and vista and mounted or whatever xbmc calls it on the xboxes.  That means I end up with like 10 drives in vista between the local drives (which are partitioned) and the network drives.  I'd really like to have some solution that lets me treat the different drives all as one big drive.  The only other thing I need to do on the ubuntu pcs is run a torrent client.  I also like having webmin.  It's a lot faster when I use vnc and do things like unrarring through that rather than on the mapped drives.  Any suggestions on the best way to set this up?  Should I install ubuntu server and put the gui on top of that instead of having all the ubuntu desktop apps and then removing them?

---

### Post by hyper_ch on 2007-12-29
well, if the old two computer both are installed as linux you can remotely mount the filesystem of old pc 2 into old pc 1 and then it would appear as 1 huge filesystem....however when requesting data from pc 2 it will first pass through pc1... that might slow down the transfer.

As for the setup, I would setup them as ubuntu servers and not have a gui... if they are pure fileserver you don't need a gui... and for torrent client, in that case I'd also recommend rtorrent. It's also terminal/ncurse based and not very difficult to handle.

---

