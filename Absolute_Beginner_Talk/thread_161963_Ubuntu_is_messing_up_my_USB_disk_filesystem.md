---
title: "Ubuntu is messing up my USB disk filesystem"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-04-18
I own a 1GB USB drive. I used it a lot on WinXP with no problems. However, I now use Breezy. The USB drive filesystem is FAT32.

For some time now, I have some problems: 0 bytes file sizes, "un-deletable" files, no space on the disk though the only files on it are two 5 kB text files and so on.

My guesss was that something, either Ubuntu or WinXP is messing up the file allocation table, but as long as I used the drive on Windows I encountered no problems. As soon as I started using the drive for EXT2FS to NTFS and NTFS to EXT2FS file transfers, problems occured. So it might be Ubuntu or a component of it.

1. What should I do?
2. If I format the drive so that it uses EXT2FS, will I be able to read/write on it from Windows XP?
3. How do I format the drive (EXE2FS)?

---

### Post by bscbrit on 2006-04-18
If you want to use it with both OS:

The only format that both systems can read and write (reliably) is FAT/FAT32.

Windows cannot read/write ext2 without installing additional software.

Reformat the drive as FAT32.  Make sure that when using it with linux the USB drive is mounted correctly with the correct permissions. :-

[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

If you only want to use it with linux, yes, go ahead and format it as ext2. The command you need is mkefs.ext2 - take a look at 'man mkefs.ext2' for more info.

---

### Post by soonindallas on 2006-04-18
as bscbrit says, FAT32 is a good filesystem to use because it is portable between Linux and Windows.  Even with a 1GB stick you're not getting near the size limit for files and speed is not really an issue with sticks.

As for your comment about running out of space you should be aware that when you mount your drive under Ubuntu it will create an invisible trash folder: this can be confusing because when you delete stuff it does not free up space and the files are hidden in this invisible folder.

Bring up Nautilus, the file browser and select View>Show hidden files (ctrl-h works too) and you will see a folder .Trash-yourusername

To truly delete stuff and recover the space on your drive you need to empty this folder: select all the items, press delete and confirm at the dialog.

---

### Post by zugu on 2006-04-18
I can assure you that the .trash folder was empty.

Anyway, the big issue is that my FAT32 is corrupted in some way, and I think that it's Ubuntu's fault (because the drive performed just fine on WinXP).

So, does anyone know anything about this? Did someone else encountered this issue?

---

### Post by bscbrit on 2006-04-18
If the drive is corrupted, then it will need to be reformatted using the commands that I've already suggested.

If you _know_ that Ubuntu corrupted it then you presumably know how or why.  In which case, please raise a bug report so that we can ensure that the problem is fixed.  If you only _think_ that Ubuntu corrupted it then your choice is whether to risk it happening again i.e. keep using the drive, or to avoid the risk and find some other way of transferring or backing up data.

There are many thousands of USB drives in use by Ubuntu users - I have 2 myself.  I haven't seen this problem so I cannot tell you how to prevent it happening but my first guess is that you didn't unmount the drive before you last removed it.  Unlike in Windows, which uses a different method of read/write to the drive, in linux you have to mount and unmount drives.  If you mount a drive and then write to it, there is no guarantee that the data is fully written to the drive and the associated file contents updated until you unmount the drive.  This is a more efficient method of reading and writing to the drive.  But, if you do not unmount it, then the data on the usb drive could be in an indeterminate state (i.e. not fully updated and the file table could be corrupted).  

Now it is likely that a user might 'blame' ubuntu (or any other linux) for causing this problem but, in actual fact, it is simply that the device and software haven't been used correctly.  When it comes to driving a car, you have to pass a test.  Unfortunately, when it comes to computers, you are expected to learn how to use them without anyone checking that you are able to carry out the various actions correctly.  This is even more difficult for former Windows users - who all think that they are computer literate because they have been using Windows for years.  In fact, they can only use one operating system - namely Windows.  Now that some of them want to use linux (and I applaud them for this and will support them in getting the most out of the experience) they assume that they just do what they have always done and, when it doesn't work, they blame the software.  

This is probably not the case in this instance - you may have discovered a bug in the software that most of us haven't seen.  Please report it with as much detail as you can so that it can be fixed.

For the others for whom this response has touched a raw nerve, please take the time to learn how to use linux before blaming the software for what is, in fact, your own limitation. ;)

---

### Post by zugu on 2006-04-18
Indeed, there might have been some improper use or a bug that caused my problem. Either way, I'll consider both possibilities.

As for the "blaming", in no way was I blaming Ubuntu for whant happened. I just thought that there was some kind of incompatibility with FAT32, or with my hardware. I love Ubuntu and I would never blame it, because it's an operating system that does what is instructed tot do. Tackling problems by blaming isn't constructive at all.

Anyway, thanks for your post bscbrit :)

---

