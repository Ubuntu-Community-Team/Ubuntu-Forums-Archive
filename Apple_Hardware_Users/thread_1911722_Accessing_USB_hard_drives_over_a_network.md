---
title: "Accessing USB hard drives over a network"
date: 2012-01-19
forum: Apple Hardware Users
---

### Post by galvatron1983 on 2012-01-19
Another question!

With my Ubuntu Nettop connected to the same wireless network as my iMac Server, will the nettop be able to access the USB drives connected and mounted on the iMac server through the network?

I dont need to write to the drives, just access video files stored on them for playback on the Ubuntu nettop.

---

### Post by CoffeeRain on 2012-01-19
I think so. Try ssh and cd to /Volumes/nameofusbdrive. This should be where it is.

---

### Post by Buntumatic on 2012-01-19
Yes, if your server is sharing them over NFS.

---

### Post by galvatron1983 on 2012-01-19
> **Buntumatic said:**
> Yes, if your server is sharing them over NFS.

How do I enable NFS sharing of my USB drives on the Mac?

---

### Post by Buntumatic on 2012-01-19
[http://www.behanna.org/osx/nfs/howto1.html](http://www.behanna.org/osx/nfs/howto1.html)

That's the first hit on Google, feel free to search more.

---

### Post by galvatron1983 on 2012-01-20
Thanks for the help guys, its looks like NFS is set up by default in Lion. I just to make sure my USB drives arent HFS+ Journaled so the Ubuntu Nettop can read them...

---

### Post by Buntumatic on 2012-01-20
> **galvatron1983 said:**
> Thanks for the help guys, its looks like NFS is set up by default in Lion. I just to make sure my USB drives arent HFS+ Journaled so the Ubuntu Nettop can read them...

You misunderstood, dealing with local filesystem is the job for local OS. The only filesystem support needed from your nettop is NFS - network file system. Your Mac has to be able to read those drives in order to export them over NFS.

---

### Post by galvatron1983 on 2012-01-24
> **Buntumatic said:**
> You misunderstood, dealing with local filesystem is the job for local OS. The only filesystem support needed from your nettop is NFS - network file system. Your Mac has to be able to read those drives in order to export them over NFS.

My Mac has these drives connected to its USB ports at all times, so theyre mounted and the iMac is reading them fine. They are formatted in HFS+, and as I understand it Ubuntu can read NFS+ as long its not Journaled NFS+.

All I need from my Ubuntu nettop is to be able to access these drives. I want the drives to appear in the Ubuntu file browser window on the nettop so I can access the files inside them. The iMac Server and the Nettop will be connected the same wireless network to facilitate this. 

It should work like this :- File sharing is active on the iMac. On the nettop in Ubuntu, I want to see the iMac Server's icon in the network portion of the file browser window, Ill click on that and see all the mounted volumes on it, including the USB external drives. I can then click on a say.. a video file thats stored on the USB external and it will open on the nettop and happily play in VLC or something over the wireless network. 

Instead of having a keyboard and mouse controlling the nettop, I want to be able to remote desktop to it on my MacBook Air, apparently TeamViewer is the best bet for this.

---

