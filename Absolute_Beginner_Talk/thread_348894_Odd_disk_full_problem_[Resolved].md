---
title: "Odd disk full problem [Resolved]"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by freebeer on 2007-01-29
Hi guys!

I've encountered a rather odd problem with my 6.06 machine.  The / partition is full, which, of course, prevents me from logging in normally.  It appears that I can log in in safe mode, however.  (The machine is at home, and I'm at the office right now so I can't check anything until I get home.)

I first noticed the impending error when I was reading the ubuntu forums in firefox.  I got a little warning message informing me that my / partition was 95%.  (Nice warning to have!)  About a minute later I got another warning that it was 96% full.  I looked down at my box, and sure enough, the drive light was buzzing away.  97%... 98%... 99%... full at the rate of 1% per minute or less (I didn't time it).  Interesting, sez I.  (It's a 20 GB partition, FWIW.)

I suspect that some process was writing to the disk.  What that process might have been, I don't know.  What file(s) that might have been written to, I don't know.  That's where I turn to you guys.  :)

I'm **guessing** that it's just a log file, which I can delete easily enough.  The challenge for me is trying to find it.  How does one go about finding recently written files and/or very large files that might be anywhere on the / partition?  Given that the partition became full, would that file even properly show as a file, since it probably would have run out of space before the file index could have been updated.  (My ignorance of the mechanics of the ext3 file system is showing, here.)  :D

FWIW, I'm not doing anything disk intensive with this machine - nothing that I can think of that might cause this.  I'm not compiling anything, or running funky scripts that aren't standard with 6.06.  I am running an Apache2 server, but it's pretty basic with just a single test page and no PHP, or blogging software, etc.

So, any ideas what may have caused this?  Any suggestions on how to hunt this down to prevent it from happening again would be appreciated.  That and any help in finding the rogue file(s) and deleting them so I can get my / partition back would be most appreciated.

---

### Post by taurus on 2007-01-29
Boot into recovery mode from GRUB menu and do a little house cleaning.

```
aptitude clean
rm ~/.Trash/*
rm /home/**username**/.Trash/*
(replace the actual name of your log in for **username**)
```
Then, look in /var/log and remove all the backup copy of your log files.  Most of them will either end up with a number at the end or .gz.

---

### Post by freebeer on 2007-01-29
Thanks for the tip!  The commands managed to clean up some stuff - enough to at least let me log in normally in Gnome.  I now have ~36 megs free.  

Having looked at the contents of /var/logs it would appear that whatever was filling the disk, it didn't reside here... there wasn't anything there that stuck out as large enough to be the culprit.

Is there a command that I can use that will list files and their sizes if size is greater than, say, 2 megs?

I realize that I can do something like:

```

ls -aRtl > file.txt

```

to recursively list all files (including hidden) with date and time, redirected to a text file.  This would work, I think, for my purposes of hunting down the culprit.  However if I could also limit that hunt to the larger files, that'd be great (and I'd learn something or 3 in the process).  :D 

Thanks!

---

### Post by freebeer on 2007-01-29
That was fun.  I got the problem resolved.  (Is it possible for a thread starter to mark it as resolved, or can only mods do it?  If I can, how is it accomplished?)

The last step was to clean out the .Trash, so to speak.  :D  The command listed above, for some reason, didn't appear to work in recovery mode.  I got no error message at any rate when I tried it.

Once I was able to login as a regular user, I could delete the contents of .Trash in nautilus (after issuing the "sudo nautilus" command).  The Trash icon on my desktop was empty.  Different .Trash directories?

At any rate, I was able to build a terminal command that helped me track down the big files combining "ls" and a few of its friendly parameters, filtered through "grep" looking for only instances of [0-9]G, redirected to a file for easier browsing.  Why are newbies (and I consider myself to be a newbie) so afraid of the command line?  It's so powerful! 

Anyways, it was a wonderful exercise in learning how to use this OS.  (Try *that* one, Windows!)  :D

---

### Post by irish_flu on 2007-01-29
> **freebeer said:**
> That was fun.  I got the problem resolved.  (Is it possible for a thread starter to mark it as resolved, or can only mods do it?  If I can, how is it accomplished?)


first, "edit" your first post in this thread.  Then at the bottom of the editing windows click "go advanced".  It will load the full editor, and you'll see check boxes above the editing pane for marking something resolved or not resolved.

---

### Post by Buck2348 on 2007-01-29
I'm curious to know what kind of files were the culprits and how much space you recovered.

Thanks,
Buck

---

### Post by freebeer on 2007-01-30
@irish_flu:  Thanks for the tip!

As for which files: there were several that I deleted, actually.  The culprit that forced to full partition was a backup file.  I have a small script that does an incremental backup every night, and a full backup every week.  Unfortunately, I didn't realize that the script wasn't deleting the old backup files.  ](*,) 

The biggest gain was from deleting the vmware installation and support files.  I never did get vmware to work (my fault, not its).  There were 4 Windows 2000 files taking up 2 gigs each.  I ended up cleaning off 15 gigs in total.  :D

I would never have guessed on my installation of vmware taking up that much space if it wasn't for that terminal command that I hacked together.  :wink:

---

