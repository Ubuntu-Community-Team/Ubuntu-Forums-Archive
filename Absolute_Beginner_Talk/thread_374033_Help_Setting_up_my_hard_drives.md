---
title: "Help Setting up my hard drives"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by mahiyar on 2007-03-02
HI,
I have been using Ubuntu since December, and now fairly well settled in it and I love my system. Currently I have a single IDE drive on which I'am dual booting Ubuntu. I'am currently planning to migrate to SATA drive and retain my IDE drive as a seconadary device with windows. So basically there will be one primary SATA drive fully dedicated to Ubuntu/Linux. And another Secondary IDE drive having WIN XP professional. Now my question is what is the exact way to go about it? I'am not worried about the installation part but about grub, fstab entries etc.

---

### Post by yabbadabbadont on 2007-03-02
Sometimes grub doesn't like it much when your /boot partition is on a sata drive.  It works for some people and not for others...  Your safest course would probably be to leave a small /boot partition on the IDE drive and then put the rest of Ubuntu on the sata drive.  256MB is plenty for /boot.

---

### Post by mojorising on 2007-03-02
This might be a little tricky. 

The first thing you should do is back up all your important data (docs, photos, etc) to CD or DVD, etc.

I would probably make an image of the old Linux partition and put it on the new drive using something like ghost 4 linux ([http://sourceforge.net/projects/g4l)](http://sourceforge.net/projects/g4l)). If you need to create or resize partitions, a great and easy to use graphical tool is gparted ([http://gparted.sourceforge.net/livecd.php)](http://gparted.sourceforge.net/livecd.php)).

Of course, an easy but time consuming solution is to simply install Ubuntu on the new HDD and copy your documents and such over to it after you are done -- this is the way to go if you haven't customized your setup or installed a whole bunch of applications very much. 

Those are just some ideas of mine. Someone else out there may think of a better strategy. 

Mike

---

