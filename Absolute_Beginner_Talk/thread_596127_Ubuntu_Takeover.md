---
title: "Ubuntu Takeover"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by kbless7 on 2007-10-29
So I have a somewhat serious situation. I loaded Ubuntu on my external hard drive and instead of partitioning it like I told it to, it took over the whole drive. Now when I operate in XP I can't even access my external. It recognizes that there is a mass storage device connected but it doesn't show up in "my computer."  Also I can't save anything to the external when I'm in Ubuntu. It says I don't have ownership of the drive even though I'm the admin. So whats going on guys? Thanks for any help. 



-Matt

---

### Post by hyper_ch on 2007-10-29
I guess you didn't say the partition right and just chose the wrong partitioning scheme...

Windows cannot handle Ext3 on its own. Either you will grab the Ext2/3 drivers and install them in winows or you'll have to resize the ex3 partition and create another one on that drive.

---

### Post by Inxsible on 2007-10-29
Looks like you bit the bullet too soon. If it took over the entire external drive, you must have selected that option. All your data on there external(if there was any) is most likely lost.

XP won't be able to access EXT3 partition unless you install Fs-driver [www.fs-driver.org]("http://www.fs-driver.org") About you not being able to write to external from Ubuntu as well, thats how its supposed to be. you can only write to your home directory.

If you need to make changes outside your home folder, you need to supply the root password that you created during installation.

Please read up on [installing]("http://ubuntuforums.org/www.psychocats.net/ubuntu/installing") and [partitioning]("http://ubuntuforums.org/www.psychocats.net/ubuntu/partitioning")

---

### Post by taurus on 2007-10-29
If you want to access your external harddrive with Ubuntu on it, you need to install this app first in windows, [http://www.fs-driver.org/](http://www.fs-driver.org/).

You are NOT an admin on your machine even though you are the only user on it.  However, you do have a root privilege to modify system files by using sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kbless7 on 2007-10-29
Ok. How can I completely unistall Ubuntu to where it was like it never happened. I think this might be easier, then I can start over and do it right.

---

### Post by Inxsible on 2007-10-29
> **kbless7 said:**
> Ok. How can I completely unistall Ubuntu to where it was like it never happened. I think this might be easier, then I can start over and do it right.
if you have nothing but Ubuntu on your external, you can use GParted on the LiveCD and simply format the entire external drive. Be careful to back up all the important data if you have any.

---

### Post by sailor2001 on 2007-10-29
if you are reinstalling windows, it will format your entire drive and install. Ubuntu gives you the option to partition the drive (for dual boot). but that is done after windows is installed

---

