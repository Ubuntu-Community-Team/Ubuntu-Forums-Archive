---
title: "Second hard drive turns to read-only while copying"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by cschoeps on 2007-12-17
Hi,

I'm fairly new to Linux, but have worked out most of my problems except for this one:

I recently reformatted what use to be my Windows drive as another drive to keep media on (My Windows boot gave me a blue screen every time, so I just got rid of it). It is now formatted as ext3. I get to where the drive mounts on start. It used to only let me write when I was root, and I spent the past couple of days figuring out how to let me use it. I ended up just logging in as root, changing the permissions, and logging out again (which I realize isn't the smartest thing to do, but I was frustrated, and it appeared to work). 

I have full access to my drive now, but when I try to transfer data over from an external hard drive, it transfers for a little while and then I get an error while copying, telling me the drive is a "read only file system." When I acknowledge the error, the drive isn't visible in nautilus any more. When I log out and back in, it's there, but trying to access the drive yields: "The folder contents could not be displayed. Sorry, couldn't display all the contents of "MediaDrive".

my /etc/fstab is below:

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=71b25076-4a4c-459f-a500-1b51595c0034 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=89166bd9-3d97-4bef-b072-845a6d65d219 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hda /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/sdb1 /media/MediaDrive ext3 defaults 0 1 

Any help would be greatly appreciated. Thanks! :)

---

### Post by nowshining on 2007-12-17
if u converted via gparition, parttion editor, this may happen - have u tried a reboot and re-trying.

---

### Post by cschoeps on 2007-12-17
I did convert with gpartition, but I have rebooted three different times and tried copying each time with the same results.

---

### Post by nowshining on 2007-12-17
hmmm.

comment out

/dev/sdb1 /media/MediaDrive ext3 defaults 0 1

by doing this

#/dev/sdb1 /media/MediaDrive ext3 defaults 0 1

save and reboot, once rebooted, go to places --> my computer and right-click and mount it - does it ask u for a password, if so input ur password and try again from there.

---

### Post by cschoeps on 2007-12-17
Okay, I've rebooted, mounted from my computer using my password, and have started some stuff copying. Usually it'll freeze after a little bit, and then give me the error message. I'll just let it go and see if an error comes up.

---

### Post by confused57 on 2007-12-18
You also want to check out this guide for mounting a linux partition:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I just added a new hard drive, used this guide, but had to chown & chmod a couple of times before I was able to access as the owner.

---

### Post by cschoeps on 2007-12-18
Okay awesome, if my transfer does go through this time, I'll take a look through that and hopefully it can get me set up the right way. Thanks.

---

### Post by nowshining on 2007-12-18
once u chmod and chown if u don't get the owner, u may need to logout and back in for it to take affect

---

### Post by cschoeps on 2007-12-18
Ok, I'll definitely keep that in mind. The transfer has gone much further than it did before, so that's looking pretty good. If it decides to stop at any point, I'll post again. Either way, thanks for the help!

---

### Post by cschoeps on 2007-12-18
Hmm...the transfer stopped. I got a new error:

Error "I/O error" while copying 
Would you like to continue?

If I hit retry or skip, it just gives me the error again.

If I try to start the transfer over again, I get: Error while copying to "/media/disk-2/Movies". You do not have permissions to write to this folder.

When I go into 'Computer', unmount and attempt to remount, it says:

Unable to mount the volume. Details:
mount:wrong fs type, bad option, bad superblock on / dev/sdb1, missing codepage of helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so

---

### Post by nowshining on 2007-12-18
I/O error sounds like to me ur hard disk is going bad as it shouldn't give any i/o errors at all, i suggest doing a backup of all ur media, off the drive if u can via a/the live cd, rebooting into ur current OS main system, making sure to if automounted the drive to unmount it by right-clicking and in places -- my computer and unmount..

from there open up partition editor -- rescan, from there find the drive and check for errors. :)

---

### Post by cschoeps on 2007-12-18
Ahh, alright that's what I was afraid of. Luckily there's not too much stuff on it. Thanks for the help!

---

### Post by nowshining on 2007-12-18
ur welcome.

---

