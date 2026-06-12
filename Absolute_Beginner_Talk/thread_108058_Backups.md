---
title: "Backups"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by cjm5229 on 2005-12-24
Hi, 
Having trouble getting a backup program that works. I installed BackupPC, but can't seem to get it to run. I tried logging into the website, without luck. It said server unavailable. I also tried backup2L, can't seem to get it to run either. Most problems I've had so far I can find the answers to in the forums or the guides, this one though I haven't been able to find anything about. I would like to be able to backup my entire Ubuntu OS to a fat 32 partition on my HDD so I can enlarge my Ubuntu Partition. Making WinXP smaller. Still not able to eliminate it yet. Can't seem to find a reason to pay for win4lin or Cedaga when I own a valid copy of WinXP and can dual boot. Any suggestions on how to do a complete backup?
 Thank you, Carl

---

### Post by Herman on 2005-12-25
Personally, I prefer simplicity, and just make simple back-ups without any file compression. See this link: [http://www.users.bigpond.net.au/hermanzone/p13.htm]("http://www.users.bigpond.net.au/hermanzone/p13.htm")

If you have a Ubuntu 'Live' CD, I recommend Gparted for shrinking Windows. Also good is QTParted on a Knoppix CD, or System Rescue CD.

All other methods are a little bit tricky for absolute beginners, this is called the absolute beginner's section, I'm not intending any disrespect.

Another way to acomplish what you are wanting to do is this: [http://www.ubuntuforums.org/showthread.php?t=105255]("http://www.ubuntuforums.org/showthread.php?t=105255")

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")
  The above link contians the most popular answer to your question, but I haven' t tried it yet myself, others seem to like it. [COLOR=Red]EDITED 28/01/05 : Use the link given by mustard, two posts down, this one is out of date, sorry cjm5229, sorry everyone, I didn't realise, thanks for correcting me, Mustard.
[/COLOR] 
There's a better way, but it might be a bit advanced:
[http://www.ubuntuforums.org/showthread.php?t=96694]("http://www.ubuntuforums.org/showthread.php?t=96694")

Choose a method suitable for your skill level and be very, very careful!
Good luck, (Herman).

---

### Post by cjm5229 on 2005-12-25
Thanks, Herman
 I think the second option is what I was looking for. First step to messing things up is a backup, right? I have a 10 Gb Fat32 Partition I can put my backup on. I shrunk windows with OTparted. I have that on a Mepis disk, Runs in live and when you click install you can run QTparted quite easily. I ran the script in the link you gave, and I now have a backup file in my home folder. The problem is now I can't move the file. Everything I try I get the message I "don't have permission to move file" Once I get that moved I will be able to delete the partition I have Ubuntu on, add the rest of the free space I created when I shrunk windows,  Reinstall Ubuntu, restore backup, and If I didn't screw up to badly, it should work? So now all I have to do is figure out how to move the backup file. 
Thanks, Carl

---

### Post by Mustard on 2005-12-25
Could you do this command below and paste the output in this thread?

```
ls -l yourbackupfilename 
#subsitute the filename you're  trying to move for 'yourbackupfilename'
```

Could you tell me whether you are on Breezy Badger or Hoary Hedgehog too please, as one of the links above that Herman has shown you is for Hoary Hedgehog not Breezy Badger.  Its the thread entitled, "How to Backup and Restore".  The Breezy Badger thread for that option, if you used it, is below.

[http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

---

### Post by Herman on 2005-12-25
Carl, it sounds like you are doing fine and are on the right track. 
I think I should mention for the sake of others viewing that I'd recommend using more than one kind of backup, for example, just to be sure, I'd do the simple back-up first, just for regular files, e-mails and bookmarks and that kind of thing. That way if something does go wrong with the more complete, but more complicated back-up technique you decide to employ, then at least you can still get back some of your main stuff from the simple back-up.
As for moving your backup file, it sounds like you'll need to use your terminal and use a sudo command to (tell it who's boss), and move your file directly using a command you can make up for that.
Another way might be to 'chown' the file, so you can move it around and do as you like with it, but I'm not sure if it has to be 'root' again when you restore -likely it would I imagine. You might be able to 'chown' it back to 'root' ownership again later. 
I can't remember now if I tried that method out or not, but maybe I'll give it a run sometime to find out what happens for myself and see what other commands might be needed. :D (Herman)
Oh, it looks like mustard is going to sort it out, Ill let you go. Good stuff!

---

### Post by cjm5229 on 2005-12-26
Ok, here's where I have gotten to. I did backup with the one for Hoary, I figured out how to start Nautilus in root and that took care of moving the file, actually it copied it. When I tried to delete it, It moved to trash. Then I read the post on  using the backup script for Breezy instead so I tried to do that and it is backing up the first backup from the trash, Now I can't find a way to empty the trash can that it is in, and I have two backups to get rid of now. :) At least I'm having fun, and learning a few things in the process. I think I will try the first method from Herman and see if I can just do a simple backup of necessary files. If that doesn't work I will just co a clean reinstall and start over. Since I am on a learning expedition here, I really don't have anything important in my files anyway. Thanks guys and I will be back when I figure out whether it works for me. I may screw this up a few times but eventually I'll learn enough to be able to help others as you have helped me. Carl

---

### Post by infoseeker on 2005-12-26
While we are on this topic, what is the best way to backup bookmarks?  I usually export the bookmarks to an html file, and backup that, but this can't be the right way, surely !

Any suggestions/tips ?

P.S. I don't use a backup program, only K3B.

---

### Post by bscbrit on 2005-12-26
infoseeker,  What is wrong with that way of backing up your bookmarks? You could, however, always backup the location in which the bookmarks are usually stored (e.g. for firefox I would backup ~/.mozilla/firefox).

---

### Post by cjm5229 on 2005-12-27
Well, I got My issues taken care of. Messed up a few things but mostly just copied files to my F drive. Took out my extra partitions with  Ubuntu partitioner. did a clean ubuntu install. Returned the backed up files. reinstalled what I missed. Resized my F Drive with QTparted. Now I have 40GBs for Ubuntu, 35 GBs for XP and 5GBs for F Drive(fat32) to swap files from XP to Ubuntu. Everything is working great. Thanks for the help. I basicly backup my Bookmarks the same way except I put them on my Pen Drive. I also found a thread by Kyral "Terminal for Beginners" [http://www.ubuntuforums.org/showthread.php?t=73885]("http://www.ubuntuforums.org/showthread.php?t=73885")   that helped me with a lot of the issues I had doing things with Terminal, Good read. Learning Ubuntu is more fun than playing games. I might not always do things the right way but it is sure a lot easier to fix it than it is in Windows. My youngest son (10) Has screwed up his computer so many times I'm on a first name basis with the people at windows activation department because he has reinsalled it so many times. I'll get them all switched over to Ubuntu yet. ;) Thanks again, everyone, for all the help. Ubuntuforums Rocks! Carl
PS. Herman, I Bookmarked Hermanzone, It really is a great resource. It's really wonderfull how so many people contribute so much to the knowledge banks for Noobies to learn from. Thanks

---

### Post by ardchoille on 2005-12-27
I use tar for backups. Here are some steps to perform:

1) Create a directory to store the backups. Replace the "<user>" below with your username:
```

sudo mkdir /home/backups
sudo chown <user>:<user> /home/backups

```

2) Create the backup, move it to the storage directory and put the date in the backup filename. Replace the "<user>" below with your username:
```

cd /home
tar -cjf /home/backups/`date +%Y%m%d`.<user>_home.tar.bz2 <user>

```

Read man tar for more information about the tar command. The command line is fast and powerful. There is no need for a gui app for backups.

---

### Post by bscbrit on 2005-12-27
I wouldn't personally store my backup of my home directory in subdirectory of home.  If I lost my home directory there would be a good chance that I would have lost my backup also!
Better in a different directory, better still on a different drive, yet better still on another computer, and best of all on some media stored at another location.  If both locations burn down simultaneously - you will probably not be too concerned about your computer data!

---

### Post by ardchoille on 2005-12-28
[QUOTE=bscbrit]I wouldn't personally store my backup of my home directory in subdirectory of home.  If I lost my home directory there would be a good chance that I would have lost my backup also!
Better in a different directory, better still on a different drive, yet better still on another computer, and best of all on some media stored at another location.  If both locations burn down simultaneously - you will probably not be too concerned about your computer data![/QUOTE]
You have a good point there.

---

