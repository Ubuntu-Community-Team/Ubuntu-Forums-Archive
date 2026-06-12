---
title: "file permissions and backups"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by kel on 2006-03-01
Hi, I'm new to ubuntu and linux so please bare with me :D

I've had to reinstall ubuntu due to a broken installation, but it seems to be working fine now.

Problem is that I backed up some files to CD before I reinstalled (eclipse and my workspace mainly), problem is that when i copied these files back to my home folder they now have little lock icons attached to them and eclipse won't run.

I've noticed that i can go through every file and set the permissions manually but eclipse has a ton of files and some hidden ones to so this isn't very practical.

So what are my options here, how can i get these files back working again, and for future reference, what is the best way to back up files to cd to avoid all the permissions trouble.

worth noting that i did change my computers name after the re-installation, is this the cause of the permissions trouble?

thanks


[edit]  Ahh, found the solution, looks like i need to use Chown i think. 
I'd delete this thread but i'm unable to :D

---

### Post by aysiu on 2006-03-01
```
sudo chown -R kel:kel /home/kel
```

---

