---
title: "scheduled backup"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Matrix1 on 2007-10-26
I have an external USB hard drive and would like to marry to Ubuntu 7.10 for auto scheduled backup.  Does anyone know how I can make this happen?  How does anybody on this forum do auto scheduled backup?  thanks. The external hard drive came with the schedule backup program called Prospect and I was using in XP for auto scheduled backup.

---

### Post by sancho panza on 2007-10-26
You can use [Sbackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite?highlight=%28sbackup%29") for a simple backup requirements.

---

### Post by mdpalow on 2007-10-26
Thanks Sancho for posting the SBACKUP link. I like it. However, while reading the link there was only one part that was confusing. It reads:

"Note: By default, Restored Files and Directories are owned by root This is because sbackup runs with root priveleges. You need to change these file or folder permissions using chmod, or just right click and select properties of the file or folder."

This one statement just made a simple program a little harder - for me anyways.

A backup will have hundreds of folders. How would you know what all the folders original permissions were in order to change them? Changing all the folder permissions seems ridiculous, so I MUST be missing something.

Would you simply change the /home folder to be owned by you and everything else to root?

Please explain and keep in mind that I'm a Linux newb....

---

### Post by sancho panza on 2007-10-26
Hi...
I'm sorry I had not noticed that issue earlier. You are meticulous :) I think its a major issue which should get fixed. Thanks for pointing that out. I dont know any GUI based easy way to do it. Or am I missing something?

But I'm sure there would also be a quick command line way (using *chmod* command) to easily change the permissions of a large group of files, but havent used any yet.

I dont have the time to actually file a bug report and follow them thru, so could some one please follow up on this?

---

### Post by mdpalow on 2007-10-26
Hi Sancho,

I'm a newb at Linux/Ubuntu, so I wouldn't even know how to suggest this fix and follow-up with it. :) However, if you give me a brief explanation on how to do it - I'll be able to do it in the future.

I think the easier way to do a back-up would be to use the TAR command in a terminal and ensure you have the permissions copied as well. I'm a newb as I mentioned, but even I was easily able to do this based on a "How to" guide I found in the forum. I did a search for "How to Backup" and found

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)


which explained it very simply. Granted, it won't do a scheduled backup - but it's a backup none-the-less and it's easy.

I wrote the author of the posting and asked him to update it since there was one minor change he should have added, but no response as of yet.

My suggestion to him was to also EXCLUDE the /media folder when entering the back-up command or else you would be backing up all additional drives someone might have connected to their computer. I have a total of three drives and TAR'ing the other two would be ridiculous since they are not Linux.

The command is simple and reads as so:

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

My recommendation was to add: --exclude=/media

Recommend anyone reading this go to the post before executing it 'cause you do have to "sudo" and change the directory you're in. It's all easy though.

I actually did it and a couple minutes later it was done AND maintained my permissions for all the folders as you will read about in the posting.

---

