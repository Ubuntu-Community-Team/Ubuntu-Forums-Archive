---
title: "Ubuntu Installation Newbie"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by agregal on 2006-03-28
I'm an absolute newbie when it come to Linux and Ubuntu. I have been using Windows for years and I thought I needed a change.  Forgive me if my question sounds so simplistic but I really don't have a full understanding of Linux.

I'm setting up a dual boot system on my Dell Inspiron 8500 laptop with Windows XP and Ubuntu 5.10.  I used the Install disc and created different partitions my original partition was NTFS.  I also set up a FAT32 and a Swap partition as recommended from the following site:

 [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

Everything seemed to go along fine but when I booted to Ubuntu on the desktop I don't have the icons for the different partitions (disks) [I hope I'm using the right terms].  According to that website, there should be icons for my NTFS filesystem and my FAT32 filesystem.  But they aren't showing up.  

What am I doing wrong and how do I get those icons on my desktop?

---

### Post by IDipSkoalMint on 2006-03-28
You may need to mount them manually. I have a thread about mounting, which you can find [here]("http://www.ubuntuforums.org/showthread.php?t=151448"), in which people were extremely helpful, it may be of some use to you. Best of luck.

---

### Post by gabruo on 2006-03-28
If you want to view your partitions in a GUI, try downloading gparted, or qtparted from the Synaptic package manager.  You will be able to view all your partitions and their sizes then.  If you are hoping to access you other partitions through gnome or KDE then I don't know if this is even possible as I am a noob myself.  Hope I understood your question. good luck.

---

### Post by Obor on 2006-03-28
you can also follow the guide on [wiki]("https://wiki.ubuntu.com/MountingWindowsPartitions")

---

### Post by Mustard on 2006-03-28
The link given in the previous post should work well.  Another link you can look at is this one...

[http://easylinux.info/wiki/Ubuntu#Windows](http://easylinux.info/wiki/Ubuntu#Windows)

or even this one..

[http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)

If you have some trouble then I'd like to have a look at your partitions and also your /etc/fstab file, so if you could open a command line and paste the output of these two commands in this thread it would be good.

```
sudo fdisk -l
#this will list all the partitions
```

and

```
cat /etc/fstab
#this will display the contents of the fstab file in the /etc/ directory
```

---

### Post by agregal on 2006-03-28
[http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)   I followed this link to be able to mount my ntfs and fat32 partitions.  I was able to mount them but they disappered yet again after I rebooted my laptop.  I have been at this since my first post over 6 hours ago and I still cannot figure out why the partitions fail to mount on my desktop permanently.

Can someone please explain this to me.  I'm getting so frustrated because I know this should be easy yet I'm having difficulty.

---

### Post by IDipSkoalMint on 2006-03-28
[QUOTE=agregal]Can someone please explain this to me.  I'm getting so frustrated because I know this should be easy yet I'm having difficulty.[/QUOTE]

Take a look at the section of the thread I linked you to earlier that deals with the FSTAB file, editing that made the mount permanent for me.

---

### Post by Mustard on 2006-03-28
[QUOTE=agregal][http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)   I followed this link to be able to mount my ntfs and fat32 partitions.  I was able to mount them but they disappered yet again after I rebooted my laptop.  I have been at this since my first post over 6 hours ago and I still cannot figure out why the partitions fail to mount on my desktop permanently.

Can someone please explain this to me.  I'm getting so frustrated because I know this should be easy yet I'm having difficulty.[/QUOTE]

I could help if you read what I ask you to do. :)  I asked you to show me the output of two commands in my last post, but you haven't shown them to me.  If you didn't know how to do them, then you never said so.  If you are getting error messages, then you should show us the error messages.  You could also explain what you have done already, so we can have some idea of whats going on.

From your current description it seems like you jumped on the first explanation you saw without reading the entire document.   You can mount drives temporarily through the command line but just using mount commands with the relevant options, or you can mount them permanently by editing your fstab file and putting the required information in there, so that they are mounted at boot time.

You can even get a script that will edit the fstab for you automatically, and the instructions for that were given in one of the first links given in this thread.  If you have tried that and had problems, what were those problems?

You need to give feedback on what you are doing, or we are working in the dark.

If you paste the output of those two commands I asked you to paste earlier we can make some progress, or you can keep plugging away at it yourself.  It's up to you.  I would strongly suggest you take the time to read what people tell you the first time it is said, because it becomes a bit frustrating to have to say things twice. :)

---

### Post by agregal on 2006-03-28
According to your link this is what I did:

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows -t ntfs -o nls=utf,unmask=0222 

This is the error message that I got:

wrong fs type, bad option, bad superblock on /dev/hda1, missing codepage or other error.

Right now using different people's idea's I have created directories for mounting the partitions, so far I have

