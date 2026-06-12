---
title: "Backing up Ubuntu?"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by akechi on 2005-08-23
Hello all,

is there a way to backup ubuntu, say to another partition?   i want to wipe a drive im using it on to test out gentoo on it.  im learning how to compile Gentoo soon in my comp networking / network security class and wanted to get a head start on it. but i dont want to loose all the time i put in to perfecting my ubuntu. I have a second drive im using for my multimedia with Ubuntu wich has plenty of room for another partition.   if there is a way, how would i go about backing it up (and what would i backup), and creating some room on the spare drive i have (partition it, how?).  and then moving it.   i've found no utilites like windows to do it for me.  and if i can do this sucessfully,  how would i go about restoring it after im finished practicing my gentoo compile?

Thanks in advaced for any help,  i really love ubuntu and REALLY dont want to install it all over again,  thats one reason why i left windows >_<

Ron-

---

### Post by Juergen on 2005-08-23
If you have free space, why don't you just install Gentoo there?

To move Ubuntu you can just copy the whole system with 'cp -a' or, to create a 1:1 clone of a partition to one of the same size use 'dd' (look at the man-pages for those commands)
Unlike Windows there are no 'system' or 'hidden' files that somehow can't be copied.

You should do this running from a live-CD, though, to avoid demons writing on your source-partition while the copy is in process.

If you modify /etc/fstab of your copy and create an entry for grub (and probably re-install grub from its copy), you should be able to run Ubuntu from its new location without problems (but, again, you could also install Gentoo there, and avoid the whole 'backup')

To delete/create/resize partitions on your 2nd drive look at (g)parted (its in the repositories).
But you should probably backup THAT drive before you start fiddling with the partitions...

---

### Post by TristanMike on 2005-08-23
You could read this wiki....[https://wiki.ubuntu.com/BackupYourSystem](https://wiki.ubuntu.com/BackupYourSystem)

 :)

---

### Post by akechi on 2005-08-24
Thank you all for the info and the Wiki (should have looked there to begin with >

The reason im doing it this way is,  we're also in the process of preforming disaster recovery on all our win 2k/xp/2003 machines.  i figured i could get linux to do the same in case anything ever happened to my machine.  better safe than sorry.  and i figured that it would be good to learn regardless.    what i really want to know is, using the method above, can i keep that copy of the system i will make, and then periodically make incremental backups to it?  if so,  how would this be done?

once again, thanks for all the help.
im just one of those ppl that, even if its not necessary, i  still like to try it to know :)

---

