---
title: "[SOLVED] GUI data backup for dummies?"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2007-10-21
Hi community!

I would like to find a nice simple GUI utility for backing up my data in Ubuntu 7.04

In Windows XP I found & like SyncBack which is very simple & makes incremental backups, so is quick after the first time.

For Ubuntu, it looks like "sbackup" (or is it "Simple Backup" ?) would be about the same, but I read that it may not work with 7.04

Can anybody confirm that one way or the other?

Is there anything else I should look at?

Thanks!

---

### Post by kast on 2007-10-21
I believe this does work for 7.04, I had tried it once, but it turned out that it had more options then I really needed, funny when you consider it's a simple backup :) 

  I just wrote a small script to tar  the directories I needed backed up, and then move the file to my snap server, I'm in no need of incremental just full backups.

I say just install it and mess with it!  See if you like it, it was a nice little program.

---

### Post by 2CV67 on 2007-10-22
I installed sbackup via synapt & tried to run a backup with the default settings (manual) as I found it.

As far as I can see (there is no progress monitor) it churned away for about 20 minutes (which was surprising as my Ubuntu files are pretty small so far - I am still mainly using XP) but only succeeded in creating an empty folder called "backup"...

I tried again & there was much less activity, but still only the empty folder.

Any ideas please?

Is anybody sure sbackup works OK with 7.04?

Thanks!

---

### Post by kast on 2007-10-22
I will install it again and give it a whirl.

---

### Post by 2CV67 on 2007-11-02
No news on sbackup?
I have given up on it.

In the meantime, I installed unison & unison-gtk, thinking this might be the answer, but I am stuck already.

I tried to backup my home directory to my external hard drive (FAT32...) but ended up with a whole list of files saying "Failed to set permissions of file /...."

I could not find anything understandable about that, even on Google.

Is this a detail or a fundamental problem?

Help please?

---

### Post by isparkes on 2007-11-02
I do understand that this is not at all what you are asking for, but I'd recommend you to have a look at creating a TAR file with an associated include file. I started where you have started, looking for a GUI, but to be honest with you I've ended up just using a really simple script to do the whole of the backup process with one command.

If you want, I'll happily post a sample script, but I don't want to feel that I am forcing you into anything. The idea is this:

You create an include file that contains the paths to all of the files or directories that you want to backup on a regular basis. You then execute "tar" to create a compressed backup file of all of the files in the include file.

---

### Post by DaveRM on 2007-11-02
I have been using sbackup for awhile now.
It's easy and it works for me.
Here is a good How To.

[http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html]("http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html")

DaveRM

---

### Post by 2CV67 on 2007-11-03
Thanks DaveRM for that encouragement on sbackup!

After reading the How-To I tried again & have made some progress, but I have to agree with some of the correspondents below the How-To who raise good questions, like progress indicator, root, confusion etc!

Firstly, I have found that I _can_ make backups in Manual mode.
But I can only see them if I switch to Root first...

Secondly, I am still unable to set automatic backups (this is not a big problem - just an irritation).
When I try to set "Use recommended..." instead of "Manual" & set a daily time a few minutes forward - nothing happens at that time.
When I re-open Simple Backup config again, it has reverted to "Manual" even though I try to "Save" the modifications.

Thirdly, I am unable to backup to my external hard drive, which is really the whole point.
This drive is configured (wrong word?) as FAT32, if that may explain something.

Fourthly, the backups appear to be incremental (good) but kept separate, so I wonder how I would manage to re-assemble everything I needed to restore after a disaster?

It really looks as though Syncback under XP is light-years ahead of Ubuntu here (GUI data backup for dummies) or maybe I just have a lot of painful learning to go through still!

Thanks for the help though :)

---

### Post by 2CV67 on 2007-11-03
More progress with sbackup...

The "Custom backup" setting _does_ work & is saved & does generate an automatic backup at the pre-set time, so I suppose I don't need the "Recommended" setting at all.

To be continued...

---

### Post by 2CV67 on 2007-11-03
Ah - that seems to be OK now!

Remaining problem was that I couldn't set the destination for my backups to be the external hard drive.
For the sake of any other dumb newbies, I finally found it was under 
/media/LACIE...

So, to resume GUI data backup to External Hard Drive for dummies:
[LIST]Install sbackup via Synaptic Package Manager
[*]Open Simple Backup Config in System - Administration
[*]Select "Use custom backup settings"
[*]Destination - select "Use custom..." then "other" then navigate to /media/YourExtHD/new folder
[*]Time - set "daily" & a time
[*]Save
[*]Backup Now! to check.
[/LIST]

