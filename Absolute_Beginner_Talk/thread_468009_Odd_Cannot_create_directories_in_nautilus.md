---
title: "Odd: Cannot create directories in nautilus"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Jorge on 2007-06-08
I added a secondary drive to my system. I had two NTFS partitions on it, so I used gparted to remove one (45 GB) and created a replacement (same size) with ext3 format. 

Then I created a new folder "archivo" in /media and added this line in the fstab:

/dev/hdb1	/media/archivo	ext3	defaults	0	0 

So the partition gets mounted every time I start the computer. The odd thing is

I can make a new folder inside the partition using the "mkdir name-of-folder" in the terminal, but when I try to do the same in Nautilus (right-click in a blank area on the partition's content window), the options "create document" or "create folder" are dimmed, as it this was a read only disk...

But if I made a folder (through the terminal), then I can go inside that folder and Nautilus lets me create folder and documents.

Any ideas?

---

### Post by rich.bradshaw on 2007-06-08
what are the permissions on the drive?

Can you make a directory just by typing mkdir NAME, or do you have to use sudo?

---

### Post by Jorge on 2007-06-08
I just type mkdir NAME (no sudo)

If I use the icon Computer, in Nautilus, and check the permissions on the drive, they are set as: owner - root
group - root

---

### Post by Inxsible on 2007-06-08
you can change permissions using:
```
sudo chown -R <your username>:<your group> <path to device>
```
 
So assuming your username to be jorge and group to be jorge too
```
sudo chown -R jorge:jorge /media/archivo
```

---

### Post by Jorge on 2007-06-08
Thank you! But there's something still bugging me: on some other computer I had partitions set to root as owner/group but I am able to make directories from Nautilus as my user.

---

### Post by NeoLithium on 2007-06-08
It could have been set with permission for all to write, but the owner was still root, if that was the case :)  I have a folder on mine that is owned by root but it's Read/Writable for all users.

---

### Post by rfurman24 on 2007-06-08
I had an issue very similar to this. I could not change permissions using the sudo command or by logging in as root and trying to change permission that way. I had to manually edit the fstab to make it work.

---

