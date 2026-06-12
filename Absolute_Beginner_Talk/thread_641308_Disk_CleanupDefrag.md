---
title: "Disk Cleanup/Defrag?"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by KudoKid on 2007-12-15
Having been a Windows kid for the last...oh 14 years...and just switched to ubuntu going on 3 weeks ago, i am still used to a lot of cleanup work. I'm loving not needing to run spybot and nod32, Saves time and space...
But i think i still have to run disk cleanup and defrag, However, I have to idea how! So could someone tell me how to run these two? and if there are any other cleanup tools i should run? thanks a ton for any posts i get. =)

---

### Post by Taboo Mirage on 2007-12-15
There's no need to defrag the drive because of the way that the filesystem works; it keeps fragmentation to a minimum by default.

For disk cleanup, [this](http://ubuntuforums.org/showthread.php?t=140920) might help.

Take care.

---

### Post by KudoKid on 2007-12-15
Thanks sooo much! =P thats helps a ton.

---

### Post by Paqman on 2007-12-15
You might have also noticed that the system automatically checks your partitions for errors every 30 mounts. You'll see it occasionally at bootup.

---

### Post by Devport on 2007-12-15
> **Taboo Mirage said:**
> There's no need to defrag the drive because of the way that the filesystem works; it keeps fragmentation to a minimum by default.

For disk cleanup, [this](http://ubuntuforums.org/showthread.php?t=140920) might help.

Take care.
This depends on the filesystem - and I dont see that the author mentions which one he uses. Furthermore all current filesystems suffer from file fragmentation over time. It is one of the features of the upcoming file systems ( ext4 / reiser4 ) that they will heavily **decrease** fragmentation compared to their predecessors.

Here is one of many docs confirming e.g. that ext4 does **less** fragmentation than ext3 :

[http://www.usenix.com/publications/login/2007-06/openpdfs/mathur.pdf](http://www.usenix.com/publications/login/2007-06/openpdfs/mathur.pdf)

Sadly there is not yet any defragmentation tool I know for any file system. But as I understand it there is one planned for ext4, see doc above ( which wouldnt be the case if fragmentation would not be relevant, even with the improved ext4 ).

Personally I experienced a major slowdown with reiserfs3 over time. See also :

[http://talkback.zdnet.com/5208-12694-0.html?forumID=1&threadID=32450&messageID=597855&start=-9960](http://talkback.zdnet.com/5208-12694-0.html?forumID=1&threadID=32450&messageID=597855&start=-9960)

---

### Post by Taboo Mirage on 2007-12-15
I took an educated guess that a new user displaying they were using Ubuntu 7.10 as part of their profile that they were using the ext3 filesystem.  I'm certain I'm accurate on this count.

Referring to the [Linux System Administrator's Guide](http://www.tldp.org/LDP/sag/html/filesystems.html), section 5.10.11:
> Modern Linux filesystem keep fragmentation at a minimum by keeping all blocks in a file close together, even if they can't be stored in consecutive sectors. Some filesystems, like ext3, effectively allocate the free block that is nearest to other blocks in a file. Therefore it is not necessary to worry about fragmentation in a Linux system.
I personally have never seen fragmentation as a problem in ext3 filesystems on any system.  Fragmentation itself is almost a fairly moot point these days with the general performance of modern hardware; the small amount of fragmentation on an ext3 filesystem will not significantly impact performance on such systems.  I think to imply that it does to the extent you are doing is fairly unrepresentative of the general state of play, for the ext3 filesystem anyway.

I have no comments about ReiserFS.  I know of no major distributions that use this these days as their default filesystem now that Novell switched to ext3 for OpenSuSE as of 10.2.

Take care.

---

