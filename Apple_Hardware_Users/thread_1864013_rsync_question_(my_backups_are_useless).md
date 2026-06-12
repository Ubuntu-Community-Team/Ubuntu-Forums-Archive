---
title: "rsync question (my backups are useless)"
date: 2011-10-18
forum: Apple Hardware Users
---

### Post by kentt on 2011-10-18
Hi

I am in a huge crisis.  
I backed up my old mac by
sudo rsync -rv / /Volumes/BACKUP01/OldMBP

This took about 6 hours to finish and I checked and saw that the files seemed to be there.
Now it seems that files are missing here and there, seemingly without rhyme or reason.  For example in a folder where I should have two files, there is only one.  It's seems sporadic.

Anyway, the original drive is now being used elsewhere and my backup seems useless.  I was literally puking the the bathroom at work because I've lost some important stuff that I don't have backups of (go ahead and lecture).

Any advice as to what I've done wrong, or how to recover would be immensely appreciated.

Kind regards,
kentt

---

### Post by Lars Noodén on 2011-10-18
My condolences.  I would have spot checked a few files to make sure of the transfer.  When I backup using rsync I usually do it like this:

rsync -avH /path/to/source /path/to/destination

Often I'll do it over SSH.

---

### Post by kentt on 2011-10-18
Thank you.
I see now that the drive is refusing to mount so I assume it had been failing for a while.

---