/media
/windows
/media/windows

How do I go about deleting some of them.  When I try I get an error unable to move. access denied.

---

### Post by agregal on 2006-03-28
Well what would be the easiet way to do that since I don't have internet access on the computer that I have installed Ubuntu on. the only thing I can think of is to retype all of the information.

sudo fdisk -l gives me the following:

disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
units = cylinders of 16065 *512 = 8225280

device boot                 start             end          blocks       id    system

/dev/hda1                   1                  2067        16603146   7    hpfs/ntfs
/dev/hda2                   4162             4864        5646847+   5    extended
/dev/hda3                   2068             4161         16820055   83  linux
/dev/hda5                   4257              4864        4883760     b    w95 fat32
/dev/hda6                   4162              4255        754992      82   linux swap/solaris

---

### Post by Mustard on 2006-03-28
[QUOTE=agregal]According to your link this is what I did:

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows -t ntfs -o nls=utf,unmask=0222 

This is the error message that I got:

wrong fs type, bad option, bad superblock on /dev/hda1, missing codepage or other error.

Right now using different people's idea's I have created directories for mounting the partitions, so far I have

/media
/windows
/media/windows

How do I go about deleting some of them.  When I try I get an error unable to move. access denied.[/QUOTE]


The command you show above looks like a total mess. :)  It vaguely resembles what the command should be.

Please compare what you have written above to the proper command..

Your command as shown above...

```
sudo mount /dev/hda1 /media/windows -t ntfs -o nls=utf,unmask=0222 
```

The proper command

```
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

Do they look the same?  No, they are not the same.  Now maybe you typed it wrong in this post but correctly in the command line, that could be the case, but I don't know that.   So the issues is you are not entering the command correctly, hence the 'bad option' erro.  I would suggest you copy and paste the commands that you see from the webpage into your console if that is possible, so as to avoid typing errors.

What you are doing above is only a temporary mount situation.  Further down on that page are instructions for doing it permanently, but I would say you haven't read that far down atm.

Secondly, you still havent shown me the output of these two commands.

```
sudo fdisk -l
```

```
cat /etc/fstab
```

Do you need help with how to copy and paste from the command line into the web browser?

Your other questions are leading away from the subject at hand.  Let's try to stick with one topic at a time.  You don't want to delete those directories.  Especially the /media directory.  It is there for a purpose.  So as I say let's just stick to the task at hand and that is mounting your drives at boot time.

---

### Post by agregal on 2006-03-28
As for cat etc/fstab  I get got the following:

proc                /proc        proc         defaults      0          0
/dev/hda1        /windows   ntfs         nls=utf8,unmask=0222     0           0
/dev/hda5       /fat_files    vfat         iocharset=utf8,unmask-000     0        0
/dev/hda3       /               ext3         defaults,errors=remount-ro    0        1
/dev/hda6        none         sway        sw             0          0
/dev/hdc    /media/cdrom0   udf,iso9660 user, noauto    0         0

---

### Post by Mustard on 2006-03-28
Hehehe..ok..now your being too efficient for me. :)

Well done.

Let me look this over for a minute.

-edit-

Ok , see the problem now..your making typing errors when you enter the commands.

---

### Post by agregal on 2006-03-28
Well I have read what people said, that's why there are different versions of what I have tried.  Depending upon who writes what, not everything is exactly the same.  

I don't need help with cutting and pasting, let me put in another way, I'm worknig on a Mac that is connected to the Internet, the laptop that I'm working on with Ubuntu isn't connected nor can it be.  So there is no way that I know of to give you the information without retyping it.  I'm doing the best with what I have to work with.

I have relied to each of your requests for the output that I get.  They are listed in the posts.

---

### Post by Mustard on 2006-03-28
This is what you have...

```
proc /proc proc defaults 0 0
/dev/hda1 /windows ntfs nls=utf8,unmask=0222 0 0
/dev/hda5 /fat_files vfat iocharset=utf8,unmask-000 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none sway sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user, noauto 0 0
```

This is what it should be...

```
proc /proc proc defaults 0 0
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /fat_files vfat iocharset=utf8,umask=000 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user, noauto 0 0
```

You are typing 'unmask' instead of 'umask' and you used a '-' instead of an '=' sign on the line referring to the vfat drive.

---

### Post by agregal on 2006-03-28
Ok - What should be the first thing that I do to correct the problem?  Anything you want me to do I'll do.

---

### Post by Mustard on 2006-03-28
[QUOTE=agregal]Well I have read what people said, that's why there are different versions of what I have tried.  Depending upon who writes what, not everything is exactly the same.  

I don't need help with cutting and pasting, let me put in another way, I'm worknig on a Mac that is connected to the Internet, the laptop that I'm working on with Ubuntu isn't connected nor can it be.  So there is no way that I know of to give you the information without retyping it.  I'm doing the best with what I have to work with.

I have relied to each of your requests for the output that I get.  They are listed in the posts.[/QUOTE]

Ok, thats fair enough.  It would have been helpful to know that before hand. :)

---

### Post by Mustard on 2006-03-28
[QUOTE=agregal]Ok - What should be the first thing that I do to correct the problem?  Anything you want me to do I'll do.[/QUOTE]

Edit the fstab file and correct the errors.  Go over your edits carefully and confirm you have entered exactly what is on the page you are reading.

When you have finished editing, save the file and do this

Unmount both drives using the 'umount' command (note: its not **unmount**, its umount)

```
sudo umount /windows

