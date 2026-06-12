---
title: "Will This Work?"
date: 2008-11-11
forum: Apple Hardware Users
---

### Post by gclown on 2008-11-11
Ok, a little background. I am currently running windows xp and osx on a macbook pro (santa rosa). Everything is peachy, but I want to try ubuntu natively. According to the ubuntu documentation, triple booting is as simple as installing xp via bootcamp and partitioning your macintosh hd again creating a partition that an ubuntu boot disk can reformat to whatever format ubuntu uses. It is not that simple (correct me if I am wrong). Heres how it works when I follow the ubuntu guide. I try to repartition my macintosh hd to include a 60 gb mac hd, and a 20 gb linux partition (that can be reformatted later). All of this would be done leaving the ntfs windows xp partition essentially by itself. Here are the problems:

1. I get a warning saying that if i repartition my mac drive it might make windows xp (bootcamp) unbootable.

2. Who cares about the warning ill take my chances booting with rEFIt. Even then after I try to do my partitions it stops me with an error saying "unable to partition macintosh hd Filesystem verify or repair failed."

I figure that having the ntfs partition with windows is stopping me from repartitioning my hd. Here is my proposed plan (feedback/ feasibility report needed)

1. Back up my bootcamp partition to an external hd via winclone. This creates an image of the windows partition that would be able to be easily restored to a partition on my computer.

2. Destroy the bootcamp partition leaving everything for mac.

3. create a 20 gb partition for linux

4. recreate my bootcamp partition and restore windows.

5. install unbuntu onto the 20 gb linux partition. (should i do step 4 or 5 first?)

6. Install refit to so that i can boot all of my os's (this could/should go first)

Does this sound feasible? Is winclone able to be used in this way? Will formatting the 20 gb linux partition create problems or even work?

Thanks for any replies.

---

### Post by cyberdork33 on 2008-11-11
go ahead and install refit up front.

That error message is about your OSX partition. It seems to have a problem. Try booting from the OS X install disc and running DiskUtilty to check the partition there.

---

### Post by gclown on 2008-11-11
so if i am able to fix my disk and partition out my macintosh hd, what should i format it as? Also, when I am installing ubuntu, will it be able to find that partition and repartition it into three linux partitions (home, swap, root? not sure what they are called)?

---

