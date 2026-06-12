---
title: "Auto-run script when file share is mounted? (not USB!)"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by EricDB on 2008-02-01
I've got a NAS file share that auto-mounts when I connect to my home network.  I've also got rdiff-backup set up to mirror my important documents to the NAS (just a single command-line call).  

How can I set it up so that the backup command gets executed every time I connect to my home network, without me having to think about it?

Thanks!

---

### Post by opscure on 2008-02-01
Obviously this share mounts to a directory, so you should think about this logically.
ie if mount directory exists then do something.  so your bash script that you load into your auto-started application should look something like this:

#!/bin/sh
while [ 1 ]
do
if [ -e "/media/share" ]
then
cp /media/share/* /home/user/backup/
else
sleep 1
fi
done

---

### Post by EricDB on 2008-02-01
Thanks for your reply, but that doesn't directly address my need.  Yes, I can make a script that knows whether the backup destination is mounted, and aborts if not...but when does it run?

I could make a cron job to run it every X hours or minutes, but what if I connect to my network 10 seconds after the job fires?  If I'm only connected for 5 or 10 minutes, then the backup won't occur.

Running it every minute or so isn't a good answer, either, since if I'm not mistaken, at least some data is generated for every backup.

I guess the script could maintain its own record of when it last ran successfully, but that's really overcomplicating things, when all I really need is a way to run foo.sh automatically whenever /media/bar is mounted.

---

### Post by opscure on 2008-02-12
if you start this script with the autostarted applications it will run in the background always.  Running a shell script will not take up a lot of resources at all and will preform the necessary functions to detect when the drive is mounted.  Also, you can reduce the time by which it actually checks by increasing the sleep time.  If you increase this to something like 60 then it will check every minute and thus not take up any noticeable resources.

---

