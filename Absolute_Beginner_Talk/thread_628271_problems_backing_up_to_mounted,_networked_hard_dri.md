---
title: "problems backing up to mounted, networked hard drive"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2007-12-01
I have finally worked out how to mount my external hard drive (iomega networked hard drive 1TB) but i am now having problems with using backup software to backup to it.

I have tried using software such as keep, konserve and rsync, all of which don't even bother to tell me that the backup has done absolutely nothing. the files just don't get copied.

when I use hubackup, i get these messages:

firstly:

> It's recommended that you verify the integrity of the newly created backup archive.Would you like to proceed with verification? (Make sure the first medium of the newlycreated backup archive is accessible or loaded in drive)

that makes sense. If i click cancel, it gives me no more messages, but when i check on the backup, it hasn't been done. when i click on ok...

> The media does not seem to contain valid HUBackup data.
Please make sure media #1 of your backup set is in drive and retry.(You can always use the "Verify" button independently)

this is really annnnnnnoying!!!
much help required, all of it appreciated, thanks

---

### Post by lightstream on 2007-12-01
When you say external networked harddrive, do you mean you have an external harddrive connected to another computer which you are accessing over the net? Or a standalone device which is connected to the net independently?

Are you using rsync from the command line? If so, what the command you are using?

Also, you might try the graphical front-end for rsync, which is available from Add/Remove under the name grsync

---

