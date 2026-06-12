---
title: "merging /home partition and / partition"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by bruenig on 2006-08-07
I want to know how to merge these partitions(/ and /home) together. I figure the easiest way is to put in the live cd and do it with gparted or the like, but I am not certain exactly how I would do that. I don't want to lose any of the files. I suppose I could always backup the /home directory. Delete the partition and then make the / partition bigger at which point I replace the /home directory but just looking for an easier way.

---

### Post by Indras on 2006-08-07
It's probably going to be messy.  By far the best thing you can do is make a backup first.  After that, the way I would go about it is boot to the live CD, mount both the / and /home partitions to separate folders (like /rt and /hm) and copy things from one place to the other.
```
sudo mkdir /rt/home/
sudo cp -R /hm/* /rt/home/
```

Then, verify that everything in /rt/home/ matches your old /home partition.  Modify your fstab file to remove the reference to your old /home partition...
```
sudo nano /rt/etc/fstab
```

Then, unmount both partitions, delete the /home partition and gparted, and stretch your / partition to fill the freed up space.  After that gets applied, if your /home partition was before your / partition on your drive, that will change the partition number that your / partition is on, which means you'll have to update your /etc/fstab and /boot/grub/menu.lst to point to the new partition number.  So, remount / to /rt and edit those two files, then save and try to restart.

If it doesn't work, you backed up, right? :)

---

### Post by Anduu on 2006-08-07
Ideally you *want* / and /home seperate.That way you can reinstall without losing all your important data....

---

### Post by bruenig on 2006-08-08
Indras, much thanks. The only problem with your instruction is ownership. If /home is not owned by the user, ubuntu gets mad and you can't boot into it. Doing what you say changes the ownership apparently

I just did a quick ctrl+alt+f1 to get to a prompt and then did a sudo chown -R username /home to get it back.

---

