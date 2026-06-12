---
title: "One important thing for beginners"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by doobit on 2007-02-07
I have become convinced that one important thing that beginners should do when they are installing is to set up a separate /home partition. I know that can be a little confusing because of the way the partitioner prompts you during setup, but working through it will be worth it in the end. If you are dedicating an entire hard drive to Ubuntu, then make three partitions. They can be primary or logical, but the first should be / and have a boot flag, the second should be a swap and twice the size of your RAM, and the third should have the /home label. 

The same is true for a dual boot install except your partitions will all follow the first primary partition which will be Windows.

Having that separate home will allow you to backup and restore or upgrade much more easily because your settings and user accounts are kept on that partition.

---

### Post by crane on 2007-02-07
Good suggestion. The only issues would be if they tried a different distro and mounted the home partition again. Could have some problems. I have a few partitions. One partition ids just for games (quake3,4, UT2k4,Cod, WoW, etc) That way I don't have to reinstall my games for any os install or change.
 If re installing, it is always good to back up your stuff even if you have a sererate home partition.

:guitar:

---

### Post by punx45 on 2007-02-07
i am a member of the /home partition club.
though, i havent had to do any recovery work to make it necessary.

---

### Post by rsambuca on 2007-02-07
If I ever have to, I just do a complete re-install.  It is a good excuse for changing themes, etc!  Also, you learn a lot more at the beginning if you work from scratch, I think!

---

### Post by r4ik on 2007-02-07
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

For those who want to create one.

---

### Post by bodhi.zazen on 2007-02-07
Not to be difficult, but I am not a fan of a /home partition.

Backup/restore is no easier or harder with or without a separate partition, this is irrelevant.

Saving your data if you re-install an os is, however, very helpful.

Thus I suggest a /data partition.

You should back up all your essential . files (like .bashrc), but there is no need to preserve most of the . files in /home.

If you use a data partition you can link to it in /home

Like this: ln -s /data/music /home/user_name/music

Now you can share all your data across OS without fear of conflicting . files in /home. Although conflicts may be rare, they can be a pain if you share one /home across multople OS of various age.

Just my 2c

---

### Post by punx45 on 2007-02-08
i could see the /home partition being more useful for multi-user systems that actually have multiple users, and they have varying levels of access to other parts of the system.   but for a single user system (which most of our systems are likely to be) what bodhi.zazen suggested seems to be a practical solution as well.   Especially for someone like me who has a / partition that is 81% full and a /home that is 10% full...:roll:

---

