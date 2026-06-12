---
title: "Putting Old Ubuntu Hard Drive in a New PC?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by uncreative on 2007-01-08
Right now I have Ubuntu installed on a computer which has just grown old.  Its slowing me down with the design work I do etc... So I want to go buy a newer, faster computer, but I don't want a fresh install of Ubuntu.  It took me a while to get this just how I like it, and some programs I can't even get anymore.

Is there a way to take the hard drive out of my old computer and put it in my new computer and have it work just fine?:confused: 

Any help would be appreciated, thank you.

---

### Post by glotz on 2007-01-08
Probably it will work just fine, lately did it myself. Do you know what kind of harddisk it is? Both computers are desktops, right?
On the other hand, you might want to buy a new harddisk and just copy over the content. The new disks are a lot faster than the old disks. And then you'd have a handy backup disk too. If you're buying a killer machine, it makes little sense to lag it down with a bad disk.

---

### Post by Totzo on 2007-01-08
it's really quite easy, only thing I'd be aware of is that it may negate the warranty on your new box. But then installing ubuntu on it probably would as well!

A new computer may use a different type of hard drive interface (sata) but since older (pata) ones use the same interface as cdroms you will still be able to connect your old drive.

You need to check the jumper settings on the drive as well if it is the only one you are connecting to an ide slot set it to "master", if it is on a cable with another drive one must be "master" and the other "slave".

Once it is fitted you will need to check your bios (normally by pressing "delete" or similar when you switch your computer on) to see which drive the computer will try to boot from first and that's it.

Check [this]("http://www.buildyourown.org.uk/pc-building/fitting/hard-drive/") out too

---

### Post by haiku99 on 2007-01-08
this is easy as was said, however the old drive will be cofigured for the old computer, so that could potentially cause some problems since the new computer will have different hardware (processor, memory, interface cards, etc)., but perhaps Edgy will reconfigure automatically...

---

### Post by glotz on 2007-01-08
At least Dapper managed motherboard+CPU+memory+vid card+sound card+network card change without operator. :)

If you'll change your monitor resolution you might want to reconfigure x-server. And you might want to get an optimized kernel for your new processor. Both are simple things.

---

