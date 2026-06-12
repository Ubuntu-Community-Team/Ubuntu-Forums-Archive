---
title: "usb memory sticks"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by kfehr911 on 2007-05-22
I'm unable to clear my memory stick because I don't have the correct permissions.  What can I do?  
I'm about to try to clear it in terminal use sudo I hope that works but is there a better proper way?  The permissions are set to create and delete files so what is the problem.  Is there some links that I could read to know how to properly use usb memory sticks  in ubuntu? Thanks

---

### Post by diatribe on 2007-05-22
try using google search for memory stick ubuntu, but I don't understand why it won't let you delete things off of it.  also, 'trying sudo' is a bad practice and can lead to you breaking your system if you aren't careful.

---

### Post by richaoj on 2007-05-22
i had a similar problem.  i tried and tried many different things, but what i ended up having to do was backing up anything important that was on the usb disk, and then reformatting it using gparted.  after that, it has worked fine . . .

---

### Post by maob on 2007-05-22
Well, sudo isn't all that bad, because it's actually a security measure so you don't need to do things using root--which is far more powerful and is far more prone to doing something stupid..

I'm not an expert, but here it goes...

I presume that your memory stick is automatically mounted right? Since the system automatically mounts your memory stick when you plug it, the "owner" and the "group" of the memory stick becomes "root" by default.

Since you don't (and probably can't) login as root, you need sudo to access root commands.

To clear data from your memory stick, you need to access it via root--or in this case via sudo (i'm assuming you're using Gnome as your desktop manager):

```
$ sudo nautilus
```

Then hit the return key.

After having done that, you'll be asked for your password and then a nautilus window will open. Then navigate to the location of your stick (or click on it on the Places bar).

Since you're running this nautilus using sudo, you have all the privileges and permissions to your stick--just like if you logged on using root..

:D

---

### Post by Mr.Beast on 2007-05-22
> **maob said:**
> Well, sudo isn't all that bad, because it's actually a security measure so you don't need to do things using root--which is far more powerful and is far more prone to doing something stupid..

I'm not an expert, but here it goes...

I presume that your memory stick is automatically mounted right? Since the system automatically mounts your memory stick when you plug it, the "owner" and the "group" of the memory stick becomes "root" by default.

Since you don't (and probably can't) login as root, you need sudo to access root commands.

To clear data from your memory stick, you need to access it via root--or in this case via sudo (i'm assuming you're using Gnome as your desktop manager):

```
$ sudo nautilus
```

Then hit the return key.

After having done that, you'll be asked for your password and then a nautilus window will open. Then navigate to the location of your stick (or click on it on the Places bar).

Since you're running this nautilus using sudo, you have all the privileges and permissions to your stick--just like if you logged on using root..

:D

