---
title: "Disk full, can't log in"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by freesitebuilder on 2007-10-10
Had a brainstorm yesterday, and ran Simple Backup, backing up my home folder to my Ubuntu home folder - don't ask! :(

Now of course I can't log in because my disk is full. I've tried deleting the file through th terminal, but I don't have permission. I can see the file in XP using Linux Reader, but of course I can't delete it, I can't see the file through Nautilus.

I've tried the Live CD, and tried sudo in terminal, but I can't delete that file.

How can I get rid of it? I've looked at the other posts covering this, but my main problem is the file permissions.

TIA

---

### Post by phr0ze on 2007-10-10
Are you preceeding the delete command with SUDO?

sudo rm filename

---

### Post by Pumalite on 2007-10-10
Try Knoppix. You appear as root in the terminal and it mounts all your partitions automatically.

---

### Post by Delvien on 2007-10-10
with the knoppix  live CD you should have access to it in terminal, you should be able to either mount the drive with the live cd or it will detect it correctly.


then put in 

```
 sudo rm -r /PATH/TO/FILE 
```

This will skip it going to trash and delete it from your hard drive, freeing space

PLEASE NOTE this is a powerful command, make sure you have the path right.

If this does not work reply.

---

### Post by freesitebuilder on 2007-10-10
In the terminal I can change to /var, typr dir and see the problem directory listed. sudo cd then tells me that the directory doesn't exist. sudo rm /dir/filename also tells me the directory and filename don't exist.

I'll try downloading Knoppix if I can.

Something that worries me is that I can't even see the filename in Linux - I had to use Linux Reader (XP) to get the filename. Nautilus just tells me I don't have permission to view the directory contents. If I only had Ubuntu (which is my main aim) how would I find the filename?

---

### Post by dptxp on 2007-10-10
Use Puppy Linux. Much smaller than knoppix.

---

### Post by freesitebuilder on 2007-10-10
I managed to chmod the directory and then the rm -r worked - now I'm back to normal. Thanks!

---

