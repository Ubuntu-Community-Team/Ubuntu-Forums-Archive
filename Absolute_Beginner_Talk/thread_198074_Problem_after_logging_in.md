---
title: "Problem after logging in"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Absurd on 2006-06-16
I have searched for a solution for my problem and I cannot seem to find any questions and/or concerns concerning, so I will post my problem.

First of all, I prefer to install the latest Ubuntu release (6.06 Dapper Drake) onto separate partitions since I have a lot of important windows files. The install and everything goes smoothly without any problems until I am told to log in. I enter my login name and password and a message box comes up saying 

"Your home directory is listed as: "/nonexistent" but it does not appear to exist."

Then it suggests to me that I boot to my home directory (which I, by the way, installed onto a separate partition in my extended partition). I let it do so, then I get another message box that says 

"User's $HOME/.dmrc File is being ignored... ."

:confused: How do I fix this problem?

---

### Post by brentoboy on 2006-06-16
I had this problem because I mounted a partition inside of /home that messed everything up.

if you are going to share a partition between win / lin  then I recommend mounting it somewhere else like /media/win_c 

of course, I only assume you mounted something inside a subfolder of /home because that is what I did.  I made a /home/brent/windows_docs and it really screwed things up.

I could probably be more helpful if you explained what partitions you have, and where you tried to put them all.

---

### Post by steve.horsley on 2006-06-16
Check if your other partition is being mounted, and if so, where. Type the command **mount** to see which partitions are mounted, and where.

Boot into recovery mode, which gives you full root access. 

Check your home directory configuration - use the command:
> cat /etc/passwd
and look for the details after your user name. The normal home directory is /home/username then reboot.

If your home partition isn't mounting right, it may be easiest to create a home directory for yourself on the system partition. At least you can get the graphical environment working while you work on sorting out your partition mounting issues. Use these commands in recovery mode:
[B]mkdir /home/yourname
chown yourname:yourname /home/yourname
nano /etc/passwd
[/B] then edit your username line and change the last field (after the last ':') to /home/yourname

---

### Post by Absurd on 2006-06-17
[QUOTE=brentoboy]I could probably be more helpful if you explained what partitions you have, and where you tried to put them all.[/QUOTE]This is how/where I'm trying to keep things

windows in dev/sda2 (NTFS since I have XP), linux in dev/sda3(EXT3), and the swap in dev/sda4

Because I bought this computer from Dell, the first partition is FAT and I don't believe it can deleted. 

[QUOTE=steve.horsley]If your home partition isn't mounting right, it may be easiest to create a home directory for yourself on the system partition.[/quote]I don't think it mounted correctly. I just browsed through the directory using PartitionMagic and there doesn't seem to be a subfolder in there (it's completely empty).

Should I instead make an extended partition that consists of swap, root, and usr in /dev/sda3/home?

---

### Post by Absurd on 2006-06-19
follow up

I tried steve.horsley's suggestion of booting into recovery mode and creating the /username directory in home. The problem is that when I do
> chown username:username /home/username I get the message that the group is invalid.

> nano etc/<password> doesn't do anything either

I checked my install disk for defects and it didn't find any by the way.

[edit]Nm, I fixed it with the deluser username adduser username commands

---