#and then

sudo umount /fat_files

#these two commands will unmount the drives.
#Be careful to type 'umount' not 'unmount'
#Its a common error that people make
```

Then mount all entries in fstab again with this command...

```
sudo mount -a
```

Come back here with any error messages you get, if any.

These are the lines you need to edit and correct, written out the way they should be (assuming these errors are not just typos you are making while copying from your other machine)..

```
/dev/hda1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /fat_files vfat iocharset=utf8,umask=000 0 0
/dev/hda6 none swap sw 0 0
```

-edit-

Doh..I'm making typos now.. make sure you read my latest corrected version.

---

### Post by agregal on 2006-03-28
Ok - You were right there were typos. I originally entered 'unmask' instead of 'umask'.  I corrected the entries with what you told me. I rebooted the system but they drives are still not on my desktop.

When I go into Filesystem --> fat_files there is nothing in that folder.  However, when I go from Filesystem --> media both hda1 and hda5 are there but both are empty.

---

### Post by Mustard on 2006-03-28
[QUOTE=agregal]Ok - You were right there were typos. I originally entered 'unmask' instead of 'umask'.  I corrected the entries with what you told me. I rebooted the system but they drives are still not on my desktop.

When I go into Filesystem --> fat_files there is nothing in that folder.  However, when I go from Filesystem --> media both hda1 and hda5 are there but both are empty.[/QUOTE]

Ok, firstly the mount points would need to be in the /media folder for them to appear on desktop.  So your current fstab is using the mountpoints of /windows and /fat_files, which precludes this from happening.  To have them appear on desktop, you would need to use the mountpoints of /media/hda1 and /media/hda5.

This is what it should look like if you did that..

```
proc /proc proc defaults 0 0
/dev/hda1 /media/hda1 ntfs nls=utf8,umask=0222 0 0
/dev/hda5 /media/hda5 vfat iocharset=utf8,umask=000 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

```

Note in the above, the only changes I have made are the names of the two mount points /media/hda1 and /media/hda5.  I assume from what you have written above that those folders exist in the /media folder. I also removed a space between the comma and 'noauto' on the line for the cdrom.  I hadn't noticed that earlier on. Again its hard to do this when I have no idea what errors are typos as you translate what you see on one computer to the other computer.

Another question, is there anything on your vfat partition at the moment?  If there is nothing on it, then there will be nothing to see when you go there.  If there is and you have browsed to the /fat_files and found it empty then  I would have to assume there is a problem with mounting of the that partition still.  You didn't mention whether you browsed to the /windows folder and found anything, so I don't know whether that's mounted correctly or not.

I have some questions also.

1. Did you use the **umount** command to unmount the partitions and then remount them with sudo mount -a, as per instructions in a previous post?  

1a. If you did, did you see error messages and what were those error messages?

Try making the changes I have written above, then do this..

```

#Unmount both partitions. 
#Read what error messages (if any) are returned 
#when you do this and remember to tell me

sudo umount /windows
sudo umount /fat_files

