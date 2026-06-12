---
title: "mandriva dual booting"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by online14230 on 2006-10-09
Good aftermorning peoples,
Heres a small problem: I partitioned my HDD such that Ubuntu boots off hda1 = 5 GB, Mandriva boots off hda2 = 5GB, and both share a /home on hda3 = 9GB. 1 GB allocated to swap at hda5. Dont ask, its what GParted did.
Now Ubuntu logs me out as soon as I log in, and tells me "Users $HOME/.dmrc is being ignored. Ownership should be 644 and nobody should have write permissions."
In ~/.x-session-errors, it says "beginning session setup
Could not set mode 700 on private per user gnome configurationdirectory /home/brendan/.gnome2_private
operation not permitted."

Can Mandriva and Ubuntu live in the same home? :)
If not, how would I fix it so that ubuntu /home is on hda1 and Mandriva /home is on hda2, while they actually share documents and media files and the like on hda3? Without re-installing? Please? Help me? Please???


_________________________________________________________________
B.: Expert Ubuntu Breaker. Login to broken in 10 secs!

---

### Post by gonesolo on 2006-10-09
I'm not expert but I'd have to say no. surely each distro would have differences in how they save user preferences etc which are all stored in your home folder.

Possibly you could do it if your login name for each distro is different but as I said I'm no expert.

As for changing it with out installing, if you can change your mapping for your /home folder to being on the same drive as each OS is installed then you should be able to do it without installing but as a relative linux newbie I have 0 idea how you would do it. 

Sorry.

Sharing the "shared space" should be easy enough just probably not as /home

---

### Post by Xappe on 2006-10-09
moving your home dir is not that difficult. 

If you have your /home on another partition than root, it's mounted at boot through a line in /etc/fstab.

If you want to have your /home on another partition,just edit that line so that it points to your new home partiton. Copy the user dir from /home to the new partition using "cp -a" and reboot.

I guess that should be it, but I recommend that you make backups of all important files in your /home (and of the files that you're editing) so that you don't loose any data if anything goes wrong.

If you want to share a partition between the two distros, just use a spare partition and mount it on both systems using fstab.

---

### Post by online14230 on 2006-10-16
Thank you all for the advice. Now, I have a 9 GB partition doing absolutely JACK! With Mandriva AND Dapper booting beautifully, alls well. I can read from the partition, but I cant open any files or write to it. How would I set it up so that Ubuntu and Mandriva both have complete access to it? Also, Ive found that there are still files on the partition, from when I moved off the partition. What do I do with them? One more thing: DVD's are choppy, and some dont even play. At best, they just start and quit, with all that rubbish about libdvdcss2 and the like. Believe me, Ive followed ALL the tuts and how-tos and stuff, but nothing works... Also, my Benq DVDR ONLY writes at 1x! HELP! X-CD-ROAST wont even start, saying root has to set it up first. Im seriously thinking of taking to the PC with a hammer!!!

---

