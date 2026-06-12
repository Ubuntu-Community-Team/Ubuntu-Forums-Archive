---
title: "mounting woes due to permissions &amp; server access with Live CD"
date: 2009-11-08
forum: Apple Hardware Users
---

### Post by wxl on 2009-11-08
So I've got a Powerbook G4 that's got a dying hard drive (hfsplus).  I can access the drive and see the structure and at least some of the files will copy without failing due to i/o errors but there is certainly a mechanical issue.  So I'm trying to save what I can.

I've got access to a nfts share with lots of space that I can use to put the info on.

Obviously I cannot install to the dying drive.

So I've successfully booted to the live CD.

I can use "Connect To Server..." to connect to the nfts share.

I can automount to the hfsplus drive but a standard mount won't work due to some bad super block issue, so I can't change the owner.

And therein lies the rub.  So I can sudo or sudo su in terminal to access the files I wouldn't normally have access to in Nautilus.  This is good.

But since "Connect To Server..." mounts to ~ (in this case user ubuntu, not root), that means I can't access the nfts share.

So no matter what I do I can't get access to both drives.  Any ideas?

---

