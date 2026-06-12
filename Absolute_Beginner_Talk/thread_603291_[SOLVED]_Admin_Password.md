---
title: "[SOLVED] Admin Password"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by itix on 2007-11-05
Is there any way you can change options somewhere so you won't have to type the administrative password every time you're trying to move the mouse pointer 3 inches to the left??

---

### Post by drowner on 2007-11-05
Of course there is.

But, the sudo system is there for your own protection

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Why do you need to enter the password so frequently?

---

### Post by linaxe on 2007-11-05
can java rune on ubuntu?

---

### Post by dfreer on 2007-11-05
What are you talking about here, the screensaver lock? It's not the administrative password, if that's what you are referring to, it's the user's password. And you can disable it in gnome by going to **System > Preferences > Screensaver**, then uncheck the "*Lock screen when screensaver is active"*

If that's not what you are talking about, please be a bit more descriptive.

> **linaxe said:**
> can java rune on ubuntu?

Yes, it can, but what does that have to do with this thread?

---

### Post by itix on 2007-11-05
I have three main partitions. One 11 gig for Ubuntu, one 10 gig for windows and one ~60 gig for files (NTFS). If I want to listen to my music (which is on the 60) I must first mount that one (requires password). I often find things that I want to try => install through Package Manager (requires password). Update Manager, system preferences (like everytime I try to fix that damn workspace cube of mine because of that non-existant pic at the bottom of it).

---

### Post by itix on 2007-11-05
I don't have my screen lock activated so no... se my answer to drowners post. I mean that password that is required for almost any application here. Package Manager, Update Manager, Mounting Disks etc.

Nice avatar BTW. Cecil \o/

---

### Post by SunnyRabbiera on 2007-11-05
yeh your setup has a lot to do with this, especially if its a ntfs filesystem.
maybe you should backup that partition for files and reformat it as something both linux and windows  can understand.
You could try to make it a fat32 partition or something, both windows and linux can read it and access it.
if ext3 was readable by windows you could use that but sadly there is an issue with that on the windows side.

and as said before the master password is there to protect you, it makes linux more secure.
trust me if you were using vista it would be worse then linux.
Of course there is a way to turn off the master password and allow anyone to use the administration apps but thats what windows does to make it less secure.
I know its an annoyance but its for your own good.

---

### Post by FuturePilot on 2007-11-05
That's normal for you to have to enter the password for anything that will change the root file system or any type of administrative task. As for your partition, I'm sure that you could add that to fstab so that it will always be mounted.

> **SunnyRabbiera said:**
> yeh your setup has a lot to do with this, especially if its a ntfs filesystem.
maybe you should backup that partition for files and reformat it as something both linux and windows  can understand.
You could try to make it a fat32 partition or something, both windows and linux can read it and access it.
if ext3 was readable by windows you could use that but sadly there is an issue with that on the windows side.
Gutsy can now read and write to NTFS by default. I actually wouldn't recommend FAT32. It's a very old file system and has many flaws. NTFS would be better than FAT32. Of course EXT3 would be ideal, but that's not always an option.

---

### Post by drowner on 2007-11-05
Its actually a good idea to have to enter your password before programs are installed. Same for changing system settings. 

Lets tackle the playing your music first.

What you want to do is mount that drive so that its always mounted at login, and you have permission to read and write to it.

Could you open a terminal and show us the output of 

sudo fdisk -l

and

cat /etc/fstab

The first command will show us the names of your partitions, and the second one is a file that stores all the drives you have automatically mounted. We can edit the second file so that it automatically mounts the partition with music, and that you (or everyone, however you prefer) has access to it.

---

### Post by itix on 2007-11-05
Yeah I know, But then again, there's the problem with larger files like for example DVD-imgs, games and such. Fat32 is restricted to <4gig files...

---

### Post by SunnyRabbiera on 2007-11-05
> **itix said:**
> Yeah I know, But then again, there's the problem with larger files like for example DVD-imgs, games and such. Fat32 is restricted to <4gig files...

I fully understand...
there is no real solution for you unless you just restructure your whole system and that will be a major pain, especially if you dont have a windows disk around.

