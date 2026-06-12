---
title: "Evolution: details of tar backup settings?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by aridus on 2007-12-19
Evolution has a neat File -> Backup Settings (and also a Restore Settings) command that backus up e-mail, notes, settings and so on. It produces a single tar file. I would like to run this backup separately from evolution. Ffor example to put it in a cron job to occur at a certain time, and/or I would like to know exactly what folders (and/or files) are being backed up so that I could instead back them up separately in a different backup software. 

Would anybody happen to know what the (presumably) tar command is that is being used for the backup (and also restore) commands?

With thanks, Martin

---

### Post by blueridgedog on 2007-12-21
I suspect it is simply getting /home/USER/.evolution, but you can tar anything you like and compress it at the same time.

I typically backup my entire home directory with 

tar cvfz 20071221home.tgz /home/USER

This stands for use the tar command, Create File 20071221home.tgz, be Verbose and Zip the file, (I serilize file names) and put in to the file the contents of /home/USER.

You could alternately specify a path for the new file such as

tar cfvz /media/sdb1/20071221home.tgz /home/USER

From here, the sky is the limit, as you can automate the process and have the serialization done automatically, but that is another show.

---

### Post by blueridgedog on 2007-12-21
Sorry, I did not see your "restore" question.

Here is my recipe for restoring from a tar file:

1.  Move the file to a safe location:\
mkdir myrestore
cp myfiles.tgz ./myrestore
cd ./myrestore

2.  Restore the files to your safe location
tar xvfz myfiles.tgz
or, if not gzipped
tar xvf myfiles.tgz

3.  Remove the extra copy of the archive and use any files you need

or

4.  In event of a major problem, simply restore on top of the existing files,

---

### Post by aridus on 2007-12-26
Thanks - although I am not sure quite how this answers my question.

Specifically I would like to know exactly which folders (and files if necessary, e.g. for user settings) the built in Evolution backup/ restore facility is dealing with. I still haven't been able to sort this one out, and I'm not convined that simply backing up the whole of /home.../.Evolution is either required or sufficient.

Many thanks, Martin

---

### Post by blueridgedog on 2007-12-26
The easiest way to find out what the program is backing up is to open one of the files up and take a look.  You can do that with Nautilus or the command line.  I did it and it appears to simply be getting the entire /home/USER/.evolution directory.  I did a comparative test against actually getting the entire directory:

-rw-r--r--  1 james james 53587261 2007-12-26 17:51 evolution-backup.tar.gz
-rw-r--r--  1 james james 53587238 2007-12-26 18:06 test.tgz

(test.tgz is my file getting the entire .evolution directory)

If you want to see what is in the file from the command line you can use:

tar -ftz evolutoin-backup.tar.gz

You can compare what is in the files:

james@ripstop:~/evolutionrestore$ tar -tzf evolution-backup.tar.gz > 1.txt
james@ripstop:~/evolutionrestore$ tar -tzf test.tgz > 2.txt
james@ripstop:~/evolutionrestore$ diff 1.txt 2.txt
james@ripstop:~/evolutionrestore$

Diff returns nothing, so the files are identical.  At that point, I would say it is simply getting /home/USER/.evolution.

So the command for that would be:

tar cvfz mybackup.tgz /home/USER/.evolution

I disagree that backup /home/USER is not required or sufficient.  I feel it is required.  I backup my home directory regularly as it contains my documents and many settings for other programs not just evolution.  I also routinely grab /etc.

---

