---
title: "Help with Thunderbird"
date: 2006-02-04
forum: Absolute Beginner Talk
---

### Post by Magellan on 2006-02-04
I was using Thunderbird as my email client in Win2k.
I have set up a dual boot with Ubuntu and Win2k.  I mounted the Win partition that contained my Thunderbird email files.

I installed and set up my email account in Thunderbird within Ubuntu, but can't get it to recognize the files on the Win partition.

Under the Account Settings for the Local Folders, I set the Local Directory to the directory on the Win Partition (/media/windows/data/Thunderbird).  I have shut down and restarted Thunderbird.  I seel a list of folders under the Local Folders (Inbox, Sent, etc), but my messages aren't there.

I was hoping to have access to the same downloaded messaged regardless of what OS I booted into.

When I navigate to that directory from outside of Thunderbird, I can see files like Inbox, Inbox.msf, etc.  It looks like 2 files per folder.

I opened up one of the files (without the .msf extension) in a text editor, and I see my email, so I am pionting to the right place.

Can I not share the files acorss OSes?  Do the versions of Thunderbird use different file formats?

Thanks,

James

---

### Post by aysiu on 2006-02-04
These two threads may help:
[http://ubuntuforums.org/showthread.php?t=22795](http://ubuntuforums.org/showthread.php?t=22795)
[http://www.ubuntuforums.org/showthread.php?t=29021](http://www.ubuntuforums.org/showthread.php?t=29021)

However, keep in mind that to share a profile, you should be using FAT32 in Windows. Windows 2000 is usually formatted as NTFS, so you may have to create a FAT32 partition.

The easiest way I've found to "share" emails across operating systems and computers is to just use IMAP instead of POP.

---

### Post by Magellan on 2006-02-04
I read those threads.  The partition is vfat, so that isn't the prolem.

IMAP is on my list for when I host my own email, but for now, I hae to retrieve from a pop server.

---

### Post by Magellan on 2006-02-04
I unmounted and re-mounted the partition, but that didn't help.

I also tried deleting and re-adding the profile.
When setting up the profile, I set the folder location to the existing folder location, but now I get an error indicating the folder is in use.

So, I thought I'd create a new folder on the FAT partition and then copy the files over and change the TB copy in Windows to use the new folder.

I was unable to do that because I do not have write permissions on the FAT folders.

I tried sudo +777 /media/windows_2/data/new_folder_name, but it had no effect.  No error msg, but no effect.

Can I not alter the permissions on a FAT partition?

---

### Post by aysiu on 2006-02-04
FAT32 doesn't support user permissions.

If you don't have write permissions on the FAT drive, you may have mounted it incorrectly. Can you post your /etc/fstab?

---

### Post by Magellan on 2006-02-04
Thanks.  That pointed me in the right direction.  I had mounted the partition from the System-Administration-Disks, and there was no place for any options.  I read up on fstab and mounting and I set up fstab as follows:

/dev/hda5       /media/Windows_2 vfat suid,rw,gid=1000,uid=1000,umask=000,dmask=000,fmask=000 0 0

1000 refers to my userid and group.  I think this is probably overkill, but I don't understand all the options.  I got this from another poost and tweaked it accordingly.

After doing this, I pointed my TB Profile to the same folder as I use in Windows, but instead of using the files in that folder, it created another folder within there called MAIL and thena LOCAL FOLDERS folder within that.  I put a copy of the inbos file in there and I see my email messages in TB now.  

I think I'll copy all the folder files into there, then point the Windows version to the same folder.  I'll post the results later.

Let me know if there is anything I should change about the fstab entry.

Thanks for the help.

---

### Post by aysiu on 2006-02-04
I don't know what all those options mean either, but this has always worked for me: ```
/dev/hda5 /media/Windows_2 vfat iocharset=utf8,umask=000 0 0
```

---

