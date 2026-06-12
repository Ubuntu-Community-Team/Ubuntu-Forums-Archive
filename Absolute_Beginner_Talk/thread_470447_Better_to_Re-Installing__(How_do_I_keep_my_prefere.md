---
title: "Better to Re-Installing?  (How do I keep my preferences/settings?)"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Cullen on 2007-06-11
I was digging around the garage the other day and I discovered a 40 GB hard drive.  I want to more or less turn this hard drive into my operating system drive.  My question is this, Is it better to reinstall my entire setup on the new drive, or can I just copy my linux partition to a partition on that drive?  

_**If I have to reinstall:**_
[LIST]
[*]How do I retain account settings for Thunderbird?
[/LIST][LIST]
[*]How do I save my bookmarks from firefox?
[/LIST]
[LIST]
[*]Is there a way to retrieve my installed package list, so I can easily punch it in to the terminal when I get things back up and running?
[/LIST]

_**If copying my stuff is the better way to go?**_
[LIST]
[*]I'm not experienced with grub, how do I re-configure it to find the installations on the new drives? (I dual boot win xp, that partition would also be moved to the new drive.)
[/LIST]

---

### Post by avik on 2007-06-11
Have a look at this: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

Basically, if you can somehow get *only* the home directory onto its own hard drive then, you can have your data on a separate hard drive without ever having to worry about losing your settings, bookmarks, etc.

So what I would do is go ahead and reinstall Ubuntu onto the 40GB hard drive, then mount the other hard drive and delete everything but the home directory on that hard drive.  Finally, I would mount that hard drive as /home as per the directions in that link.  However, I'm not responsible if any data gets inadvertently erased.

Also, I believe the following will list all packages:
```
dpkg -l
```

I'm not sure of the exact output format for that command, but this link talks about it: [http://ubuntuforums.org/showthread.php?t=355243]("http://ubuntuforums.org/showthread.php?t=355243")

Hope that helps.

---

### Post by Tux Aubrey on 2007-06-11
> I was digging around the garage the other day and I discovered a 40 GB hard drive.

Wow! Can I come over to your place?  All I have found in my garage is some half full paint tins.

You strategy will depend on how much you want to save from the existing drive.  Thunderbird and firefox settings can be copied and you can get a fair idea of what you have installed by opening your file manager and viewing hidden files - almost everything you have installed will have a hidden folder named for the app.

It might be worth doing a backup of your thunderbird directories and your bookmarks and doing a clean install.  That will give you the opportunity to set up your partitions as you want them (eg. a separate /home) and do some spring cleaning.

Good luck

---

