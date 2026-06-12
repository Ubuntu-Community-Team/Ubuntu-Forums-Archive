---
title: "Simple iDisk Use (with davfs) ?"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by thornomad on 2006-08-10
Hi,

I have been searching the web for an easy way to connect to my .Mac account iDisk ...

First, I tried the WebDav connection under /Places/Connect to Server... then selecting WebDav(HTTP), and entering "idisk.mac.com" as the server and entering my username.  This creates an icon on the desktop but if I click on it, nothing happens.  I have tried other settings but with those I only get errors.

I then looked some more and found "davfs" ... which I installed through the package installer and edited the "secrets" file to include my iDisk information ... however, I still can't get that to work either.

Anyone know of a simple way I can mount my iDisk in Ubuntu?

Damon

---

### Post by Redcard on 2006-08-10
> **thornomad said:**
> Hi,

I have been searching the web for an easy way to connect to my .Mac account iDisk ...

First, I tried the WebDav connection under /Places/Connect to Server... then selecting WebDav(HTTP), and entering "idisk.mac.com" as the server and entering my username.  This creates an icon on the desktop but if I click on it, nothing happens.  I have tried other settings but with those I only get errors.

I then looked some more and found "davfs" ... which I installed through the package installer and edited the "secrets" file to include my iDisk information ... however, I still can't get that to work either.

Anyone know of a simple way I can mount my iDisk in Ubuntu?

Damon

I tried this awhile back, and it seems that Apple makes it very difficult to use anything but Apple software to get there.  It might be the same still, in which case you probably won't be able to mount your iDisk.  All the instructions I see had the method you used.  This probably means that Apple has closed it off.  Sorry.

---

### Post by thornomad on 2006-08-11
Hmm ... my problem, I think, is that I am not quite sure which instructions I need to follow to configure everything ... I tried following the instruction in the davfs readme file ... so that I could mount the iDisk automatically ... it appears now next to my other partitions ... however, when I try to connect, I get the error:

```
/usr/lib/mount.davfs-2.6: no mountpoint specified
```

Again: I think a lot of it has to do with my complete lack of understanding as to what steps I need to take (and so many different options for the different "flavors") that I am confused.

Thanks everyone!

Damon

---

