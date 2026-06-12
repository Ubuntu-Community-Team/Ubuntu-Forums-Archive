---
title: "Unlock external drive for reformatting?"
date: 2008-02-24
forum: Apple Intel Users
---

### Post by Aurora on 2008-02-24
Greetings,

I have an external Firewire drive I want to use for audio recording with Ardour in both MacOS and Ubuntu.  It has two HFS+ partitions. I thought I would try to reformat one of them to FAT32 so I could read/write with both systems.  I could keep the other HFS+ for backups, or if I want to use Pro Tools to record.

 First of all, is this a good idea for an audio drive? I just read that FAT32 limits the file size, and audio files from recording sessions are huge.  In fact, maybe I should just reformat the whole thing as one partition so I have room.  But will FAT32 be OK?

I use the same user name on all my computers to facilitate this sort of thing.  On Mac OS, the drive is owned by the user, who has read/write privileges.  In Ubuntu, it says it's owned by root, and even with sudo, GParted can't touch it.  There is a lock symbol by the partitions, and all the partition menu items are greyed out.  I tried changing the permissions in Mac OS, by giving the user, the groups, and 'others' all read/write access. Not as secure as I'd like, but I couldn't think of anything else.  Back on Ubuntu, when I right-click and select 'properties', it now says it's owned by '99' instead of root. GParted still can't do anything with it.

If I do sudo fdisk -l, I get:

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

With the 'mount' command, I get:

[my user name]@Studio909:~$ mount

/dev/sdb10 on /media/PPA1.1 type hfsplus (rw,nosuid,nodev)
/dev/sdb12 on /media/PPA1.2 type hfsplus (rw,nosuid,nodev)

What can I do to make this drive work in both Ubuntu and MacOSX?

BTW I'm waiting for Hardy before I even attempt to dual-boot my first revision MacBook.  So for now, we are talking about two computers, a desktop running 32-bit Ubuntu Studio on AMD 64, and a MacBook 2GHz Core Duo running OS 10.4.9.  I have 1GB RAM on the Ubuntu box, and 2GB on the MacBook.

Thanks,

Paul

---

### Post by cyberdork33 on 2008-02-24
FAT32 will likely limit you to an unreasonable file size. 4GB I believe. 

Although your username might be the same in OSX and UBuntu, the underlying userid number (and groupid) are not the same, thus both OSs will still see the equivalently named users as different users.

gParted likely says it is locked because the drive is mounted. You have to unmount it first.

---

### Post by Aurora on 2008-02-24
> **cyberdork33 said:**
> FAT32 will likely limit you to an unreasonable file size. 4GB I believe. 

Although your username might be the same in OSX and UBuntu, the underlying userid number (and groupid) are not the same, thus both OSs will still see the equivalently named users as different users.

gParted likely says it is locked because the drive is mounted. You have to unmount it first.

So I might not have enough room for a long session, and I might not be able to write to the drive with both systems?

Is there a better way to share Ardour session files between OSX and Linux?

FWIW, I have a USB drive I formatted with FAT32 that works on both. I probably formatted it with fdisk or something similar.  Maybe it will work with the Firewire drive, too?

Thanks,

Paul

---

### Post by ronocdh on 2008-02-25
You can get r/w with HFS+ if you just disable journaling. I have an external drive formatted HFS+ no-journaling and it works fine.

Remember in OS X to Get Info on the drive and "Ignore permissions on this drive." It'll make Ubuntu's accessing it much easier. If for some reason you have an unclean mount, you might have to boot into OS X and let the fsck autorun there, then redeclare ignore permissions on the drive.

---

### Post by cyberdork33 on 2008-02-25
> **Aurora said:**
> FWIW, I have a USB drive I formatted with FAT32 that works on both. I probably formatted it with fdisk or something similar.  Maybe it will work with the Firewire drive, too?There should be no difference between the two drives as far as the filesystem is concerned. You can format a FAT32 partition very easily, and it can be used by both OSs, it just has a 4GB filesize limitation.

HFS+ might be a better option if you are ok with opening up the file permissions to everyone like is mentioned in the previous post.

---

### Post by Aurora on 2008-03-03
I reformatted OK, but I still don't get how to give myself full permission on the drive.  I have reformatted it as HFS, not journaled.  I opened read and write to everybody. I can move files to it from Ubuntu, but I can't delete them.  When I right-click the file, "Cut", "make link", "rename", and "move to trash" are greyed out,

