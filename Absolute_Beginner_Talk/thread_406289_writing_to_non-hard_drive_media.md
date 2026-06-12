---
title: "writing to non-hard drive media"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-04-10
Why is it that all of a sudden I can no longer write files, etc. to either my CD-RW drive and/or my thumb drive.

I could do this just a while back and to my knowledge I have not changed anything (except applying the updates as they became available) have they changed something in the O/S ?

Thanks.

---

### Post by caffienefree on 2007-04-11
What error are you receiving when you attempt to write?

---

### Post by wpshooter on 2007-04-11
It is a write permissions error.  Please see the attached screenshot.

This is an attempt at writing to my thumb drive.

I recently had occasion to download some sound files from a website and I wrote them to my download directory on my hard drive.  I then wanted to make a backup copy of them on a CD-RW and I KNOW that all I did was drag the sound files from the hard drive location to the CD-RW media and it copied them just fine.  Now when I attempt to do this to either the CD drive or to my thumb drive I get this permissions error.

Could this have something to do with the fact that in the interceding time that I used the thumb drive and the CD-RW media on a Windows based machine at work ?  Could this have somehow changed the ownership of the media/devices ?

Thanks.

---

### Post by caffienefree on 2007-04-12
Please execute the command ls -l in the folder below that.

---

### Post by wpshooter on 2007-04-13
> **caffienefree said:**
> Please execute the command ls -l in the folder below that.


I don't understand what you mean by "Folder below that" ???

Do you mean to CD to any folder than is located on the thumb drive or the CD-RW media  ?

Thanks.

---

### Post by eentonig on 2007-04-13
I had the same issue yesterday, where my USB HD was suddenly auto-mounted as read-only.
I forced it to reload and didn't solve.
Then I blocked the mounted folder under /media/, so it needed to take/create another folder on auto-mount. It worked again as it should. 

I didn't post a bug yet, as I first wanted to investigate if it was caused by some wrong doing on my account.

---

### Post by wpshooter on 2007-04-13
Eentonig:

Having heard you say that, this give me suspect that some update/upgrade to the Ubuntu O/S has caused this.  I certainly don't think I have change any settings that would have caused this behavior or lack therefore.  

Because to be quite frank, I don't think I am smart enough to make the change that would be needed to change this media access.

Me thinks Ubuntu has developed a BUG.

I would appreciate it if you would consider reporting this as a bug.

Thanks.

---

