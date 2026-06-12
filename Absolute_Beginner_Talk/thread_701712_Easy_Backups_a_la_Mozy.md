---
title: "Easy Backups a la Mozy?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by urbushey on 2008-02-19
The only thing I'm missing now is a backup system that's as seamless and easy to use as Mozy was. ([www.mozy.com](www.mozy.com)) I'm cheap, so I was going with their 2gig free hosting service. Three daily backups of "My Documents" and great peace of mind.

Has anyone ever looked into running Mozy with WINE or a Windows emulator?

Are there other free hosting services I might look into? What program would I use to do automatic backups with?

Is it more worth my while to invest in some storage space, and if so, any suggestions for a service?

---

### Post by fatality_uk on 2008-02-19
> **urbushey said:**
> The only thing I'm missing now is a backup system that's as seamless and easy to use as Mozy was. ([www.mozy.com](www.mozy.com)) I'm cheap, so I was going with their 2gig free hosting service. Three daily backups of "My Documents" and great peace of mind.

Has anyone ever looked into running Mozy with WINE or a Windows emulator?

Are there other free hosting services I might look into? What program would I use to do automatic backups with?

Is it more worth my while to invest in some storage space, and if so, any suggestions for a service?

I would have serious doubts about storing files online. Most of the EULA's that people quickly skip over and click accept usually state, in laymans terms

"We offer this service, free or paid for in a condition we like. If we lose your stuff we'll try and get it back. If we can't tough, you clicked the EULA"

How about a Linux solution? Usually most people can get a small headless Server/PC up and running using something like Debian etch. Once it's on, just leave it and it can act as a central server, web server etc, million and 1 uses. :) I made one from the left overs from various upgrades I have done, so i had a onld mobo, sata HD and some ram. Threw it into a case and there you go. Didn't need much RAM or a good video card ;)

---

### Post by herbster on 2008-02-19
If you're talking about backing up your linux partition, it's a piece of cake. You can use rsync, a magical tool. First, how have you installed Ubuntu-- with a separate / and /home partition or one partition? Use:

```
df -h
```

and paste the output here.

Then you could simply rsync with ssh to a host, like I do with my Bluehost domain (300gb of space, though not free). You wouldn't need more than maybe 20gb, depending on the size of your system of course. You would just really need to set up ssh with the host, which isn't difficult and any host supporting it will have clear instructions on how to do so. Once you have ssh going, just rsync:

```
rsync -avz -e ssh remoteuser@remotehost:/remote/dir /home/urbushey
```

I have mine doing this every night. You can add the "--delete" command to rsync so that it will constantly delete anything on the server that is not in the directory you're backing up, so it's as accurate a clone as possible.

---

### Post by urbushey on 2008-02-27
That looks like a fantastic technique, thanks. 

Now all I need to find is a service that provides cheap web space for this sort of activity. I'm looking into rsync.net, but does anyone else have a service to advertise? Something that's free would be my ideal solution: i'm looking to backup no more than ~1.5 - 2 Gigs of data, (school documents and the like.) Any suggestions?

---

### Post by sicofante on 2008-02-28
I'm doing some research myself on the subject. I've run into this little comparison:

[http://theblogjoint.com/2007/04/10/free-online-storage-roundup/](http://theblogjoint.com/2007/04/10/free-online-storage-roundup/)

A few of these services are free and compatible with Linux. I'm about to try Xdrive. Anyone has any info/opinion about it?

---

### Post by Paqman on 2008-02-28
If you want something simple to use then i'd recommend sbackup. It'll automatically back up  a selection of important files, or you can spsecify what you want backed up, when and where to put the backups. it does restores, too.

---

### Post by herbster on 2008-02-29
Yep, Sbackup is a GUI frontend for rsync and adding a cronjob, good if you don't want to do it the CLI way.

---

