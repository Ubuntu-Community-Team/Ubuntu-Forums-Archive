---
title: "[SOLVED] Copy /home"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-10-20
What I want to do is to copy my home directory, including all hidden files, so that I may upgrade and then copy it back to the new setup and use the same program settings.

However, when I try to copy over the files for a lot of them I get a message "Operation not Permitted".  This appears even when running as root.

I thought that perhaps this was because the files were in use and  I would be able to get round this by booting from a Live CD and then copying the files over.  Not so.  In the case of the Live CD I get a message which says that I do not have the permissions to do this.   I wonder what permissions I am supposed to have since if a Live CD is used are the permissions of the files on the hard drive not a separate issue?

What is the best way of simply copying over the home directory and all its sub directories and hidden files?

---

### Post by kolinab on 2007-10-20
I copy my entire /home regularly to an external HD using a program called 'rsync.' If you search for 'grsync' in the repositories you'll find it - It can be run from the command line, is powerful, and also come with a graphical front end, which I like.

---

### Post by bsharp on 2007-10-20
```
cd /home
sudo tar -cjvf homebackup.tar.bz2 *yourusername*
```

to replace:
```
sudo tar -xjvf homebackup.tar.bz2 /home
```

---

### Post by ofb on 2007-10-20
Speaking of rsync
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

expatCM, where are you trying to copy to? I get similar errors when I do a quick drag'n'drop backup to my fat32 drive because fat32 can't handle all the characters that ext3 can.

---

### Post by expatCM on 2007-10-20
I am trying to copy from an ATA drive to a SATA drive which is used for data files.  The file system of the target drive is fat32.  Could this possibly be the problem?  I remember some time ago having to stop attempting to use Unison since there were problems synchronizing between ext3 and fat32.

---

### Post by ofb on 2007-10-20
> **expatCM said:**
> The file system of the target drive is fat32.  Could this possibly be the problem?

Yeah, there are various character allowed in ext3 file names that are not allowed in fat32. A quick dodge around the problem would be to make your backup an archive, then copy that over.

---

### Post by Hospadar on 2007-10-20
are you using the recursive operation for cp?
```
sudo cp -**rf** /home <destination>
```the 'r' is for recursive, the'f' is for force (doesn't ask you for write-protected files and some other wierd things)

This might not be your problem at all, but maybe it is.

Edit:
I would bet, that your problem is the fat32 filesystem.  fat32 allows files of a maximum size of 4gig.  If you are using fat32 so you can read it from windows, I would consider reformatting the extra drive to ntfs and then use the ntfs-3g drivers from linux.  they are very easy to use and stable and provide full read-write support.  also they come with the ntfs-config tool to setup your fstab to mount your ntfs volumes properly.

I guess if you have not a single file greater than 4 gig maybe this isn't your issue, but i'd put money on a different filesystem solving this problem.

---

### Post by expatCM on 2007-10-21
I have just moved some directories off an ext3 partition to create space.  I then tried to copy the home directory.

It worked.

So the conclusion has to be that copying from ext3 to fat32 does not always work.

It has been suggested that I copy to an archive and then move that over.  Yes, I had not thought about that ....  my concern would be that I do not automatically want to unpack the whole archive, I know I can view and selectively unpack but ...  I do like to keep it simple.

Thanks to everyone for your comments on this thread.

---

