---
title: "problem with unmounting a secondary hdd"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by 713aggie on 2006-12-13
So when i installed, i did not know where to mount my secondary hdd, so i mounted it to /usr. i tried using
sudo umount /dev/hdb1 but it said the device was busy.

What does that mean, and how do i solve the problem. Basically I want to unmount it, and remount it to a place where i can store my music and video files. So the second question would be, after i unmount, what is the best place to mount it (where i can also share it on a windows network)?

Thanks.

---

### Post by taurus on 2006-12-13
You have to boot your machine with the LiveCD, then mount the partition where / is.  Now, you need to edit /etc/fstab on the harddrive to mount your /dev/hdb1 somewhere else instead of /usr!  However, there could be a problem because all kind of programs already installed in /usr so if you mount that partition somewhere else, your machine won't work...

---

### Post by disabled_20220313 on 2006-12-13
Erm, not quite sure how to help.

Running the command
```
mount
```
in the command line would provide you with information about where your 2nd hard drive is mounted, and hopefully a clue to why its still being used... Post the output here for us to help you.

Once you do have it unmounted. The best option would be to mount the drive to /home and keep all the home directories on that drive. I have this set up, so it is possible to do, relatively easily.

I used this guide [here]("http://www.ubuntuforums.org/showthread.php?t=46866").

It means when you re-install your OS, without touching your personal documents.

Good luck

---

