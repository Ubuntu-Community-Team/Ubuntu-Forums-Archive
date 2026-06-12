---
title: "alright, partitions."
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-29
yep, I finally decided to jump into the cold water of the partitioning world...

If I understood what I read correctly, then Ubuntu automatically partitions my harddrive into three partitions, when one is /home.

Now my first question is, if I want to reinstall ubuntu, or just install kubuntu(WITHOUT gnome), without deleting all my personal data, is that possible? if yes, how?

I don't have a big harddrive, i fact I've got a small one, about 20GB, is 10GB enough for ubuntu, so I can start expermenting with other distros?

Currently I'm in a bad situation, every time I try something new, be it the dapper, or reinstalling ubuntu, I need to start everything over, and if I plan, as I plan, to try debian, and others, my situation will be really bad...

So what can I do?
Oh, and I can't get a new harddrive, I'm using a laptop...
here's a screenshot of gparted, it doesn't give me the option of resizing a partition...

thanks...

---

### Post by RRS on 2006-04-29
During installation Ubuntu only creates 2 partitions automaticly, one ext3 for the OS and a small swap depending on the amount of ram you have.

To create a seperate home partition you need to select the manual option during installation. Your screenshot doesn't indicate this was done.

You can install Kubuntu, or maybe Dapper, assuming you want to experiment with different systems. During installation simpy select the manual partitioning method and reduce the sise of your current ext and use the free space for the new OS. They can share your current swap.

10g is more then adequate for Ubuntu. I installed Breezy about 4 months ago and have since upgraded to Dapper. All my "experimenting" has added alot of extra stuff and I'm still only using 6.5g.

Are you trying to run gparted from your installed system? If so it won't allow you to resize a mounted partition, hence the option not being available. 

If you run gparted from a live CD you'll be able to resize prior to performing any new installations. Or you could use the utillity in the install disc and then exit the install process.

I would recommend backing up any data you'd rather not use. Losses are rare but problems do occasional occur.

Hope this helps a little.

---