I also recorded a test Ardour session on the Mac.  The Ubuntu box can't open the session: It says I don't have write access to the session.  That part may be an issue with the specific session file, not the whole disk. But something is awry at the disk level, as indicated by the inability to delete files.

Though I don't expect plug 'n play between different operating systems, I miss the ease with which I could move my drives among various Macs.  It was part of daily routine when I was studying audio at a local community college.  Everybody carried Firewire drives around to do all their work on, whether at home or at school.

--PD

---

### Post by upforthedownstroke on 2008-03-03
I'm having a similar problem regarding an hfs+ formatted LaCie usb drive. A friend of mine loaned it to me so I could use it as a rescue backup disk for a Windows machine I'm working on. he uses OSX. Every time I try to delete the current contents of the drive to make room for the backup, Ubuntu tells me that the disk is read only. When I attempted to chown it, I was cheerily responded to with a "read-only filesystem" error. is there a way I can format the disk or gain full permissions through Ubuntu?

Thanks.

---

### Post by cyberdork33 on 2008-03-03
> **upforthedownstroke said:**
> I'm having a similar problem regarding an hfs+ formatted LaCie usb drive. A friend of mine loaned it to me so I could use it as a rescue backup disk for a Windows machine I'm working on. he uses OSX. Every time I try to delete the current contents of the drive to make room for the backup, Ubuntu tells me that the disk is read only. When I attempted to chown it, I was cheerily responded to with a "read-only filesystem" error. is there a way I can format the disk or gain full permissions through Ubuntu?

Thanks.yours sounds like you have the filesystem journaled. You must turn off journaling to enable read/write access, and unfortunately, this needs to be done in OSX. If you are not planning to use the external drive with OSX, why don't you reformat it to something more compatible?

---

### Post by Aurora on 2008-03-04
> **cyberdork33 said:**
> yours sounds like you have the filesystem journaled. You must turn off journaling to enable read/write access, and unfortunately, this needs to be done in OSX. If you are not planning to use the external drive with OSX, why don't you reformat it to something more compatible?

Isn't that Catch-22?  He needs to have read-write access to reformat, but he needs to reformat to get read-write access.  Without OSX, he's stuck.  At least I have my Mac in the same room.

So how do I get full read-write access for both computers?  I used Disk Utility to erase the disk, HFS file system, journaling off.  I did not see a menu item that said "reformat" or "format", just erase. However I wrote files to it, so it must have formatted it.  Am I missing something here?

---

### Post by upforthedownstroke on 2008-03-04
> **cyberdork33 said:**
> yours sounds like you have the filesystem journaled. You must turn off journaling to enable read/write access, and unfortunately, this needs to be done in OSX. If you are not planning to use the external drive with OSX, why don't you reformat it to something more compatible?

I was eventually able to plug the drive into a Mac and erase it, although the Mac attempt at formatting with FAT32 failed. At long last I plugged it into a working Windows box and formatted it with NTFS like I'd been trying to and got my backup working. Even so, I'm curious as to why I couldn't just reformat it without dealing with the Mac filesystem at all...

---

### Post by cyberdork33 on 2008-03-04
> **Aurora said:**
> Isn't that Catch-22?  He needs to have read-write access to reformat, but he needs to reformat to get read-write access. No. You do not need read/write access to a filesystem to format it, you do need read/write access to read or write to the filesystem, but "formatting" or "partitioning" does involve accessing the filesystem at all, just deleting or creating a new filesystem.

---

### Post by Keltenbleich on 2008-03-05
I must say all this seems to be very confusing to me.... Has the trouble been fixed at the end the way you wanted? Do you think there's always a solution when dealing with LINUX? Do you think there are more problems with LINUX than with other platforms because of its complexity? Please explain for beginners..!

---

### Post by Aurora on 2008-03-06
> **Keltenbleich said:**
> I must say all this seems to be very confusing to me.... Has the trouble been fixed at the end the way you wanted?

Not yet.   If I merely wanted to use Linux, and not Mac also, it would be no problem.  Also  if the other guy had a drive that was formatted in a Linux-compatible filesystem, no problem.  It is the cross-platform disk sharing that is hanging us up.  It's all Mac's fault ;)

