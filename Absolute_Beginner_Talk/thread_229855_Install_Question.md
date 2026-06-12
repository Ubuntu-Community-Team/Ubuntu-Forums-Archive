---
title: "Install Question"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by djmoffat on 2006-08-05
I'm installing Ubuntu for the first time. I have copied a lot of my data to this hard drive from a failing one, and I was wondering if Ubuntu will 'erase' my drive first as part of the install, or will my data remain untouched?

Thanks,
Dave

---

### Post by benuski on 2006-08-05
You will have the option to erase the entire hard drive, or you can manually edit the partition table, which means you`ll be able to create a separate Ubuntu partition, leaving all your other data entact.

---

### Post by not_yet on 2006-08-05
during install you will be given the option of erasing the entire drive, or just using that portion that is unused.

---

### Post by djmoffat on 2006-08-05
Thanks! That is exactly what I was looking for. So, there is no way for me to add Ubuntu to the existing partition with my other files. I pretty much need to have a new partition for Ubuntu?

What is the best option for "Filesystem"?

---

### Post by OU812 on 2006-08-05
This should answer some of your questions

[http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html)

But in a nutshell - one way or another you need a minimum of two separate partitions for ubuntu: swap (uses a chunk of your hard drive as memory storage) and root (for everything else). So if you choose to install ubuntu in the unused space of your win drive, you can set up ubuntu to access your win drive.

john

P.S. Before you go for it, back up your data, defrag your drive and run scandisk.

P.P.S. Are you from CA?

---

### Post by djmoffat on 2006-08-05
This drive does not have win installed. It was a second hd in my system with my junk on it. Now I want to install Ubuntu on it, but I really only want one the two partitions. From what you are saying it sounds like I could make two partions from the existing drive.
1) root (currently has all my junk on it, but could be resized to allow for swap)
2) swap (create this new)

Does that sound correct?

No, I'm from Minnesota

---

### Post by OU812 on 2006-08-05
I'm confused. Let's recap. The "old" drive is failing, so it has to go. The "new" drive has the files from the old drive that you want to keep. Now you want to install linux on it? If this is true, I think you have two options:

1. I think you can let ubuntu install itself automatically in the unused portion of your drive. Then you'll have three partitions - one for your recovered files, and the two I mentioned for linux.
2. You could create the partitions yourself. This way you could also add a "home" partition, which is usually a good idea. To do this, however, would mean running qtparted from the livecd and creating a partition on your "new" drive for linux (so the first will have your files and the second will be for linux). After that, you can click the install icon. If you choose this option, please click the link from my previous post.

john

P.S. I work with a guy with the named moffat who's a dj. Had to ask.

---

### Post by djmoffat on 2006-08-05
Thanks for the tips. I liked the link gave me some ideas I had not thought about.

I like the idea of a different "/home" partition!

Dave

---

