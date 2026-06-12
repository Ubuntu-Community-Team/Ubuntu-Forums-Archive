---
title: "Network File sharing issue, help please!"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by Eliphelet on 2007-11-03
Hi,

I have what I feel is quite a complex problem that I hope someone can help with.  

I have just installed Ubuntu on my pc which was amazingly simple and not at all like the horror stories ive heard.  I now have 2 physical HDD's in my desktop pc, one which hereon will be referred to as the Windows HD and the other the Ubuntu HD.  My windows HD has a number of partitions one of which holds a vast quantity of music, about 200gb of it.  

I have a standard home network with a combination of ethernet and wirelessly linked pcs round the house.  My brother who also listens to me does not have a great pc and could not hope to fit this music on the pc.  Before I started using Ubuntu the solution was simple, share the music partition on my windows xp HD over the network.  Doing this they could be effectively streamed round the house.

These files are stremed directly through windows media player and catalogued in the library there.  

When running windows on my pc this still works fine.  However when booting up Ubuntu I have no success whatsoever.  I have tried to find a guide that will help me sort this and have come up empty handed.  I'm hoping someone can tell me what i need to do this.  I have wondered whether the problem is that the music is on a completely different HD to the currently running OS but figure that regardless it must be possible to share the content of this drive over the network.

I also dont want my brother to have to type a password every time he tries to play a song.

I'd appreciate a set of instructions to do this or for someone to point the way to a guide that will help me.

Many thanks,

Eliphelet

---

### Post by Dr Small on 2007-11-03
Have you checked out Samba ?
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Eliphelet on 2007-11-04
I can see how this program would work to share files with other pc's on the network, and have tried this already.  But I cannot access the drives using this program.  They dont appear at all.

---

### Post by TeaSwigger on 2007-11-04
> **Eliphelet said:**
> I have just installed Ubuntu on my pc which was amazingly simple and not at all like the horror stories ive heard.

Yeah ubuntu is a sophisticated and shockingly easy to use OS. Enjoy :)

About sharing over a network, now that was pretty much the hardest part of my experiences so far. This guide was very helpful to me in figuring out enough of the mysteries to get my home network going:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by TeaSwigger on 2007-11-04
I'm trying to sort out the rest of what you wrote. Some points that come to mind:

About the PC which contains the music library; When you are in ubuntu, the drive containing the music must be recognized and mounted by ubuntu; you would then use Rhythmbox or any of a number of great native linux apps to play that music on that PC in place of Windows Media Player. If the drive and/or partition containing the music is kept in window's native NTFS filesystem, you should enable read/write support for NTFS in ubuntu so that it can mount and use that drive / partition.

In order to access that music on another (windows, correct?) computer in a home network; A working samba network must exist between the ubuntu PC containing the music and the other windows PC. Here is a guide which may be helpful as you wade through that samba stuff:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Once they are networked, you can use windows media player or WinAmp or what have you to play the music library on the other PC. :)

If the drive and/or partition containing the music library is changed to the linux file system, ext3, you can still do what you want to do, but you may have to install a (free) driver on the other windows computer which will allow it to read/write to the ext3 filesystem. 

Hope some of that at least makes sense. There are also other possible methods of serving the music to the other computer, but I'm not well versed on any of them, just putting you wise so to speak. Keep plugging at it and asking questions, you'll get it :)

---