#then mount all partitions in the fstab file
sudo mount -a
```

This should remount the partitions on the new mount points and return errors if there are any problems, ie some typos in the line, the wrong filesystem selected, or a corrupted partition.   If you don't see errors then it should be working.  Sometimes it does take a reboot for things to show up on desktop, but the main thing is to just get them mounted on the mount points that you want them on.

The error messages are really the vital clues to what is happening so if you can tell me what errors you are seeing I can have a better idea of what is going on.

---

### Post by agregal on 2006-03-29
Ok- finally, I'm so glad they actually mounted. No error messages at all.  Can I assume then that after rebooting they should remain mounted?

I really do appreciate you taking the time to help me out.  I do hate bothering people on such simple tasks.  Do you know a good tutorial that I should look at, something that explains all these commands such as 'sudo' 'gedit' etc.
Then now how do I go about deleteing the extra folders like /fat_files?

One last thing, where should I look on this site for help listening to my mp3 files, since ubuntu doesn't play mp3 by default?

---

### Post by meborc on 2006-03-29
for all restricted formats (mp3 etc) [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

wiki is there to help! ;)

Also check the two links in my sig... TheGuide is the one you will find most helpful

---

### Post by Mustard on 2006-03-29
[QUOTE=agregal]Ok- finally, I'm so glad they actually mounted. No error messages at all.  Can I assume then that after rebooting they should remain mounted?

I really do appreciate you taking the time to help me out.  I do hate bothering people on such simple tasks.  Do you know a good tutorial that I should look at, something that explains all these commands such as 'sudo' 'gedit' etc.
Then now how do I go about deleteing the extra folders like /fat_files?

One last thing, where should I look on this site for help listening to my mp3 files, since ubuntu doesn't play mp3 by default?[/QUOTE]

There are a couple of options for removing directories.  When removing anything, I would advise caution too, as quite often in linux there is no, 'Are you sure you want to do this?' warning message when you tell the system to delete something.  When you type in the command to remove, it will do so permanently and irrecoverably.

A simple method to using the graphical interface is to type into console this command below, which will give you 'root privileges' in your nautilus file browser.

```
gksudo nautilus

#this will bring up a graphical password dialog
#after entering your password you will the ability
#to edit files/folders in the file browser with
#administration privileges
```

The command line methods are below.  Always be cautious when using them.  There are options for making them interactive (asking for confirmation each time a file is going to be deleted) which are explained the manual for each command (more on that at the end)

1.  the rmdir command is the remove **empty** directory command. This command will warn you if the directory is not empty.

2.  the rm command is the remove files and directory command. This command will not explicitly remove empty directories by default, but can be made to do so with the right options.

An example of the use of these commands are below.  Both example use the 'sudo' command, to access the file system with administrator privileges, because these folders are outside the user space ie the /home/username folder is the user space.

```
#To remove the /fat_files directory

sudo rmdir /fat_files

#To remove the /windows directory

sudo rmdir /windows
```

Manuals for nearly all the common terminal commands can be accessed from the terminal itself.  For example..

```
#To read the manual for rmdir
man rmdir

#To read the manual for rm
man rm

```

To exit the manuals, press the 'q' key.

A couple of links that might help with the explanation of how linux uses its filesystem are below..

[http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT](http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT)
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

---

### Post by agregal on 2006-03-30
[QUOTE=Mustard]There are a couple of options for removing directories.  When removing anything, I would advise caution too, as quite often in linux there is no, 'Are you sure you want to do this?' warning message when you tell the system to delete something.  When you type in the command to remove, it will do so permanently and irrecoverably.

A simple method to using the graphical interface is to type into console this command below, which will give you 'root privileges' in your nautilus file browser.

```
gksudo nautilus

#this will bring up a graphical password dialog
#after entering your password you will the ability
#to edit files/folders in the file browser with
#administration privileges
```

The command line methods are below.  Always be cautious when using them.  There are options for making them interactive (asking for confirmation each time a file is going to be deleted) which are explained the manual for each command (more on that at the end)

1.  the rmdir command is the remove **empty** directory command. This command will warn you if the directory is not empty.

2.  the rm command is the remove files and directory command. This command will not explicitly remove empty directories by default, but can be made to do so with the right options.

An example of the use of these commands are below.  Both example use the 'sudo' command, to access the file system with administrator privileges, because these folders are outside the user space ie the /home/username folder is the user space.

```
#To remove the /fat_files directory

sudo rmdir /fat_files

#To remove the /windows directory

sudo rmdir /windows
```

Manuals for nearly all the common terminal commands can be accessed from the terminal itself.  For example..

```
#To read the manual for rmdir
man rmdir

#To read the manual for rm
man rm

```

To exit the manuals, press the 'q' key.

A couple of links that might help with the explanation of how linux uses its filesystem are below..

[http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT](http://www.pathname.com/fhs/pub/fhs-2.3.html#MEDIAMOUNTPOINT)
[http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)[/QUOTE]
When I used the gksudo nautilus command, I got the following error:

(nautilus:8150): GnomeUI - Warning **: Wile connecting to session manager:
Authentication Rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed.

What does this mean?

---

### Post by Mustard on 2006-03-30
[QUOTE=agregal]When I used the gksudo nautilus command, I got the following error:

(nautilus:8150): GnomeUI - Warning **: Wile connecting to session manager:
Authentication Rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed.

What does this mean?[/QUOTE]

The same error appears on my installation.  I assume it appears on everyone's installation when they do gksudo nautilus. The window still opens up though, on mine at least and I can edit with root privileges.

I assume it is a superfluous error message that is more about the operating system complaining to itself than complaining to the user.  You get used to these types of error messages after a while.  The main thing is it works. :)

---

