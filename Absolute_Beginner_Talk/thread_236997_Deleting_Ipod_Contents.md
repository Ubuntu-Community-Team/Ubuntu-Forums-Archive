---
title: "Deleting Ipod Contents"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by quickblaine on 2006-08-15
So, I'm a pretty confident linux user but this has got me a bit stumped. I've been trying to update my ipod in amaroK, only to find that it will only let me use 526mb of space (its a 2GB nano)

So i went into the ipod, and realised that hidden files werent showing. i got them up to find a folder named ".Trash-ben" and everything I was deleting was going in there, meaning i wasnt actually reclaiming any file space. I tried deleteing that, but I got something like:

Error While Deleting

"/media/ip...od153.mp3" cannot be deleted because it is on a read-only disk.

I have full permissions for the ipod, so am unsure how to get rid of that folder to get my ipod space back!

I'd apprecieate any help,

Ben
Edit/Delete Message

---

### Post by stricevics on 2006-08-15
> **quickblaine said:**
> 
Error While Deleting

"/media/ip...od153.mp3" cannot be deleted because it is on a read-only disk.

I have full permissions for the ipod, so am unsure how to get rid of that folder to get my ipod space back!

I'd apprecieate any help,

Ben
Edit/Delete Message

Not an expert when it comes to iPod, but it seems to me that this error has been caused by the iPod's file system which has been mounted as read-only.

Try to search forums for postings regarding mounting different file systems.

Hope this helps,

St.

---

### Post by shoot2kill on 2006-08-15
this is not to do with the ipod file system, becaause i have a memory stick (USB) which does this also, but i just used windowze to delete the folder....

an answer to this would be rerally handy..

---

### Post by quickblaine on 2006-08-15
update: did some digging about the forums and found this:

> **MarcMaserati said:**
> First

```
cat /etc/mtab
```

to find out where the ipod is mounted (it'll be the line with /media/ipod, cat that when the iPod is plugged in and automounted, obviously).  Once you have the /dev, alls you do is

```
dosfsck /dev/sdb2 -a
```

Where /dev/sdb2 is your ipod's device.

So i did that, and now my ipod shows the folder icon and "www.apple.com/support/ipod"!!! what now?

---

