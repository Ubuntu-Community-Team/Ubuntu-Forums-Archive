---
title: "[SOLVED] Preparation to upgrade - specifically MySQL and /home"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by flamingsole on 2008-01-26
Hello,

Currently, I'm still running Feisty, as I had a fairly large freelance project I had to finish, and didn't want to have to worry about losing any data. Feisty has been my first experience with Linux.

In any case, I'd like to upgrade to Gutsy now, and have a couple of questions about the best way to do this. I do have separate partitions for /, /home, and boot. Also, I run XP in a dual boot on this system. It has a 200 gig hard drive, and a 250, and 2 gigs of RAM.

I just downloaded and verified an install CD, as I plan to upgrade from a clean install. My main question is: how do I upgrade in this manner without losing the data on my /home partition? My assumption is that there might be an option during the install, but I wanted to ask before I get that far.

My second question is very similar. I have a lot of MySQL databases on this system, and would like to ensure that I don't lose them. I realize it's a bit more of a MySQL question than it is an Ubuntu question, but where is the actual data stored, so that I can ensure that I don't lose them?

Any advice is most appreciated. Thanks.
Jonathan

---

### Post by shad0w_walker on 2008-01-26
During the install it will ask about partitions, When it gets there select manual and you can select what partitions to use for what. You can select your root (/) partition and choose to only format that. You will need to select what each partition is mounted as.

For the SQL tables I assume you have a knowledge of SQL so just do the usual backup of them. I believe if you really want to take the files themselves they are stored in  /var/lib/mysql/<database name>

You will probably need to be root to gain direct access to those files though.

---

### Post by flamingsole on 2008-01-31
Thanks for your help on both of those. My upgrade came right after I bought a new monitor, and I couldn't figure out how to fix the configurations so that Feisty would not say "monitor out of range." So, I upgraded, and Gutsy recognized it.

Hence the reason for needing to backup the MySQL databases: Windows could see and copy from the directories, but I couldn't actually get into the system.

Anyway. Thanks again.

---

