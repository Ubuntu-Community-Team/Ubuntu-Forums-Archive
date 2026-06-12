---
title: "Finally happy with installation, now how can I back it up?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by ld50 on 2007-04-13
Ok, *finally* I am satisfied with my new Ubuntu installation, I must say that the learning curve has been rather steep coming from dumbed-down XP but I think I'm beginning to wean myself of  the Micro$oft nipple.  
Since it has taken so much time and hard work to get to where I am now I would like to be able to backup my system in such a way that it would be very simple to restore.  I guess the ideal solution would be a bootable DVD which would simply rewrite everything back to the hdd the way it is now.  Is this possible or am i just dreaming here?  This would be sooo nice as I would love to experiment with things but am too afraid to mess up my nice new installation. 

Thanks

Oh, and thanks to all here for the much needed assistance in getting me to this point!!!

---

### Post by caffienefree on 2007-04-13
Cdbackup works like what you're asking for CDRWs. Don't know about DVDs...

CD-R(W) backup utility
cdbackup and cdrestore are a pair of utilities designed to facilitate
streaming backup to and from CD-R(W) disks.  Specifically, they were
designed to work with dump/restore, but tar/cpio/whatever you want should
work, so long as it writes to stdout for backups and reads from stdin for
restores.

---

### Post by justleen on 2007-04-13
look into sbackup, a very nice GUI tool for (incrementel) backups..

doenst make bootable cd's though - but you have a live CD! :)

---

### Post by Vladimirm on 2007-04-13
What is it you'd like to do?
Simply create a tarball (i.e backup130407.tar.bz2) ? Or create a live dvd?
I'd suggest the tarball.
Much easier and much quicker.

First make a file called backup.excl
and enter this information into it


.bash_history
/mnt/*
/tmp/*
/proc/*
/sys/*
/etc/ssh/*
/usr/src/*
/home/username/backup130407.tar.bz2

then save and exit that file and enter the command

sudo tar cjfp /home/username/backup.tar.bz2 / -X backup130407.excl

Then wait for a lengthy period of time, remember that this is making a copy of ALL of your files. Everything you've installed, all of your configuration files, everything in your home directory, everything.

If you're ever at a point when you want to restore enter the following commands

cd /directory/that/you/want/to/save/to
sudo tar -xvjpf backup130407.tar.bz2

With the release of the new version of ubuntu, i would advise waiting until then to backup, however thats just my preference, if you want to do it now go for it.

---

### Post by Big Dave on 2007-04-13
You can use a program called [Remastersys](http://www.linuxmint.com/wiki/index.php/Remastersys) to create a live CD of your entire system.

---

### Post by ld50 on 2007-04-13
Ok, creating a live dvd would just create a dvd that boots Ubuntu exactly as it I have it now with all my settings right?  How would that help if I was to totally screw up my installation and wanted to restore everything?  The tarball solution sounds good except it doesnt sound like it would remove anything extra that I installed after the restore point. It would only overwrite existing files, correct?  

As for what I was wanting, I would like to create a restore disc that does not require any functioning OS to be installed prior to using it.  If everything was to be totally messed up, i.e. system will not boot (I am capable of this trust me) I could just insert the disc and it would wipe the partition clean and re-install everything the way it once was.

I'm fully ok with the fact that this may not be possible but it seems that with the amount of work that must go into getting things just right with Linux (some of you will disagree and say this is not true but IT IS!) that something like this would exist.  Heck, I think any distribution that is geared to getting people *started* with Linux should have such a feature implemented as default.

---

### Post by Gallardo Spyder on 2007-04-13
Here you go...  Best way to make a full backup - in case of messing up...

I do a full image copy of my ubuntu installation - somewhat frequently. But specifically before I mess with anything with updating the Kernal, Xserver, Beryl, etc. That way if anything goes wrong - in 15 minutes restoring my latest image - I am back to where I started.

I have used this numerous times - since I like to try new things, latest alpha and beta software (specifically with Beryl and other potential system effecting things.)

I use Partimage from the System Rescue Distro - takes about 15 minutes to do a full partimage and 15 minutes to restore back to the working system if needed.

It also servers as a nice full backup to the entire OS - stored on an external drive, you always have a DR if your main drive goes bad, corruption or other...

Here is a very easy Howto on doing this:

[http://ubuntuforums.org/showthread.php?t=360283&highlight=howto%3A+Backup+a+partition](http://ubuntuforums.org/showthread.php?t=360283&highlight=howto%3A+Backup+a+partition)

Gspyder
Edit/Delete Message

---

### Post by ld50 on 2007-04-13
Gspyder, That is almost exactly what i'm looking for, got to go to class for now, I'll check it out later, Thanks!

---

### Post by psyberpnk on 2007-04-13
@Gallardo Spyder
    Wow, thanks for the tip Sypder.  I have been looking for an app to do exactly what you described.

---

### Post by bratliff on 2007-12-04
Except Parted will not back up to a smaller disk.

Bratliff


> **Gallardo Spyder said:**
> Here you go...  Best way to make a full backup - in case of messing up...

I do a full image copy of my ubuntu installation - somewhat frequently. But specifically before I mess with anything with updating the Kernal, Xserver, Beryl, etc. That way if anything goes wrong - in 15 minutes restoring my latest image - I am back to where I started.

I have used this numerous times - since I like to try new things, latest alpha and beta software (specifically with Beryl and other potential system effecting things.)

I use Partimage from the System Rescue Distro - takes about 15 minutes to do a full partimage and 15 minutes to restore back to the working system if needed.

It also servers as a nice full backup to the entire OS - stored on an external drive, you always have a DR if your main drive goes bad, corruption or other...

Here is a very easy Howto on doing this:

[http://ubuntuforums.org/showthread.php?t=360283&highlight=howto%3A+Backup+a+partition](http://ubuntuforums.org/showthread.php?t=360283&highlight=howto%3A+Backup+a+partition)

Gspyder
Edit/Delete Message

---

### Post by Paqman on 2007-12-04
> **ld50 said:**
> 
Since it has taken so much time and hard work to get to where I am now I would like to be able to backup my system in such a way that it would be very simple to restore.

It's not exactly what you were asking for, but did you know about [this little trick?](http://ubuntuforums.org/showthread.php?t=261366)

You don't necessarily need to back up the installed aps in Ubuntu, only the config files from your /home. So generating a list of your installed aps with the above and backing up your /home does most of the work. Chuck a copy of anything important like /etc/fstab in there, zip it up and you've got a very compact backup that will restore a fresh install back to your setup very quickly.

Or if you've got plenty of storage, take an image of the whole drive like Gallardo Spyder suggested. You can opt to compact it down, but it might still be quite large.

---

