---
title: "how to best back up music files"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2006-03-05
Hi:

I run one Linux computer that functions as a file server - running SlimServer to manage my music collection and make it accessible from any computer.
I have 35GB or so of music and, although I have all the original music, it's getting to the point - heck, it's way past the point - where a crash and subsequent loss of music files would take me days to restore - probably weeks.

So, I want to back up the music files on the SlimServer box, which runs Fedora FC4, to my Ubuntu computer. Both have Samba, SSH and rsync installed.

I am thinking that, since the total volume taken up by the music files isn't that big, I should just do a simple back up (i.e. copy) to a hard drive on the Ubuntu computer that is set aside specifically for this purpose.

Am I missing something important or is going the simple and direct route a good idea?

I have read about setting up an automatic daily backup using rsync with SSH encryption but my comps are in my house on a closed network so security is not really important.

I have been reading/using this article as a guide:

[http://www.linuxjournal.com/article/8590](http://www.linuxjournal.com/article/8590)

but the rsync instructions are a little over my head - partly because the author is using encryption but also because I have never used rsync before.

I have backed up my Ubuntu system but had to split the subsequent file into several 2GB files as I understand 2GB is the max that should be used with Ubuntu/Linux. This is another reason I'd like to do a backup/copy of the music files as otherwise I will end up with something like 18 2GB files. Which wouldn't be terrible but if I just basically copy the music hard disk, if the one fails I can swap it with the other - and I don't want to use RAID because I don't want both drives on the same computer.

Sorry for the length of the post. Any ideas are really welcome.

---

### Post by aysiu on 2006-03-06
I just copy my files every week. It's too much trouble for me to figure out how to do an auto-backup, especially since I back up on an external hard drive that isn't on all the time.

---

### Post by GMachine_24 on 2006-03-06
Hi:

Thanks for your reply. I just want to make sure I understand:

You copy all your files every week or do you do a basic backup and then incremental or differential back ups?

Thanks.

---

### Post by shof2k on 2006-03-06
You can also use DAR to do an initial backup then incrementals on top of that.

---

### Post by mlind on 2006-03-06
Setting up environment which would automatically do backups (full and incremental)
from my "sensitive" stuff is on my TODO list too.

I suggest you check out BackupPC which does this task quite nicely. It has actually
saved my day couple of times. Dunno how complicated it is to setup or if is it bit
over the top for single workstation.

---

### Post by GMachine_24 on 2006-03-08
Thanks to everyone for the helpful suggestions. I will try them and see what works best and what is easiest for me - as I am still a relative newcomer to Linux.

Will post results here - hope others do the same if they read this and try some of the suggestions.

Ciao.

---

### Post by aysiu on 2006-03-08
[QUOTE=GMachine_24]You copy all your files every week or do you do a basic backup and then incremental or differential back ups?[/QUOTE] I copy *all* my files every week. I bought a 160 GB external hard drive expressly for backup purposes.

---

### Post by deBaas on 2006-03-08
[QUOTE=GMachine_24]Hi:
... SSH and rsync installed...[/QUOTE]
Those are quite an overkill for the purpose. Just make a back-up reguarly (samba, ftp or something) or write a simple script to automate.

---

### Post by GMachine_24 on 2006-03-12
Again, thanks to everyone for their replies.

As far as writing a script, I am perhaps even more of a beginner than an 'absolute beginner' as I have never written script before. If there is an easy beginner's guide - or even a not-so-easy guide - I'm interested.

I do not see this project as all that difficult - I am mostly waiting now because I need to build another system for the backups from various computers.

Thanks again.

---

### Post by GMachine_24 on 2007-03-28
My apologies for not following up with the answer I came up with it. I have been using the solution (below) for a year or more without incident. It is easy and elegant and soooo simple.

Happy computing.

Hi:

I thought I should post how I ended up copying the hard drive as perhaps it will be useful information for others.

First, I ended up doing it on an FC4 system. Which shouldn't really matter but in the interest of full disclosure.

I used the "rsync" utility to copy drive 1 to drive 2 on the same computer. It was simple and efficient; in future updates rsync will only copy what has changed - i.e. an incremental backup.

The code is simple:

rsync -avz /music1 ---force ---ignore-errors /musicbackup

/music1 is the directory/mount point for the original music drive; /musicbackup is the directory/mount point for the backup drive.

[although you probably cannot tell from the command above, there are two hyphens before "force" and "ignore-errors". so - - force  - - ignore-errors]

when you're ready to do your second back up of the same hard drive, you use the same code, rsync figures which files are new/changed and copies only those.

rsync is useful for lots of other reasons - if you want to copy over a network you can easily encrypt using ssh and there are many other features of rsync.

this site has a lot of helpful information [http://everythinglinux.org/rsync/](http://everythinglinux.org/rsync/)

This article (again) [http://www.linuxjournal.com/article/8590](http://www.linuxjournal.com/article/8590) has basic information for building a terrabyte backup system - the author uses FC4 but the same thing can be done easily with Ubuntu.

Happy back ups.

---

