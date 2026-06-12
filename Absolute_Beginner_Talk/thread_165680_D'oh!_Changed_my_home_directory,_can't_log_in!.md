---
title: "D'oh! Changed my home directory, can't log in!"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by e lo on 2006-04-25
I changed my home directory using System --> Users and Groups --> Properties. I made a directory on my FAT32 partition (I have one large SATA HDD with 3 partitions: NTFS with Win XP installed, one for Ubuntu (Breezy 5.10), and one FAT32).

I tried to log out and log back in to Ubuntu, and I get an error message that goes something like:  "home/.$???? file cannot be found. " I am also informed that I need to have 644 permission set on this file. I apologize for the sketch info -- I don't remember the error message verbatim, nor the hame of the file. 

The only way I can log in to my installed Ubuntu is via the failsafe terminal. I only have one user set up, so I can't log in as another user and fix my mistake. Unfortunately, I'm still a Linux dummy. Any advice on how I'd go about switching my home directory back to what it was originally from a terminal window?

---

### Post by nalmeth on 2006-04-25
hmm, did you actually move your /home?
When you're in the failsafe terminal, type 
cd /home
ls
is everything in there as it should be?
I believe the command to regain ownership of a folder is:
sudo chown username /home/username
with your username of course..

---

### Post by Nano Geek on 2006-04-25
I'm not positive about this, but I think you should:
[LIST=1]
[*]Download and burn a live cd
[*]Boot using it and delete the home partition
[*]Back in your installed Ubuntu make a new home partition and before you log out copy your home folder contents to your new partition as Super User
[/LIST]
Tell me if this works or not.

---

### Post by nosmada on 2006-04-26
Here is what you do, you start up in "recovery mode" when it stops loading and says "login:" type in "startx" and press enter(return) this will log you in as root and you can go through the same process you did before and change the home folder back to /home/"your username" without the quotes of course.

I just did this same thing about an hour ago.

Now for making your fat32 partition accessible through the home folder, I don't remember where but someone talked about mounting your partition to the /home directory, but that it could cause problems when using multiple users.

I am not totally sure about this so I have just mounted to /media/documents which I just use that folder instead of my /home folder.

A little long but I hope that all helps and makes sense.

---

### Post by e lo on 2006-04-26
Thanks for the suggestions, all. I actually wound up reinstalling from scratch -- a good excercise, anyway. I'm not sure what my final HDD configuration will look like, so I don't actually have a fat32 partition anymore, so that problem isn't an issue for me at the moment. :)

---

