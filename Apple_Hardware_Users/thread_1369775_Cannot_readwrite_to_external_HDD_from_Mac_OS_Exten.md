---
title: "Cannot read/write to external HDD from Mac OS Extended NON-Journaled"
date: 2010-01-01
forum: Apple Hardware Users
---

### Post by unobtrusive on 2010-01-01
I read here that Ubuntu can read the filesystem Mac OS Extended NON-Journaled: [http://ubuntuforums.org/showthread.php?t=499665](http://ubuntuforums.org/showthread.php?t=499665)

> Linux supports HFS+, though it has read-write support only for NON-journaled HFS+ partitions (you can disable journalling in OS X) ... if you want to share data, use non-journaled HFS+ (case-sensitive is OK, but not for a boot partition) or plain old FAT32.However, when I plug in the external HDD, and try to write to the folder, it doesn't let me. When I view the permissions of the drive, it shows me the following: [http://img189.yfrog.com/img189/14/screenshotad.png](http://img189.yfrog.com/img189/14/screenshotad.png)

> Owner: 99 - user #99
Group: 99
You are not the owner, so you cannot change these permissionsI formatted the drive on a Mac, so would I change the permissions there?

I need to use a filesystem that can be opened on both a Mac and Ubuntu, but not FAT32 - because I need to transfer files larger than 4GB.

Any ideas?

---

### Post by kmauser on 2010-02-02
I'm trying to mount a HFS+ (non-journaled) partition, which is on an external HD that also has another partition in ext4 format. I'm using 9.10, I've installed the hfsplus utilities, and I'm experiencing the same problem. I've gone through the steps of making sure journaling is disabled. In /etc/fstab I used UUID to recognize the drive, specified my mount point (which I already created and set the permissions on), declared the filesystem type and I even set the options of rw, uid, and gid...

The odd thing is when it first mounts and I view the permissions through the properties menu it seems like the permissions were set correctly according to what I had in fstab (or perhaps what I had set on the mount point - they are the same**); however, if I click on my home directory and go back to the external HD then it says the permissions are for "99 - user #99".

I would really like to get this to work as well as I need to transfer video files larger than 4GB (thus, FAT32 won't cut it) and I'd rather not have to use a Windows machine in the event that NTFS becomes corrupted (I've had to deal with that before and it was a major pain).

Right now I'm just coping them via command line, so that means that the read/write part is working.  Why aren't the permissions?

Any help/suggestions?  I'll repost if I figure anything out.

**It seems as though it is ignoring the uid and gid in fstab completely.  I deleted the mount point and recreated it so root was the owner/group of it.  I left my uid and gid in fstab and mounted the partition.  When I viewed the permissions on the drive it first showed the owner/group as root.  Then when I went to my home directory and came back it showed the owner/group as 99.

---

### Post by wkulecz on 2010-02-02
I'm having the same issue with 8.04 and 9.10 using an external USB drive formatted ext3.  I seemed to recall not having this issue a few hundred updates ago on 8.04.

sudo -i and manually moving stuff around from a command prompt seems the best I can do for now.

--wally.

---

### Post by adam814 on 2010-02-02
If you're able to copy them via the command line I don't think it's a permissions issue.

---

### Post by wkulecz on 2010-02-03
> If you're able to copy them via the command line I don't think it's a permissions issue.

sudo -i gets you a command line as root which overrides incorrect user permissions.  

I'm not on Apple hardware, only suggesting the issue may be a bit more generic with the way external hard drives are automatically mounted vs. the way USB memeory sticks are (which are r/w for the user logged in when they are inserted.

--wally.

---

### Post by adam814 on 2010-02-03
My bad, I thought you meant you were able to as your normal user.

Maybe you could create a group with GID 99 and add yourself to it?  That is if you don't already have a group with that GID (I don't).  Your pic shows it being group writeable.

---

### Post by Nausser on 2010-02-03
Similar issue here. I'm backing up files for a friend that have a new Mac. Their USB drive was FAT32 and the Mac was giving issues copying data from it. 

I then copied all the drives data to one of my drives using Karmic with no issues. I reformatted the drive using gparted to hfsplus and copied all the data back. Their Mac refused to mount the drive at all so I formatted it with their Mac to a journaled hfsplus file system. Now I have the drive back to re-copy the data and of course I don't have write permissions. I've tried chmod, chown, and logging in as root to copy all with no prevail. Why does Mac have to be so proprietary? Don't they know against the grain never works in the long run?

It would be the problem solver if I could get this drive formatted to hfsplus using gparted again, but only have it recognized on the Mac this time. Anything I should do differently?

Thanks for any help!!

---

### Post by mire on 2010-04-27
> **Nausser said:**
> I formatted it with their Mac to a journaled hfsplus file system. Now I have the drive back to re-copy the data and of course I don't have write permissions. 

Journaled HFS+ currently mounts read only by default on ubuntu. This is not a permissions issue its a driver design decision. Use the force  option to mount the drive with read/write permissions or turn journaling off on the drive.  I am aware of no technical  reason for mounting these read only the format is the same but with  journal which is empty if the drive was cleanly unmounted. I have a patched driver that mounts journaled hfsplus read/write and am considering uploading it.

---

### Post by 4plaay on 2011-03-21
> **mire said:**
> Journaled HFS+ currently mounts read only by default on ubuntu. This is not a permissions issue its a driver design decision. Use the force  option to mount the drive with read/write permissions or turn journaling off on the drive.  I am aware of no technical  reason for mounting these read only the format is the same but with  journal which is empty if the drive was cleanly unmounted. I have a patched driver that mounts journaled hfsplus read/write and am considering uploading it.

Okay excuse me for being dumb but how do you force it to mount read/write instead of just read?

I just sold the mac mini and have set up a media center replacement using Ubuntu. Mostly because macs hit about 4 years old and crap out (up to three that have done it now) and when they do your screwed if you want to go to PC with all your software/files. That rant was pointless and off subject but it does explain why I knew very little about how to force a mount to be read/write instead of just read.

---

