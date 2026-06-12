---
title: "File Backup Software Questions"
date: 2012-03-22
forum: Any Other OS
---

### Post by ken0069 on 2012-03-22
I've got a multi boot system running Mint 11 and also various versions of Windows on individual hard drives.  One of those drives is a 1TB drive and it has a storage partition on it.  So far I've tried 3 different Linux backup tools from the software section but all of them turn those backups into either encrypted, oddball and or compressed files, which I do not want.  

The last one I tried was simple backup suite and even though it has a box to NOT compress the files I want backed up, it makes a tar ball anyway on that storage drive and I can't see how to stop that?

So basically all I want done is to have a program that will automatically transfer/backup folders/files from linux to that storage drive without doing anything to them, ie, example, Downloads, Pictures and Documents folders copied to that storage drive's backup folder?

Anyone know of a program that will do this?

Thanks,

Ken

---

### Post by zombifier25 on 2012-03-22
What you're looking for is rsync. It's a very smart command line tool that will transfer files between two places, with the option of transferring only new/modified files and deleting files that are no longer on the source.
Syntax:
```
rsync -av --delete /source/folder /source/folder/no/2 /source/folder/no/blabla /destination/folder
```The -av parameter is to sync only files that are new or modified, and the --delete parameter is to delete files that are no longer on the source.

---

### Post by Roasted on 2012-03-22
> **zombifier25 said:**
> What you're looking for is rsync. It's a very smart command line tool that will transfer files between two places, with the option of transferring only new/modified files and deleting files that are no longer on the source.
Syntax:
```
rsync -av --delete /source/folder /source/folder/no/2 /source/folder/no/blabla /destination/folder
```The -av parameter is to sync only files that are new or modified, and the --delete parameter is to delete files that are no longer on the source.

Bingo. I'd recommend exactly this.

I just set up a How To involving rsync, but it was over the network so it may be a bit beyond what your target is. If you're curious in reading, it's here:

[http://ubuntuforums.org/showthread.php?t=1943882](http://ubuntuforums.org/showthread.php?t=1943882)

I set up mine to run when I log in through "Startup Applications". It works pretty awesome. I'm very happy with rsync.

---

### Post by Perfect Storm on 2012-03-22
Moved to Other OS/Distro Talk.

---

### Post by LewisTM on 2012-03-22
Just want to add that there are several nice graphical frontends for rsync, just type rsync in the Software center or Synaptic. 
They remove the need to remember command switches, can save backup profiles and some of them will even schedule backups for you!

Cheers!

---

### Post by Roasted on 2012-03-22
> **LewisTM said:**
> Just want to add that there are several nice graphical frontends for rsync, just type rsync in the Software center or Synaptic. 
They remove the need to remember command switches, can save backup profiles and some of them will even schedule backups for you!

Cheers!

While I agree with you, the man pages are just so darn easy to read. ;) But nonetheless, I'm a big fan of "grsync" when it comes to rsync GUI's.

Not to mention, with grsync you can schedule it with crontab, startup applications, or scheduled tasks (gnome-schedule in the repos). The only command that you need to know when setting up a schedule for grsync is this:

grsync -e profilename

When you create a grsync profile, let's say you name it backup, you would do:

grsync -e backup

The nice thing about doing that instead of the regular rsync command like I had voted for was you get an actual visual as to whether there were any errors. That can be kind of nice to have.

So while "grsync" may not have a built in scheduling feature right in the GUI, it's very, very easy to patch it into some sort of scheduler application or cron job.

The only downside I'm noticing with grsync, and I only noticed it JUST now, is it doesn't seem to play nice with multiple sources. For example, my rsync command goes something like this:

rsync -az /home/jason/Documents /home/jason/Pictures /media/storage

If I manually put in /home/jason/Documents and /home/jason/Pictures, the simulation run fails. However, the syntax is accurate... If you want to specifically back up only certain folders and you're using grsync, maybe it'd be easiest to create a separate profile for each source. *shrug* I'm not sure otherwise... but this does make me curious...

EDIT - I found [THIS]("http://redwolfinternet.com/?p=103") but the option in question doesn't exist on grsync on my 12.04 virtual machine...

Also, make sure if you use grsync with gnome scheduler that you set the one flag properly. I had it set to "default behavior" which wouldn't launch grsync. You have to make sure you choose X application, as noted in post 8 [HERE.]("https://bugs.launchpad.net/ubuntu/+source/gnome-schedule/+bug/331742")

---

### Post by ken0069 on 2012-03-22
> **LewisTM said:**
> Just want to add that there are several nice graphical frontends for rsync, just type rsync in the Software center or Synaptic. 
They remove the need to remember command switches, can save backup profiles and some of them will even schedule backups for you!

Cheers!

Hey Lewis, you da man!!  I'm not much of a command line guy so the GUI is for me.  

And BTW, I've been running and still run Ubuntu on two of my other computers which are multi-boot also so if this works I'll install it on those as well.  

The reason for this is that back last year I had a Ubuntu OS refuse to boot and it put me in a bad way because of some of the files I had in the downloads folder.  I tried to access those files but couldn't and finally did get to them by installing Ubuntu on another drive with the same username and password and I was able to get the stuff off.  If this backup deal works, then each day those files will automatically be transferred to that storage drive, which is NTFS and the Windows OS on that same computer will allow me to access them.

And thanks again.  And I'll let you know how this works out when I come back to mark this topic as solved!

Ken

---

