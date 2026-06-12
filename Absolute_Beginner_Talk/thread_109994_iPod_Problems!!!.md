---
title: "iPod Problems!!!"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by TraptElmnt on 2005-12-29
Does anyone know how to sync an iPod with ubuntu?  And is it possible?

---

### Post by Gimbo on 2005-12-29
Go to System>Administration>Synaptic Package Manager
Click the search button (the one in the top right not the bottom left)
Type ipod and hit enter
You should get a list of 12 packages including banshee and gtkpod. Although I've never tried either of those, and I don't own an ipod, those are the programs I've heard of that let you sync with an ipod.

---

### Post by narcolept on 2005-12-29
As Gimbo said, gtkpod will work fine and allow you to sync your ipod, as well as play songs from the ipod through xmms or the like.

---

### Post by MakubeX on 2006-01-14
I have a problem too.. Does Ubuntu have some restrictions with regards to power? I'm using a 3rd Gen 40GB Ipod plugged via USB but it doesn't charge. Are there permissions/restrictions blocking such things?

Thanks.

---

### Post by nijinsky on 2006-01-16
[QUOTE=Gimbo]Go to System>Administration>Synaptic Package Manager
Click the search button (the one in the top right not the bottom left)
Type ipod and hit enter
You should get a list of 12 packages including banshee and gtkpod. Although I've never tried either of those, and I don't own an ipod, those are the programs I've heard of that let you sync with an ipod.[/QUOTE]

When I do this I get "no package selected" and there is not a list of apps.

Anyone any idea.

Cheers
Bob

---

### Post by Edward The Bonobo on 2006-01-16
I had the same learning curve.

First of all, you have to get Synaptic to search the community repositories as well as the Ubuntu ones.  This is where you get software that is not part of the official Ubuntu release.  I can't remember where to click (I'm at work, in Windows at the moment), but it's something like Repositories.../ Add... then tick Community.  *Then *you can search.

One thing to note, though...only the latest Ubuntu release (Dapper) has the latest gtkpod (v0.99) in its repositories.  The others have v0.88, which doesn't work for 5th Gen Video iPods.  So...I've not got it working myself yet, if anyone is able to give further guidance.

Oh...and I *think *you have to get the iPod loaded with at least one song with iTunes in Windows first, so that it has an iTunes database for gtkpod to read.

---

### Post by billybofh on 2006-01-16
[QUOTE=Edward The Bonobo]One thing to note, though...only the latest Ubuntu release (Dapper) has the latest gtkpod (v0.99) in its repositories.  The others have v0.88, which doesn't work for 5th Gen Video iPods.  So...I've not got it working myself yet, if anyone is able to give further guidance.[/QUOTE]

I'm running Breezy Badger and gtkpod worked fine 1st time with my shiney new video iPod.  I've synced a few gig onto it quite happily.

I did an initial "initialisation" of it on Windows first while at work to make sure it was fat32 and had the files/db created.  Maybe that made a difference?

---

### Post by Edward The Bonobo on 2006-01-16
Nope.  I've already loaded it up with few Gigs using a friend's iTunes in Windows, and I can see the iTunes db file and all the .mp3s.

What version of gtkpod are you using in Breezy?  Seems I can only get 0.88 in my Hoary.

(But, yes...in answer to the initial question...it *does *seem to work.  Apparently.  Once you know what you're doing.  That's the tricky bit in Linux...knowing what you're doing)

---

### Post by Edward The Bonobo on 2006-01-18
Seemingly this post [http://www.ubuntuforums.org/showthread.php?t=114946](http://www.ubuntuforums.org/showthread.php?t=114946) tells you how to get v0.99 from elsewhere.

---

