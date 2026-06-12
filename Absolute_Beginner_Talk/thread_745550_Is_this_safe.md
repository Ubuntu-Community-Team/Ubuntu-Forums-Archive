---
title: "Is this safe?"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Fixman on 2008-04-04
I want to download a big file using azureus (a P2P program). Its safe to save it on a ntfs partition? Im trying to clean up my ext3 one.

---

### Post by wolfen69 on 2008-04-04
you will have no problems. my music drive is ntfs and all my torrents go there.

---

### Post by oblivioncth on 2008-04-04
I would save it somewhere if at all possible on your ext3 partition just to be sure but putting 
it on a NTFS partition should be fine. Though depending on the file format it may not work.

---

### Post by Tomatz on 2008-04-04
I wouldn't recommend it as it will be very fragmented.

Its your call if it borks your ntfs drive just do a **chkdsk /r** from the xp recovery console.

---

### Post by northern lights on 2008-04-04
> **oblivioncth said:**
> Though depending on the file format it may not work.What format exactly couldn't I write to ntfs? Just curious...

---

### Post by SOULRiDER on 2008-04-04
> **northern lights said:**
> What format exactly couldn't I write to ntfs? Just curious...

AFAIK it does not matter what kinds of file you woll be writing. 

I used to have an NTFs partition and never had any problems.

---

### Post by northern lights on 2008-04-04
> **SOULRiDER said:**
> AFAIK it does not matter what kinds of file you woll be writing. 

I used to have an NTFs partition and never had any problems.

That was my point. Same here.

---

### Post by Fixman on 2008-04-04
> **Tomatz said:**
> I wouldn't recommend it as it will be very fragmented.

Its your call if it borks your ntfs drive just do a **chkdsk /r** from the xp recovery console.

Im actually downloading files I need for my Vista, so, if I don't download on NTFS, I must download on Ext3 and then copy all to NTFS.

By the way, is there a possibility of (the download) going slower?

---

### Post by stefangr1 on 2008-04-04
I wouldn't put my money on it, I corrupted my windows partition beyond being able to boot doing just that a few years ago. They say, however, that is has become safer now.

---

### Post by Crafty Kisses on 2008-04-04
> **Fixman said:**
> I want to download a big file using azureus (a P2P program). Its safe to save it on a ntfs partition? Im trying to clean up my ext3 one.

I don't see why you would have any problems if you saved it to your NTFS partition.

---

### Post by Legionox on 2008-04-04
You shouldn't have problems with it now, the NTFS writing in Linux is quite reliable now but a few years ago I did screw over my Windows partition before doing this.

---

### Post by crjackson on 2008-04-04
> **oblivioncth said:**
> Though depending on the file format it may not work.

This is incorrect.  The NTFS file system won't restrict the type of files you save there.

---

### Post by crjackson on 2008-04-04
> **stefangr1 said:**
> I wouldn't put my money on it, I corrupted my windows partition beyond being able to boot doing just that [SIZE="4"]a few years ago[/SIZE]. They say, however, that is has become safer now.

Things were not the same a few years ago.  I have 12 Ubuntu system that I currently administer and All of them have NTFS data drives accessed for file storage everday and I've not had a single incident since 7.04 w/NTFS-3G.  It works fine.  Try it again on a safe drive and see for yourself.  You will be pleased.

---

### Post by crjackson on 2008-04-04
> **Fixman said:**
> I want to download a big file using azureus (a P2P program). Its safe to save it on a ntfs partition? Im trying to clean up my ext3 one.

Provided your NTFS partition is in good condition, it's perfectly safe.

---

### Post by stefangr1 on 2008-04-05
> **crjackson said:**
> Things were not the same a few years ago.  I have 12 Ubuntu system that I currently administer and All of them have NTFS data drives accessed for file storage everday and I've not had a single incident since 7.04 w/NTFS-3G.  It works fine.  Try it again on a safe drive and see for yourself.  You will be pleased.

OK, that's very nice to hear. I think this will be especially practical since a lot of people I know have ntfs formatted portable usb drives, which I until now didn't connect to my computer to avoid damaging them.

---

### Post by Mick8882003 on 2008-04-05
No, run for your life, your computer will explode, hehe

---

### Post by stefangr1 on 2008-04-05
> **Mick8882003 said:**
> No, run for your life, your computer will explode, hehe

:lolflag:

Yeah, that would be fun, having disk parts flying around due to a bug. 

No, it's more that I didn't want to take any risks with others stuff. But apparently it has become really safe now, and it is off course a handy feature sometimes.

---

### Post by SOULRiDER on 2008-04-05
> **Fixman said:**
> Im actually downloading files I need for my Vista, so, if I don't download on NTFS, I must download on Ext3 and then copy all to NTFS.

By the way, is there a possibility of (the download) going slower?

going slower because of the partition? No way.

---

