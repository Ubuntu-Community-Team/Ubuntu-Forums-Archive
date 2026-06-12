---
title: "Home user back up"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by RogerD on 2006-10-17
Hi

Has anyone tried hubackup - it looks just the thing for a low-tech route to backing up home folders.

I've installed the application, but it's not clear how you specifiy the 'Save Backup To' destination. I've got an external hard disk called My Book. Efforts to type in 'My Book' haven't met  with any success.

Any ideas, anybody?

Regards

Roger D

---

### Post by aysiu on 2006-10-17
If no one gets back to you...

I haven't used *hubackup* (never even heard of it), but you can create a separate home partition:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Or you can also use *rsync* to back up: ```
rsync -av /home /destination
```

---

### Post by giftnudel on 2006-11-22
Hi RogerD,

hubackup is currently not really meant to be used, it is more a development version and unless it supports restore (which it doesn't atm, but will hopefully in the next weeks) it is not really useful. As for your problem with your external harddrive: You need to mount it and then point hubackup to the directory where you mounted it. 

I will think about how we can implement this in a different way where we will show the additional (external) drives, this is really a nice idea.

Thanks for sharing your experience,
giftnudel

---

### Post by Cariboo1938 on 2007-01-08
> **aysiu said:**
> If no one gets back to you...
I haven't used *hubackup* (never even heard of it), but you can create a separate home partition: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Or you can also use *rsync* to back up: ```
rsync -av /home /destination
```
Hi aysiu, 
what is the proper way, i.e. what program/procedure would you recommend to back up a system? I have a separate /home partition, so I wonder if it would be enough to back up only this partition?

:-\" UPDATE:
Hi, 
I was asking the above questions because I couldn't get working "Simple Backup" at this time.
Now I figured out why it didn't work. 
Simple Backup [COLOR="Red"]DOES NOT create the destination directory[/COLOR] which you can define under the Simple Backup Config "Destination Tab". 
[COLOR="Red"]*_One has to create it (as root) before one starts Simple Backup._*[/COLOR] It has already to exist before one selects it. 
I didn't have /backup under /var therefore no backup files were created. I had to do 
```
cd /var
sudo mkdir -p backup
```first.
To run BACKUP I started -->System -->Administration -->Simple Backup Config. 
Here I was asked for my  password. After that, I just followed the instructions.
For people who are interested, I attached some ScreenShots of the whole procedure.

---

