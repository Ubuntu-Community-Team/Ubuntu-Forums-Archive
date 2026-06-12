---
title: "rsync to a remote server"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-10-04
how would I go about creating a rsync job in crontab which copies data from specific dirs to a folder on my remote server?

I've used rsync in the past but has always been the machine which initiates rsync has the data written to it.

---

### Post by Insightfill on 2007-10-04
The biggest differences between local rsync and remote are that of authentication and algorithm.

Auth: Unless you're there to actually supply the password for ssh, you'll need to create a keyset on the remote machine to automate the connection.  Since you want to use cron, you'll need to create a pair of keys and append one set onto the remote machine.

Algorithm: If files are on the same machine, the rsync uses a "whole file" approach.  If files differ, then whole files are copied and replaced.  On a remote rsync, the best approach is a partial one, where only the parts of files that are different.  It takes a while to compare the files, but the bandwidth tends to be narrower, so it's worth it.

I found the [following article]("http://lee.org/blog/archives/2005/09/21/using-cygwin-rsync-ssh-and-the-internet-to-backup-my-xp-computer/") useful.  It's actually about using cygwin to backup windows machines, but the basics still apply and the syntax isn't really any different.  I had actually used an approach similar to this to create a DOS batch file to script a backup of my dad's Windows XP machine to my linux machine over the internet.  The initial backup takes a week or so, but the updates are quick.

Also: look up [rsnapshot]("http://www.rsnapshot.org/") and [backuppc]("http://backuppc.sourceforge.net/") for a couple of other approaches that may help.

---