> 
Do you think there's always a solution when dealing with LINUX?

Most of the time, but you may have to work for it.  I have also spent many, many hours trying to work out problems with Mac OSX and proprietary audio software. I spent a year studying audio production with Pro Tools, and I think I spent as much time trying to fix things as I did creating things with the tools. The difference is, I had to pay lots of money to have it fail.  Linux fails for free! LOL  But then you have a huge community to help you fix it, also for free.

> Do you think there are more problems with LINUX than with other platforms because of its complexity? Please explain for beginners..!

I can't claim Linux is as easy to use as other systems...yet.  What the extra effort gets you is freedom from restrictive software agreements, lower cost, and more control over your system.  And geek cred, don't forget the geek cred.

---

### Post by Aurora on 2008-03-07
OK, making significant progress. Here's an update:

I went to the terminal and entered sudo thunar (thunar is my file browser of choice).
Then in Thunar I browsed to the file containing the Ardour session. I clicked "properties", then the "permissions" tab.  It listed the owner as '99' with read and write privileges, the group as '99' with read and write privileges, and Others had, IIRC, read only.  I changed Others to Read and Write access.  A window opened up asking me if I wanted to apply that recursively to all the files and folders inside, and I selected 'yes'.  I know, if I would only learn to use command line tools, this would have been faster. But, it worked.

I was able to open the session with Ardour, but none of the sounds recorded with OSX were present. I could record sounds from Ubuntu.  Maybe this is an application issue rather than a problem with the disk.  I'll do some more experiments and let you know.  But, it looks like the problem is basically solved.

---

### Post by Aurora on 2008-03-30
Is anybody still monitoring this thread?  I am still having problems.

I got so I could record audio onto the drive with both machines.  I then made the mistake of reorganizing stuff into folders from the Mac, and now I don't have permission to the drive in Ubuntu, even though "properties" still says "others" can read and write to the whole drive. So, I can't open the Ardour session anymore.  I could go back to OSX and change the permissions on each individual folder, but that would be really tedious.  I  decided I would change the ownership of the whole drive recursively to my Ubuntu user instead.

When attempts to do this with the file browser failed, I decided to read the man pages for chown and do it with the command line.

It just goes through all the files and folders, and says "read-only file system", for example,

```
pad@Studio909:~$ sudo chown -R pad:pad /media/PPA1.2
chown: changing ownership of `/media/PPA1.2/.DS_Store': Read-only file system
chown: changing ownership of `/media/PPA1.2/.Spotlight-V100/.journalHistoryLog': Read-only file system
chown: changing ownership of `/media/PPA1.2/.Spotlight-V100/.store.db': Read-only file system
```

There is a screen full of this, because the -R option tells it to change every file and folder contained inside /media/PPA1.2.  I see from the output that OSX put all my Spotlight searches and trashed files into hidden files on this drive, and now I don't know how to get rid of them.

Why do I now have no access at all to the drive, even with sudo? How do I change ownership or permissions when it says "read-only file system"?

---

### Post by upforthedownstroke on 2008-04-01
I had a very similar issue. What format is the drive fomatted to? If the drive uses the OSX format with journaling, you're basically screwed unless you're using a Mac only, because the journaled format locks the filesystem for easier use with Time Machine, or so I've heard. Reformat it with a Mac to a non-OSX format that will work for you cross-platform and you should be fine.

---

### Post by upforthedownstroke on 2008-04-01
> **Keltenbleich said:**
> I must say all this seems to be very confusing to me.... Has the trouble been fixed at the end the way you wanted? Do you think there's always a solution when dealing with LINUX? Do you think there are more problems with LINUX than with other platforms because of its complexity? Please explain for beginners..!

Well, I wouldn't go so far to say that the problems I've had in Ubuntu (Which are less than OSX and Windows thus far) are due to its complexity; rather, most of them have had to do with cross-platforming. Linux, specifically Ubuntu, as a platform for beginners is a GREAT idea because the pre-installed software is just about all you need for the basic internet/word processing/email user, and the update manager keeps things up-to-date and secure. Also, the community support makes any problem you may have a piece of cake because there are people out there who know what to do, and will willingly help out. Many of the cross-platform problems I've had with Linux have been easily solved within Linux with the exception of this OSX filesystem problem.

---

