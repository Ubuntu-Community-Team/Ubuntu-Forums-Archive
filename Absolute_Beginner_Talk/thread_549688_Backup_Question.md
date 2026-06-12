---
title: "Backup Question"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by snevensmores on 2007-09-12
I've had to reinstall Ubuntu a handful of times lately because I'll mess it up and it won't boot into KDE correctly, etc (since I still am very much a noob). Once I get this installation exactly how I want it (with installed apps and such), I'd like to make a backup of important files on cd or usb drive. That way, if I ever have an issue, I can just boot up using the live cd, mount the file system, and restore the corrupted files.

My question is... outside of obvious "important" documents, pictures, etc., what files/directories do I need to make sure to back up? I've learned from experience that xorg.conf is definitely on the list. I just didn't know if there's a consensus group of files and directories that I'd be wise to back up in hopes of restoring a corrupted system. Thanks in advance for any advice that you all can provide.

---

### Post by reckless2k2 on 2007-09-12
seriously look into tar and gzip your whole kit and kaboodle......you might be surprised how little space it takes up. the on reinstall......after reinstall....blow the tar file out and it'll pop everything back in place the way you had it.


is that what you mean?

---

### Post by shae on 2007-09-12
Personally there are way too many configuration files to back up when it comes to looking at all of root.  However, as you become more comfortable with Linux, you will have unrecoverable problems less often.  What I suggest doing is after finishing setting up your system just the way you want it, make a backup copy of your home folder.  Most programs store their settings in that folder as hidden files and folders.  This way in the event you have to reinstall, you will certainly have most of your settings backed up.  If you really want to get it set up, you could make an image of your hard disk so you can restore the entire disk to that setup.  However, I have little experience with that method.

---

### Post by Orbital75 on 2007-09-12
I haven't had any experience with this but have heard G4L is a good Image utility.
This will make a Bit for Bit copy of your whole Hard Drive.

Ghost for Linux is a hard disk and partition imaging and cloning tool similar to Norton Ghost. The created images are optionally compressed and transferred to an FTP server instead of cloning locally.

[http://sourceforge.net/search/?words=g4l-v0.23.iso&type_of_search=soft&pmode=0&words=g4l&Search=Search](http://sourceforge.net/search/?words=g4l-v0.23.iso&type_of_search=soft&pmode=0&words=g4l&Search=Search)

---

### Post by bullgr on 2007-09-13
g4l is very good except the second most critical issue (the first is the reliability) in the image backup softwares: speed.

it has three options for compression (and one uncompressed but for the file size is out of question), but any choice you make it's damn, damn, damn slow.

while symantec ghost needs 55 minutes to backup the whole 80 gb hd, the g4l was after 45 minutes in 19% before i cancel the job (and that in the fastest compression option) in the same mashine.

partimage is very fast but you can't make an image backup on a mounted disk (g4l do that) and this is a problem on mashines with one hard disk. another issue is that you need to backup every partition alone (g4l can backup the whole disk at once with all partitions included in the image file (winblows, linux, swapspace)).

i found another solution, not freeware but cheap (29,95$) but i haven't tried yet:
[http://www.terabyteunlimited.com/imagel.html](http://www.terabyteunlimited.com/imagel.html)
maybe this do the job.

if someone know another solution please post :mrgreen:

---

### Post by hyper_ch on 2007-09-13
I'd recommend to make backups of those folders:

/etc
/home
/var

The /etc folder contains configuration for system-wide stuff like daemons/servers/...
The /home folder should contain all user files
The /var folder does have system logs and also if you use mysql the DBs are in there and it's also default folder for the apache webserver

I consider them as the essential backup folder but I do backup more.

Unlike others I don't make images of my system but I use rsync to synchronize between my computer and my backup machine. Once the data is syncronized, I make a hardlink copy to reflect the backup time.
I don't compress anything.

That way I make backups every 6h back  for 90 days and it doesn't use twice the space of the "current backup files" on my computer.

---

### Post by tvrg on 2007-09-13
I think the simplest way is to create an image of your entire disk (clone it to a usb drive or something) using dd from the live cd

check here for a howto: [http://www.joescat.com/backup/disk_image.html](http://www.joescat.com/backup/disk_image.html) (works for lin disks too)

---

### Post by bubbalouie on 2007-09-14
I run the following script:

> #build a file name
FILENAME=$(date|sed 's/\://g'|sed 's/\ /\-/g')
FILENAME=root-$FILENAME
#tar and compress the wanted files
sudo tar cvpjf $FILENAME.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/dev  --exclude=/home --exclude=/media /

If I break something I can just boot from the live CD and untar the file back to root, this restores everything except user settings.

I also run the following to backup my home directory:

> #build a file name
FILENAME=$(date|sed 's/\://g'|sed 's/\ /\-/g')
FILENAME=$USER-home-$FILENAME
#tar and compress the wanted files
tar cvpjf $FILENAME.tar.bz2 --exclude=.local/share/Trash --exclude=.thumbnails --exclude=Backups --exclude=Downloads --exclude=env --exclude=Music --exclude=Network --exclude=Ryans\ Documents --exclude=Temp --exclude=virtual-drives ~/

The excludes are just locations I see no need to backup as they don't contain settings and can be potentially VERY large.

I hope this helps.

Ryan

---

