---
title: "backing up"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by djcawthorne on 2006-09-22
i am trying to backup my ubuntu directory to the root directory using the following code:

tar cvpzf backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media

all goes well apart from it does not exclude the /media folder... which contains a mounted drive from windows containing 100gb of data i do not want backing up...hence the exclusion! 

any ideas where im going wrong?

thanks in advance

Dave

---

### Post by EddieA on 2006-09-22
is that the entire code?
Shouldn't the last item in the list be the directory to backup to?
and shouldn't there be a hyphen '-' before the cvpzf

---

### Post by djcawthorne on 2006-09-22
thats the entire code. the code works, just doesnt exclude the /media folder.....the link i got the code from is as follows [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) all i have done is added the "--exclude=/media" section at the end. am new to Ubuntu and linux....its possibly a mistake on my part. 

thanks

---

### Post by chrisfay on 2006-09-22
> tar cvpzf backup.tgz / --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/media

The folder/file that you want to backup needs to be added at the end or your excludes won't work. This was noted towards the end of that thread you linked.

Ex.

To create a backup called backup.tgz and backup your entire root directory to /mnt/share it would look like this:

```
tar cfvPz /mnt/share/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/media / 
```

Notice the '/' at the end which is what's being backed up.

---

### Post by EddieA on 2006-09-23
Yes My mistake regarding the last item   :oops:  - if you look at this link 

[BackupYourSystem]("https://help.ubuntu.com/community/BackupYourSystem")

This code works:

```
tar -cvpzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```

and will back up your root directory minus excludes to '/backup.tgz' .
Notice the difference with the '/' on the end as per previous post.
Aslo notice the difference in this bit 'tar -cvpzf /backup.tgz ' - I think this is an edit of the post you linked to - I used this code( with my own edits for directories etc).
This should be OK :)

---

### Post by djcawthorne on 2006-09-24
thanks guys. both been a great help. i am now backed up :)

---

