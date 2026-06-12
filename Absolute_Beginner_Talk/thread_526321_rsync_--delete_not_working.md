---
title: "rsync --delete not working"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-08-15
im trying to backup a disk (on my laptop) to another disk (on desktop) accross the network.

all seems to be fine but the receiving end is not deleting old files which are now no longer on the host(server)

here is the command im using

sudo rsync -avz --delete -e ssh pete@192.168.2.3:/home/* /media/hdb
[edit] also tried without the *, just /home

now this should backup everything within /home to /media/hdb on my desktop PC, which it does. but when I delete a file on the laptop, it does not sync up on my desktop.

i've checked the perms, and seem to be fine, also running rsync with sudo shouldn't be a problem.

ideas?!
tia

---

### Post by scrooge_74 on 2007-08-15
try downloading grsync which is the GUI front for rsync, it did work for me doing that

---

### Post by PetePete on 2007-08-15
i'd rather not download a gui, prefer the hands on approach ;)

ive found that if i issue the command, 

sudo rsync -avz --delete -e ssh pete@192.168.2.3:/home/pete /media/hdb

it will start deleteing all the old files..
quite confused now.

---

### Post by PetePete on 2007-08-15
ive changed my folder structure around a bit, and I'll try and make this more clearer.

This Works.... (but i dont want to manually specify each folder within the source /home)
sudo rsync -avz --delete -e ssh pete@192.168.2.3:/home/pete /media/hdb/home

This Doesn't work: (with only archive, not delete files)
sudo rsync -avz --delete -e ssh pete@192.168.2.3:/home /media/hdb

---

### Post by PetePete on 2007-08-16
bump?

---

### Post by j2fraser on 2007-08-16
1st, I'm no rsync pro -- never used it before! But, I am interested in learning about it, which is how I stumbled on this thread...

2nd, [[COLOR="Red"]this expanded rsync man page[/COLOR]]("http://www.hmug.org/man/1/rsync.php") indicates that the "--delete" option "...has  no  effect  if  directory  recursion  is  not  selected." Although I understand directory recursion to be implied by the use of the "-a" option, is it possible that the "--delete" option relies on the explicit use of the "-r" (recursion) option? As the man page suggests, perhaps a "dry run," using the "-n" option would be informative!

Good luck -- let us know if and how you straighten this out...

---

### Post by talby on 2007-08-16
> **PetePete said:**
> ive changed my folder structure around a bit, and I'll try and make this more clearer.

This Works.... (but i dont want to manually specify each folder within the source /home)
sudo rsync -avz --delete -e ssh pete@192.168.2.3:/home/pete /media/hdb/home

This Doesn't work: (with only archive, not delete files)
sudo rsync -avz --delete -e ssh pete@192.168.2.3:/home /media/hdb

Try "sudo rsync -ave ssh --delete pete@192.168.2.3:/home/ /media/hdb/home", the extra "/" on ":/home/" means "treat the source as a dir" rather than ":/home" which means to treat as a file.  Also the "-z" for compression will just slow things down & create a higher cpu load on a fast network (100 or 1000).

cheers

---

### Post by PetePete on 2007-08-16
thanks for the reply and clearing up the trailing / issue, but it still isn't removing old files :(

due to an unrelated issue (hdd failure) I had to re-install ubuntu on the desktop, but the issue still persists.

could it be something to do with fact that i'm logging into my laptop with a normal user ID, which can't access all of the /home directories, and this causes later problems?

................
Just enabled the root account and tried logging in with root and everything synced up perfectly.
Maybe this is a possible bug with rsync that needs reporting? I understand that my user account wont be able to access any others on /home, but surely it should sync its onw /home folder perfectly?!

---

### Post by talby on 2007-08-16
> **PetePete said:**
> Just enabled the root account and tried logging in with root and everything synced up perfectly.
Maybe this is a possible bug with rsync that needs reporting? I understand that my user account wont be able to access any others on /home, but surely it should sync its onw /home folder perfectly?!
I completely missed that, it's not a bug at all only root@remote can access all the remote home dirs you have it exactly right.  That is why pete@remote can only sync pete@remote:/home/pete/ to the backup box good call mate :)

another option would be to set up the same user names on both boxes and have each home dir sync independently or automated in cron using shared passwordless ssh keys using ssh-keygen or even create a "backup" user that can access group level permissions on the remote host.

cheers!

---

### Post by PetePete on 2007-08-17
good idea to create backup user, think I'll do that , sounds better than enabling my root :P

but my problem was that pete@remote couldn't sync up /home/pete if I asked it to sync up /home (as i have other folders in /home which arn't home dirs) and the (correct) errors about not having permissions to access /home/otherUsers somehow caused it not to sync up /home/pete correctly. 

Where as if i asked it to just sync up /home/pete it would do this 100% correctly.

Basically asking rsync to sync up /home with a username should sync up the usernames home folder and any other folders which that user has access to then throw up errors to other users dirs (which it should). but In this case rsync would only add files to /home/pete but not delete old files.

anyway i dont care now, going to create a backup user with full perms !

thanks for the help, much appreciated.

---

