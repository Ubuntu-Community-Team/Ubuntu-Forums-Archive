---
title: "Backup Utilities"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by eeboy on 2008-04-17
Is there a backup utility that would synchronize the folders/files on my laptop with my FTP site?

---

### Post by herbster on 2008-04-17
Yes, rsync.

This may help: [http://www.brunolinux.com/10-General_Info/Rsync.html](http://www.brunolinux.com/10-General_Info/Rsync.html)

---

### Post by alpdo on 2008-04-18
this works with my pc... try this one....


Take a look at QuickStart: Back-up, Restore, & Set-up Ubuntu Quickly and Easily if you are scared of command lines.

---

### Post by alpdo on 2008-04-18
QuickStart: Back-up, Restore, & Set-up Ubuntu Quickly and Easily

---

### Post by alpdo on 2008-04-18
[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

---

### Post by eeboy on 2008-04-26
I've looked at rsync. From what I have read it looks like it requires something installed at both ends. Unfortunately I don't have control of the FTP end. It's simply the space I have allocated with my hosting (100GB at godaddy).

Do I have a fundemental misunderstanding?

I also ran across a promising application called sbackup. Unfortunately it crashes when I attempt to perform a backup.

Suggestions?

---

### Post by tamoneya on 2008-04-26
I use sbackup and that is really not its purpose.  Sbackup is for making backups of your data and then saving them somewhere.  Not synchronizing files.  What I have found useful is tools like SVN, Git and Mercurial.  They are meant for the version control of source code but I find that they are nice when I attempt to keep my laptop and desktop synchronized. This also will require something server side though so it probably isnt the best option.

Also try not to have consecutive posts.  Just edit your previous post if you have forgotten something.  I believe quickstart has been ended unfortunately.

---

### Post by eeboy on 2008-04-26
I would take a working sbackup. A synchronization tool would be best but it's not entirely necessary. From what I can tell sbackup has no development activity. I suppose at the very least I can try sbackup to a local drive and then do the FTP manually. However, I believe a backup should be automatic. I know myself... I'll forget or just put it off.

---

### Post by tamoneya on 2008-04-26
I personally use the ssh backup option on sbackup.  It will automatically transfer files to another server via ssh which is probably already installed on your ftp server.  See if you can get access via ssh.  That would be the ideal option.

As for getting sbackup working.  Try running it through command line.  Then you can post whatever errors are thrown by sbackup and we can figure out what is causing the failure.

---

### Post by eeboy on 2008-04-26
Unfortunately it appears as if SSH is only allowed on the dedicated hosting servers...

[http://help.godaddy.com/topic/310/article/833](http://help.godaddy.com/topic/310/article/833)

I'll give the command line a try.

---