Just a quick question to tag onto this thread as it's sort of pertinent and relates to the topic. (I'm thinking similar sorts of issues occur not just with flask keys but with external hard disks as well.  Normally NTFS formatted.  
Is there a way that you can add your userID into a group to grant it the correct permissions to an external disk.  I'm sure that there are command lines that will do so suitably as well, but I'm getting the impression that the main way to do anything in Ubuntu is to Sudo (I'm not saying it's a bad thing, but I do think that it puts an additional technical element in that Windows doesn't have currently (till you get to vista and the UAC does just this, but without the password requirement!!)
for certain devices that will be ported between systems, is there a simple way to grant RW access to them on a permanent basis, or perhaps a point and click method. (Even if it's a script on the desktop)

I'm just of the mindset that Ubuntu will encourage more people over from Windows on a permanent basis if we make things easier for them, and the command line is not the best place for this activity.  
Is there a script repository? and how easy is/are the scripting languages to learn?  I'm thinking of more batch file level in dos/windows, more than VBscript.
many thanks

---

### Post by darkworld on 2007-05-22
> **Mr.Beast said:**
>  I'm sure that there are command lines that will do so suitably as well, but I'm getting the impression that the main way to do anything in Ubuntu is to Sudo (I'm not saying it's a bad thing, but I do think that it puts an additional technical element in that Windows doesn't have currently

Its my understanding that the reason Linux doesnt have such an issue with viruses is because it doesnt run everyhting wide open, that is you need system rights in order to destroy things.

Coming back to the issue of rwx, user, owner and groups. Its a little stressing at first but easy once you have done a bit of reading. The problem in the transition is that people are used to windows doing everyhting for them. However they fail to realize that they never really know exactly what windows is doing? For the good or bad maybe.

Linux empowers the user but the cost is a learning curve and plenty of reading. [http://www.linuxcommand.org/index.php]("http://www.linuxcommand.org/index.php")

---

### Post by kfehr911 on 2007-05-23
Thanks for everyones help!  I Have tried a few thing ans I will share the results.
> Well, sudo isn't all that bad, because it's actually a security measure so you don't need to do things using root--which is far more powerful and is far more prone to doing something stupid..

I'm not an expert, but here it goes...

I presume that your memory stick is automatically mounted right? Since the system automatically mounts your memory stick when you plug it, the "owner" and the "group" of the memory stick becomes "root" by default.

Since you don't (and probably can't) login as root, you need sudo to access root commands.

To clear data from your memory stick, you need to access it via root--or in this case via sudo (i'm assuming you're using Gnome as your desktop manager):

Code:

$ sudo nautilus

Then hit the return key.

After having done that, you'll be asked for your password and then a nautilus window will open. Then navigate to the location of your stick (or click on it on the Places bar).

Since you're running this nautilus using sudo, you have all the privileges and permissions to your stick--just like if you logged on using root..

I was a great suggestion but it didn't work.  The files were move the the trash but  I was unable to empty the trash because nothing is there?  The properties list that only 284mb free space.  It is a 2gb drive?  I previously screwed the files up by trying to remove them not through root maybe that is why the trouble.  It is a great idea and I'm sure that will help me in the future.

What I'm looking at right now is using gparted to reformat because I think that it would be useful to be using the same linux/unix format. ! !Please correct me if I wrong! !  I believe that it might be a format issue because usb are formated for a windows or mac right.  I just waiting for a reply on what I should fornat the usb drive too.
> i had a similar problem. i tried and tried many different things, but what i ended up having to do was backing up anything important that was on the usb disk, and then reformatting it using gparted. after that, it has worked fine . .  

 As for the rest of the conversation... script is not that scary it is one of the thing that attracted me to using a linux based system.  With every new command I learn is applicable though out the whole system?  That is a good thing.  It is quite easier to use command in a sense because you can see directly what is happening.  Using a GUI you are left with little information and window that you simply click ok  not knowing what is happening.  I very new and have little time and ever minute I spend using script I feel fulfilled.  Like I'm learning more important details to the system.  And for the record I'm a cut and paste terminal user when thing get over my head.  So see script is quite portable.  Like Copy and Paste.  Cheers  Thanks again!!

---

### Post by drowner on 2007-05-23
BEFORE you reformat:

> **kfehr911 said:**
> Thanks for everyones help!  I Have tried a few thing ans I will share the results.


I was a great suggestion but it didn't work.  The files were move the the trash but  I was unable to empty the trash because nothing is there?  The properties list that only 284mb free space.  It is a 2gb drive?  I previously screwed the files up by trying to remove them not through root maybe that is why the trouble.  It is a great idea and I'm sure that will help me in the future. 

I suspect you have NOT screwed anything up.... your files have been deleted to a ./trash directory on your USB drive. This is a hidden folder.

open the USB drive in nautilus, and press ctrl+H to show the hidden files. Is that youre trouble?

> **kfehr911 said:**
> 
What I'm looking at right now is using gparted to reformat because I think that it would be useful to be using the same linux/unix format. ! !Please correct me if I wrong! !  I believe that it might be a format issue because usb are formated for a windows or mac right.  I just waiting for a reply on what I should fornat the usb drive too.
 

USB drives are usually formatted as FAT32, which is good for windows, mac AND linux. There is no need to format the flash drive as a linux filesystem (like ext3) if you intend to use it for data-moving/storage, as it then will be unreadable to most windows systems.

---

### Post by maob on 2007-05-25
> **drowner said:**
> 
I suspect you have NOT screwed anything up.... your files have been deleted to a ./trash directory on your USB drive. This is a hidden folder.

Yup, that's right.. There are actually multiple "trash" folders within the filesystem. The first and main one is the one for the whole filesystem. Then each mounted drive receives its own trash folder..

Trash folders won't show up on nautilus since it's actually a hidden folder, which means that its name is prefixed with a period (i.e. ".")--like ".Trash" or ".Trash-Astursky", which is the name of my own usb drive..

As drowner said, all you have to do is show the hidden files on nautilus by pressing 

```
Ctrl+H
```

Or by navigating to **View > Display Hidden Folders**.

I guess you tried looking at the main trash folder right? When you deleted files from your USB drive, it didn't go to the main trash folder, it went to your drive's own trash folder. So navigate to your drive and look for the trash folder there.

One difference between Windows and Ubuntu is that when files are deleted from a USB drive in Windows, they are lost forever, and can't be recovered through the Recycle Bin. But in Ubuntu, files are still there until you decide to empty the trash bin..

Cheers!
:D

---

### Post by kfehr911 on 2007-05-27
Thanks for the trash info.  I will use that in the future.  I ended up refomating the drive and that woked fine.  I will use the trash folder next time.  What about the format of the drive?  I believe that I used FAT16 is that OK?

---

