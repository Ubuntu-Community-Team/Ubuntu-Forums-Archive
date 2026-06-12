---
title: "NTFS Configuration Tool - please help!"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by jolt_TWSR on 2007-06-17
Hi, I'm still pretty new to Ubuntu,  installed Feisty Fawn a couple of days ago and have been really liking it up to now. 

I have 2 hard disks;
1st disk has two partitions - My Ubuntu partition and a second partition which is an NTFS one  from when I had XP installed a while ago which has lots of my documents and backups etc.  

2nd disk, also NTFS has my entire music collection on it. 

I heard about a way to make NTFS disks readable using the NTFS configuration tool so thought I'd try it out - installed and ran it, clicked on the tick box for "Enable write support for internal device" and got a message something like [Pacguy did on another thread]("http://ubuntuforums.org/showthread.php?t=463759&highlight=ntfs+configuration") - 

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hdd1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
Boot Windows and shutdown it cleanly, or if you have a removable
device then click the 'Safely Remove Hardware' icon in the Windows
taskbar notification area before disconnecting it.

I don't currently have XP installed, I clicked okay or cancel (can't remember) just to clear the message and then found that my Desktop background had disappeared (probably nothing but a bit strange) and then when I tried to look at my Filesystem my 2 HD's had disappeared :(      When looking in the media directory I can still see two entries for hda2 and hdb1 but both are just completely empty folders. 

Have I lost all of my data? I've restarted but it's made no difference and I can't find anything for this particular problem anywhere, really hope someone can help!

Thanks in advance,
Chris

---

### Post by scrooge_74 on 2007-06-17
This is the [HOWTO]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+driver+install") you need

---

### Post by onero on 2007-06-17
A similar thing happened with the external hard drive of a friend of mine. Don't worry, you probably haven't lost your data, and you can still mount your partitions by force mounting them. Try this command:

```
sudo mount -t ntfs-3g /dev/hdb1 /media/mydrive -o force
```

Replace /dev/hdb1 with the path of your partition, and mydrive can be replaced with whatever name you want to mount your partitions to. If it complains that mydrive doesn't exist, create a new folder in the /media directory with the name of your mount point and force mount the partition again. To create a new directory in /media, type

```
sudo mkdir /media/mydrive
```

If you successfully mount your partitions, you can try to fix them by running ntfsfix. Install the ntfsprogs package. In the terminal, type

```
sudo apt-get install ntfsprogs
```

Of course, you can install via synaptic as well. Then run

```
ntfsfix /dev/hdb1
```

or whatever the path to your partition is.

Anyway, I'm not really sure about the other details, but if you're still having problems, try looking at this thread: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by jolt_TWSR on 2007-06-17
Hiya, thanks for the speedy replies! I've tried to run the command: 

> sudo mount -t ntfs-3g /dev/hdb1 /media/music -o force

but I just get the same message: 

> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/hdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

I don't have Windows installed so can't do the first option. I know I don't have the drives mounted yet but I tried to install the ntfsprogs package  with the command:

> sudo apt-get install ntfsprogs

but now get the following message and can't seem to clear it: 
 
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Apologies if I'm being fairly  dumb, but am kinda stumped as to what to do now ::confused::confused::confused:

---

### Post by onero on 2007-06-17
Do you have Synaptic or Add/Remove Programs open? Close it before running the command in the terminal (or alternatively, install the package through synaptic :))

---

### Post by jolt_TWSR on 2007-06-17
Ahh fantastic! Got both drives mounted now, thanks very much for your help :D

---

### Post by willdex on 2007-07-28
I'm trying to mount my portable Maxtor 200GB drive to **/media/maxtor**. I've already created the **/media/maxtor** directory. When I go to _System -> Preferences -> Hardware information_ -> go down to see my drive -> see _One Touch II_ -> click on **Advanced** tab -> I see that the *block.device*'s value is **/dev/sdb**. Does this mean that I'd have to run ```
sudo mount -t ntfs-3g /dev/sdb /media/maxtor -o force
``` for all this to work?

---

