---
title: "Should this happen?"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-12-22
All right I just finished connecting to my windows box on my network through my ubuntu box.  I used places>connect to server>windows share> then entered the ip address of my windows box.

So I thought heh I could read my files.  Well is allowing me to write to an ntsf drive as well.  I thought you needed a special driver for this.  Is there anyreason I can all of a sudden write to a drive on another computer on the network running windows with a ntsf drive.


Not complaining but not sure why.

---

### Post by user007usa on 2006-12-22
> **gentlemanmasher said:**
> All right I just finished connecting to my windows box on my network through my ubuntu box.  I used places>connect to server>windows share> then entered the ip address of my windows box.

So I thought heh I could read my files.  Well is allowing me to write to an ntsf drive as well.  I thought you needed a special driver for this.  Is there anyreason I can all of a sudden write to a drive on another computer on the network running windows with a ntsf drive.


Not complaining but not sure why.

Ubuntu only acts as the client in this case.  It is a function of how you have your windows box configured.  I would be careful, it may very well be that you have it configured so that any user on the internet can write to your hard drive depending on how you have it set.

I don't think you need a special driver to do this at all when going over a windows share.  I am not sure however.

---

### Post by PilotJLR on 2006-12-22
You're not writing to NTFS... you're writing to an application layer SMB protocol server. The filesystem on the other side doesn't matter.

Granted, the Window$ machine almost certainly uses NTFS, but the SMB client doesn't know that and doesn't care.

If the NTFS volume was directly attached, then SMB would not act as the middle-man, and then you wouldn't be able to write without the beta (i think) NTFS read/write driver.

EDIT: I'm not sure how clear that was. What is basically happening is SMB (Samba) is telling the Windows machine what to do, and the Windows machine then performs the actual read / writes.

---

### Post by gentlemanmasher on 2006-12-22
OH Well I can't use any of the files.  I tried to play an mp3 and it won't play neither will my movies, but I can view my pics.

---

### Post by PilotJLR on 2006-12-22
You need to just mount the samba share to a mount point... then everything will work.

---