---

### Post by FuturePilot on 2007-11-05
This really isn't a huge problem. All you need to do is add that partition to fstab and it will always be mounted. Problem is, I'm not too good with fstab. I'm sure someone else will know.

---

### Post by itix on 2007-11-05
fdisk list:


Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2186    17559013+   7  HPFS/NTFS
/dev/sda2            2187        8455    50355742+   7  HPFS/NTFS
/dev/sda3   *        8456        9669     9751455   83  Linux
/dev/sda4            9670        9729      481950    5  Extended
/dev/sda5            9670        9729      481918+  82  Linux swap / Solaris

fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=4999d3dc-b794-498a-bcde-b2265b05c401 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=aae8d507-4212-49bf-9b27-699a612864f5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by The Tronyx on 2007-11-05
Are you using gutsy? To mount your NTFS partition on boot...

In a terminal start with:
> 
sudo mkdir /media/NTFS (or mkdir whatever you want the NTFS partition to be named)


Then
> 
sudo gedit /etc/fstab


This will pull up your fstab.  Add the following line to the bottom
> 
/dev/hda1 /media/NTFS ntfs-3g defaults,force 0 0


**Note that where it says /dev/hda1 you should rename that to the mount point for your partition.  

I also add the force line in there in the event that you get a message saying "Volume is scheduled for check. Please boot into Windows TWICE, or use the 'force' mount option."  If I had to guess, the partition that stores all your media you mentioned is sda2 so you would want to:

> 
/dev/sda2 /media/NTFS ntfs-3g defaults,force 0 0


---

### Post by itix on 2007-11-05
Should I like, back the fstab up, or anything first? I'm kinda tired from reinstalling Ubuntu for having destroyed it over and over again.

---

### Post by The Tronyx on 2007-11-05
> **itix said:**
> Should I like, back the fstab up, or anything first? I'm kinda tired from reinstalling Ubuntu for having destroyed it over and over again.

Backing up is always a good idea, especially if you are hand editing.  Worst case scenario though you only need to 

> 
sudo gedit /etc/fstab

And remove the line you added.  Note that I say worst case scenario as in it typically wouldn't cause much problem if it didn't work but I don't want to be blamed for blowing up your machine.

Hey, it's linux, in the words of my good friend, if you break Ubuntu, you get to keep both pieces.:guitar:

If you want the easy fix in the event that fstab gets screwed up do this:

Copy fstab to your home directory
> 
sudo cp /etc/fstab /home/HomeDirectoryName

That will back it up for you

To replace it
> 
sudo cp -i /home/HomeDirectoryName/fstab /etc/fstab 


The -i switch isn't necessarily called for but I use it so that I KNOW i am overwriting what I want to rather than blindly copying a file to a typo'ed directory.

---

### Post by drowner on 2007-11-05
Always a good idea!
```

sudo cp /etc/fstab /etc/fstab_backup

```
will do that nicely

---

### Post by itix on 2007-11-05
Thanx to everybody. I'll try just that...

---

### Post by The Tronyx on 2007-11-05
> 
Thanx to everybody.  I'll try just that...


You're welcome! Keep us posted so we know if you need more assistance. :popcorn:

---

### Post by itix on 2007-11-05
Wohoo!! It worked.

Thanx a lot \,,/

---

### Post by The Tronyx on 2007-11-05
> **itix said:**
> Wohoo!! It worked.

Thanx a lot \,,/

Anytime  and glad to be of assistance =D

I do ask one very small thing, please mark this thread as [Solved]:biggrin:

---

### Post by itix on 2007-11-05
Done :p

Ah what a bliss to not have to mount my disks at startup anymore

---

### Post by dfreer on 2007-11-05
Eh, I go to sleep and miss everything. Glad you got your problem solved!

FFIV ftw!

---

### Post by aonegodman on 2007-12-13
Ok, ok, ok. For me the answer I found was simple.

Go into Terminal program.

Type in: sudo -i -u *username*

Hit Return.

I understand you now have 15 minutes to play ***god*** on la machina.

Thank you!

---

