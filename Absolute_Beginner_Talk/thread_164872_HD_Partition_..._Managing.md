---
title: "HD Partition ... Managing?"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by MHlavsa on 2006-04-23
So after reading a good article on partitioning ([Link]("http://fool.newsvine.com/_news/2006/03/25/142090-dual-booting-windows-linux-partitioning-for-the-curious")), I've come to the realization that I need to set up my computer if I'm going to continue using Ubuntu a lot.  Right now I have my XP side, and then the partition I just created for Ubuntu.  I'd like to set up a FAT32 section to store music and other files to be accessed by both, but still keep a decent NTFS to run a few games.  Is there a way to manage all this without completly wiping my HD and reinstalling everything?

Thanks guys!

---

### Post by zukakog on 2006-04-23
I've used tons of partition managers for the same thing.  gparted seems to be the best in linux, but sometimes it has a hard time resizing ntfs partitions.  Partition Magic 8 seems to do the best, but it's not (usually) free.  Another option is to install [ext3 drivers in Window$]("www.fs-driver.org").  It works great for me.  You can access your whole linux partion from windows.

---

### Post by uzi09 on 2006-04-23
lol,

i had the same exact issue when i was dual booting -- check out this thread:

[http://ubuntuforums.org/showthread.php?t=151722](http://ubuntuforums.org/showthread.php?t=151722)


incase ur curious: i set mines up with a partition for windows(ntfs), one for ubuntu (ext3), and one for home (ext3). i installed the driver in windows and was able to get/use my stuff from linux no problem. i also used qtparted which worked perfectly fine for me -- i'm not sure what issues zukakog ran into when he tried it, but from what i've seen, it's a partition magic clone and it's FREE!

one thing i noted though, it seemed the /home partition was kinda useless (for me anyway). i could have just as easily had a xp(ntfs) partition and an ubuntu(ext3) partition and just used the driver to still access my files in the /home directory. i think i'm going to be setting it up this way the second time around - no need to have all these partitions :S

one thing to note though: if u did have a /home partition, when u're installing that driver in xp to read/write from ext3 partitions, u have a choice to which partitions u want shown. if u had a seperate partition for /home, u could ensure safety of the rest of the file system so that incase u ever got a virus, it wouldn't end up screwing up all of linux as well. not only that, if u have other people using the computer who aren't as familiar with linux, then they won't be able to touch those files either.
for me, i'm the only one using it, and if i remember correctly, i haven't touched  xp ever since i had ubuntu installed =D. i just have it there JUST IN CASE, but haven't had to use it yet - so hopefully i won't run into the virus problem described above ^_^.

good luck,
uzi

---

