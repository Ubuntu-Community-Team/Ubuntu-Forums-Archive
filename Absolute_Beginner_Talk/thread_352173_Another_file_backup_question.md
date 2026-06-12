---
title: "Another file backup question"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by Biochem on 2007-02-03
I'm new to the Linux scene and there is only 1 thing holding me from complete migration. I need to backup my important files. This is what I'm looking for in a backup app/script/...

1- File compression (ideally in open format and platform independent)
2- Incremental backup
3- run automatically according to a predefined schedule (I'm that lazy)
4- Split backup file (so that I can burn them)
5- support multiple instances (different daily and weekly backup)
6- support working through Samba (but I think I can workaround this by mounting the destination folder)
7- support files up to 1,5 Gig

Now I did erase file by mistake ](*,) so mirroring is absolutely not an option.

On M$ Win... there is many software that correspond to these criteria but I can't find any that fits with linux. I know I could probably write a script with cron but I don't know how :confused:. 

Does anyone have any suggestion?

Thank you,:grin:

---

### Post by kebes on 2007-02-03
Take a look at this Linux Journal article:
[http://www.linuxjournal.com/article/8931](http://www.linuxjournal.com/article/8931)

It discusses a bunch of different backup programs. I believe many of them will suit your needs. Pick the one that sounds best to you!


Personally I have a script that makes incremental copies to another partition on my hard-drive (and maintains several copies, in case I accidentally delete a file!), and I also use a script (described in [this thread]("http://ubuntuforums.org/showthread.php?t=329918")) to copy files to DVDs on occasion. I prefer un-compressed backups because sometimes archives can fail (rarely, I know... but still).

Using scripts is powerful but you have to have some experience with Linux commands.


The GUI programs mentioned in the Linux Journal article may be perfect for what you want. Good luck!

---

### Post by hodad on 2007-02-07
Help!:confused: 

I simply want to back up my files in a few directories.  There must be a simple way to do this.    I tried "Archive Manager" and laboriously transferred files into it.  Went to save the archive file, and it says something like " cannot create...".   The directories aren't locked, as far as I can tell. I left out all large files (mainly pictures).  Compression would be nice. Do I need to "tarball" the files by directory, then burn them individually onto CDs, or can I download a simple program through Synaptic that will handle simple file backups?

Seems like this should be the most fundamental of operations on a pc, but I have always found backup programs not to work. I'm thinking of buying a second hard drive solely for backups, but I need to do something for the time being.

THanks

---

### Post by kebes on 2007-02-07
Well like I mentiond in my other post, the [Linux Journal]("http://www.linuxjournal.com/article/8931") article mentions a couple of different backup programs that are worth trying, such as Keep, Simple Backup, and KDar.

These can help creating scheduled, compressed backups of files. You can then burn those to CD or DVD. Try installing those and see which one you like.


I personally use a little script, as described in this thread:
[http://www.ubuntuforums.org/showthread.php?t=329918](http://www.ubuntuforums.org/showthread.php?t=329918)
And available online here:
[http://bmgip.gotdns.com/mediabackup/](http://bmgip.gotdns.com/mediabackup/)

This script lets you pick a directory and it will just burn the files directly to CD or DVD. (Note: it's not the most user friendly program just yet... but it does the job!)

---

### Post by hodad on 2007-02-07
Thanks for your response!

I read the article before posting, and already tried "simple backup", but it apparently isn't for simpletons such as myself!

I try to create a new backup, and eliminated all folders except "home".  When I went to perform the backup, I get "A backup run is initiated in the background. The process id is: 14580".  I tried to go to /var/backup to see if anything is there, but it's a root subdir, and I can't get in to see if the backup referred to is there or not  ( I tried getting into the subdir using "sudo cd var", but it wouldn't let me).   Apparently, this is some sort of automatic backup, but it does me no good because I don't even know if it's there. I don't see any way to stop the "default backup" that is aparently running in the background. I did find the  backup time setup, however, and changed it to once every three days, which is nice.

Anyway, if it's even working, the "default" backup is not only saving just the small subset of files I want to save in "home", but the contents of all of the other subdirs as well.  I just want to burn one 640MB CD with the files that are most important to  me.  I imagine that the file (arch/whatever) that Simple Backup is creating is probably much to large to burn onto a single CD.](*,)

---

### Post by hodad on 2007-02-12
Just found a simple backup solution that works well for me. Hopefully it will help other noobs:

I created a backup directory (call it "mybackup" ) under "Home" subdirectory, and copied hundreds of MB of subdirectories and files into it that I wanted backed up.

In the Terminal I went to the Home subdirectory, and did a "ls" to make sure the backup directory was there.  Then  I coded:

tar -czvf   dailybackup.tar.gz  mybackup

This command creates a zipped tarball containing all of the files in /mybackup, and it was very fast and compressed the files automatically.  The resulting file is "dailybackup.tar.gz"  

I then burned this file (in my case, about 598 MB) onto a single CD using Gnome Baker.   The source directories and  files were about 690 MB before compression.
 
If you need more details, go to:

http//:linux.org and go to the beginner lessons.  It should be lesson 15a:backing up your files.

Hope someone else finds this helpful!

---

### Post by mikerduffy on 2007-02-15
> **hodad said:**
> Just found a simple backup solution that works well for me. Hopefully it will help other noobs:

I created a backup directory (call it "mybackup" ) under "Home" subdirectory, and copied hundreds of MB of subdirectories and files into it that I wanted backed up.

In the Terminal I went to the Home subdirectory, and did a "ls" to make sure the backup directory was there.  Then  I coded:

tar -czvf   dailybackup.tar.gz  mybackup

This command creates a zipped tarball containing all of the files in /mybackup, and it was very fast and compressed the files automatically.  The resulting file is "dailybackup.tar.gz"  

I then burned this file (in my case, about 598 MB) onto a single CD using Gnome Baker.   The source directories and  files were about 690 MB before compression.
 
If you need more details, go to:

http//:linux.org and go to the beginner lessons.  It should be lesson 15a:backing up your files.

Hope someone else finds this helpful!

Something to remember: if you're going to backup a directory, and place the backup file within that same directory, use the option --exclude=dailybackup.tar.gz  

This sounds like a stupid thing to mention, but believe me, it comes up. :grin:

---

### Post by Marsolin on 2007-02-15
I like [Keep]("http://linuxappfinder.com/package/keep") and find it simple to use.  My only complaint with it is that it lacks network transparency.  Backing up to my local drive works fine, but I get errors when trying a mounted shared drive or an FTP server.

---

