---
title: "Share partition with music with Ubuntu and XP"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by BradwJensen on 2007-05-05
I have a problem,

I have no money, ONE hard drive, and a TON of music on a partition. I also have another partition with Windows XP on it..  I would love to get into Ubuntu, but i want to be able to keep a partition with windows xp for a few programs that i can't run on Ubuntu til i get used to Ubuntu and find good programs to replace those..

The things is, if i install xp and ubuntu on 2 different partitions and keep all my music on my one NTSF partition that i already have, can i access the music on that partition from both Ubuntu and Windows XP?

If this is possible to set up, how would i go about doing this?

I have installed a version of Ubuntu before while keeping my music on that NTSF parititon but Ubuntu never shows or recognized the music partition..  I'm lost and need help!

Thanks to anyone who might help me here!

---

### Post by bobplano on 2007-05-05
for ubuntu to read ntfs you need nts3g. [here]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs3g") is a howto

---

### Post by BradwJensen on 2007-05-05
> **bobplano said:**
> for ubuntu to read ntfs you need nts3g. [here]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs3g") is a howto

Well.. would it be easier if i just put all my music on my ipod, then formatted that music partition to fat32, and put all the music back on it?

Then would both xp and Ubuntu access it?

---

### Post by bobplano on 2007-05-05
you could, but setting up ntfs3g isn't that hard. you just add the repos (if you're not using fiesty) and then run
```
sudo apt-get install ntfs-config
```
then it will be under apps>system tools and then you choose the name of the mount point(defaults to /media/*name*) then you have access to your windows. the ipod would also work, but i don't know how much more or less trouble that would be

---

### Post by BradwJensen on 2007-05-05
> **bobplano said:**
> you could, but setting up ntfs3g isn't that hard. you just add the repos (if you're not using fiesty) and then run
```
sudo apt-get install ntfs-config
```
then it will be under apps>system tools and then you choose the name of the mount point(defaults to /media/*name*) then you have access to your windows. the ipod would also work, but i don't know how much more or less trouble that would be

Thank you very much for your help :-)

---