I still have some doubts about pulling things together if I need to recover, but that can wait...

---

### Post by 2CV67 on 2007-11-06
Ubuntu is not always open at the time I have set for my automatic daily backups with sbackup.

I had imagined that sbackup would automatically run at the next possible opportunity after a missed backup, but it does not seem to do so.

Should it?

Can I set it?

---

### Post by CatKiller on 2007-11-06
> **2CV67 said:**
> I tried to backup my home directory to my external hard drive (FAT32...) but ended up with a whole list of files saying "Failed to set permissions of file /...."

I haven't used any backup software, but this is because FAT doesn't understand permissions. At all. If you're just copying generic data that you want to be accessible to everyone (pictures, music, that sort of thing) then FAT is fine. For a backup of files with existing user permissions you'll need to use a more robust filesystem like ext3 or ReiserFS.

---

### Post by Cariboo1938 on 2007-12-01
Hello all,
I used Sbackup and the backup part works but I cant restore.....
When follow the instructions [HERE]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite#head-0dd75c32a2c2946a5f62afec2b4f2ea456a420ba") the backup file does not show up!
Has anyone had this problem yet?
What can I do?:confused:

EDIT: added Screenshots

---

### Post by Cariboo1938 on 2007-12-01
I still need help with the SBackup issue!
I can backup...but I can't restore because the restore part of the program does not recognize the default location of the backup file which is /var/backup.
What can I do?:confused:

---

### Post by zmike1 on 2007-12-01
Cariboo, 
I'm sorry I can't help you with the backup question... I'm looking for answers myself.  However, I might suggest you start a new thread or something since this one is labeled "solved" and may not get much attention.
Good Luck.    -zmike

---

### Post by Niniel on 2007-12-01
Somebody recommended grsync to me, and since I was also too stupid to get SB to do my bidding, I used that. Worked very well for me - backed up to an external NTFS-formatted HD via USB without any problems. Even has a progress bar! :)

The only weird thing about that program is that it's installed to the Internet set of applications.

---

### Post by Cariboo1938 on 2007-12-01
> **2CV67 said:**
> I installed sbackup via synapt & tried to run a backup with the default settings (manual) as I found it.

As far as I can see (there is no progress monitor) it churned away for about 20 minutes (which was surprising as my Ubuntu files are pretty small so far - I am still mainly using XP) but only succeeded in creating an empty folder called "backup"...

I tried again & there was much less activity, but still only the empty folder.

Any ideas please?

Is anybody sure sbackup works OK with 7.04?

Thanks!
Maybe I'm a bit late with my reply ...
Anyhow, try check on running process by running the command line in a terminal: ```
ps aux | grep -v grep | grep <Backup process ID>
```
You get either a response like > USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root     10764    0.0        0.0          0          0       ?        ZN    13:11      0:00     [sbackupd] <defunct> or no output at all if the process is not running. (In my case the backup process ID was 10764).
To see all running processes you can use > ps auxonly.
BTW could you get Sbackup to restore your backup file? I can't!

---

### Post by erm27 on 2007-12-01
Just for my edification, I ran sbackup today for a 7.10 install. Can someone give me a rough size estimate of your successful backup file. Mine is about 180 mg and I tried to back up from root without directories like /tmp and the rest that aren't recommended.

---

### Post by Cariboo1938 on 2007-12-01
> **erm27 said:**
> Just for my edification, I ran sbackup today for a 7.10 install. Can someone give me a rough size estimate of your successful backup file. Mine is about 180 mg and I tried to back up from root without directories like /tmp and the rest that aren't recommended.
My backup file from SBackup contais 6 items, totalling 1.4 GB
including /boot,  /etc,  /home,  /usr/local,  /var

Have you tried the backup restore?

---

### Post by erm27 on 2007-12-02
I'm thinking that I need to run as root. Any suggestions on how I can get it going as root? gksu? what is the terminal command for simple backup?

---

### Post by Cariboo1938 on 2007-12-02
> **erm27 said:**
> I'm thinking that I need to run as root. Any suggestions on how I can get it going as root? gksu? I think you do not have to be root if you use that way:
Once you completed the installation you can access sbackup using System--->Administration--->Simple Backup Config (screenshot)
> **erm27 said:**
> what is the terminal command for simple backup? I never tried Sbackup Configuration from command line but if you want to configure sbackup you need to:

---edit /etc/sbackup.conf file.

I never tried Restore Backup from command line either:
 
Run "sudo srestore.py /var/backup/2006-11-18_03 /home/myuser /home/myuser/old". 
You can omit the last parameter to restore to the same directory.

See also [HERE]("http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html")

---

