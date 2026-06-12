---
title: "* Stopping MySQL database server mysqld"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by osc1882 on 2007-03-23
Ok,
So the auto updater program informed me that I needed to update a whole ton of things and I agree'd. And everything installed but automatrix2

If you pulled down the detail tab it said this:
(Reading database ... 282879 files and directories currently installed.)
Preparing to replace automatrix2 1.1-2.28-6.10edgy_1386 (using .../automatrix2_1.1-2.29-6.10edgy%5fi386_i386.deb) ...
Unpacking replacement automatrix2 ...
Setting up mysql-server-5.024a-9ubuntu0.1) ...
 * Stopping MySQL database server mysqld

Now I typed that junk out by hand in case you see something wrong in there.
After a few times of trying it gave up and now it's not even on my list of programs to upgrade and I'm pretty darn sure that it didn't up grade.
Now I'm not writing because I'm sad that I don't have the newest version of automatrix, but I am wondering if anyone can give me any tips on what to do should that happen again.

Also, I ran out of hard drive space on my Ubuntu partition yesterday and after some playing around I found out that, it was because I was saving a very large torrent on a external hard drive but I still had my temp folder for ktorrent set to my Ubuntu partition. I'm pretty sure that cleared up a bunch of space, but can anyone tell me how to check my Ubuntu partition's free space?


:popcorn:

---

### Post by Muzik83 on 2007-03-23
Hey,

First on the mysql thing, was anything using mysql at the time?  Perhaps amarok playing music, mythtv recording something, or someone on your website (if you have one).  In the future, you can manually stop mysqld by doing an
sudo /etc/init.d/mysql stop

Then at least the dpkg transaction wouldn't time out.

Second, from the terminal you can type 
df -h
(stands for "disk free -humanreadable").  It will show you the disk size, disk usage and %free

Apt will cache packages when you do apt-get install or apt-get update.  This can quickly grow quite large, and it's a good idea to clean it out from time to time.  You can do this by
sudo apt-get clean

-sean

---

