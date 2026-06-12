---
title: "Two home folders?"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by editrix on 2006-06-24
I seem to have two different places where my (not root's) /home files are stored.

I had Kubuntu Breezy installed on a computer I hadn't actually used. But I did have a separate home partition. It was mainly a test machine, so other than transferring a few files to a shared FAT32 partition while awaiting Dapper, I didn't play with it much.

All I've done so far is installed Ubuntu Dapper from a burned CD, got my modem working, and then, via aptitude, installed the kubuntu-desktop. Now, in Nautilus under Places, I have both a <myusername> folder and a /home disk icon.

The <myusername> folder contains Desktop and Examples (from the Dapper install) as well as hidden files like .metacity and .gconf. 

The /home disk contains a lost+found folder and a <myusername> folder. And the <myusername> folder contains hidden files like .mcop and .kde, but no Examples.

Both <myusername> folders have things like .bash_history and .ICEauthority--but they're different sizes.

I think I'm in trouble.

Needless to say, I wanted one /home/<myusername> directory, on a separate home partition, and I want *all* the files that normally go there to go there automatically. So where did I go wrong? And is there a way to fix it?

---

### Post by Kilz on 2006-06-24
[QUOTE=editrix]I seem to have two different places where my (not root's) /home files are stored.

I had Kubuntu Breezy installed on a computer I hadn't actually used. But I did have a separate home partition. It was mainly a test machine, so other than transferring a few files to a shared FAT32 partition while awaiting Dapper, I didn't play with it much.

All I've done so far is installed Ubuntu Dapper from a burned CD, got my modem working, and then, via aptitude, installed the kubuntu-desktop. Now, in Nautilus under Places, I have both a <myusername> folder and a /home disk icon.

The <myusername> folder contains Desktop and Examples (from the Dapper install) as well as hidden files like .metacity and .gconf. 

The /home disk contains a lost+found folder and a <myusername> folder. And the <myusername> folder contains hidden files like .mcop and .kde, but no Examples.

Both <myusername> folders have things like .bash_history and .ICEauthority--but they're different sizes.

I think I'm in trouble.

Needless to say, I wanted one /home/<myusername> directory, on a separate home partition, and I want *all* the files that normally go there to go there automatically. So where did I go wrong? And is there a way to fix it?[/QUOTE]No, you are not in trouble. The home disk is from the previous version where you had the home folder on a partition. The new home folder was setup when you upgraded. It now gives you a chance to move anything you had in your old home folder to the new one. Then you can unmount it in /etc/fstab and delete the partition.

---

### Post by digby on 2006-06-24
Can you post the contents of /etc/fstab?  If you don't know how, open a terminal and type:```
cat /etc/fstab
```Paste the output from that here, and we can tell you a little more from that...

Another thing you could try:  open up both windows in Nautilus.  Just under the 'back' button is a button w/ a black arrow pointing left.  Clicking that will expand to show you the full path to where that folder is.  Your actual home folder will be /home/username.  The other should point somewhere else.

---

### Post by editrix on 2006-06-25
Oh my, thanks for being so quick! I'm on dialup, so I can't get on the forum as often as I'd like.

[QUOTE=digby]Can you post the contents of /etc/fstab?[/QUOTE]

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda7       /media/hda7     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/fd0        /media/floppy0  auto,umsdos,vfat,ext2    rw,user,noauto  0       0


Sorry if it looks sloppy.  The /home partition is hda7.

[QUOTE=digby]Another thing you could try:  open up both windows in Nautilus.  Just under the 'back' button is a button w/ a black arrow pointing left.  Clicking that will expand to show you the full path to where that folder is.  Your actual home folder will be /home/username.  The other should point somewhere else.[/QUOTE]

Right. It's media/home.

[QUOTE=Kilz]No, you are not in trouble. The home disk is from the previous version where you had the home folder on a partition. The new home folder was setup when you upgraded. It now gives you a chance to move anything you had in your old home folder to the new one. Then you can unmount it in /etc/fstab and delete the partition.[/QUOTE]

Hmm. Maybe I misunderstood the purpose of the home partition? I thought it was more than just a storage space for backup. I thought it was where all home files would be, so you didn't have to think about backing them up before a new install.

---

### Post by steve.horsley on 2006-06-25
First you need to understand how Linux mounts other partitions. Instead of making them appear as different drive letters (C:, D:...) as DOS does, Unix and Linux make the partition appear as a subdirectory in the one-and-only file tree.

There is a catch in this scheme - instead of the partition contents appearing as a 
previously nonexistent directory, the contents of the drive partition **replace** and **existing** directory. The original directory contents become inaccessible until the drive/partition that replaced them is un-mounted again.

So my understanding is that wat was your /home drive previously is now being mounted in the location /media/hda7 instead of at /home as it was in Breezy. Now you have a tricky issue in that if you mount /dev/hda7 at /home instead of /media/hda7, all your new stuff in your home folder (examples frinstance) will disappear. I suggest that you do this, which should restore that separate /home partition to the proper place at /home:

Move anything you want to keep from home/myusername to /tmp (e.g. examples directory).

Backup /etc/fstab:
**sudo cp /etc/fstab /etc/fstab-backup**

Edit /etc/fstab (**gksudo /etc/fstab**) and change this line:
**/dev/hda7 /media/hda7 ext3 defaults 0 2**
to this:
**/dev/hda7 /home ext3 defaults 0 2**

reboot

Move the stuff you wanted to keep from /tmp back into your home folder

Hope this helps

---

### Post by editrix on 2006-06-25
[QUOTE=steve.horsley]So my understanding is that wat was your /home drive previously is now being mounted in the location /media/hda7 instead of at /home as it was in Breezy.[/QUOTE]

This makes sense (sort of) as, when I installed Dapper, it told me I had no root partition (mount point /) although, obviously, I had to have had one in Breezy--it was now labelled hda2.

[QUOTE=steve.horsley]Move anything you want to keep from home/myusername to /tmp (e.g. examples directory).[/QUOTE]

I'm getting "Invalid URI" messages. Presumably, I want to keep the Gnome config files--all the hidden files? And that's what's giving me the messages.

[QUOTE=steve.horsley]Backup /etc/fstab: ...[/QUOTE]

Okay, this makes sense. Rename hda7 home.

Well, I haven't done it yet, as I don't know what I should keep. Will all those Gnome files be regenerated?

My other option is to just reinstall--I don't have anything important on there yet. But if I do reinstall, how do I make sure that the /home partition is what gets used as home? (this may also help others in my boat)

---

### Post by catlett on 2006-06-25
I didn't read the thread so I don't know what has been mentioned. I just wanted to post the link to Aysiu's guide on moving home. I would just follow the guide and put home wherever you want it. [http://psychocats.net/ubuntu/separatehome.html](http://psychocats.net/ubuntu/separatehome.html)

P.S. Right now it appears you have a home folder on root's partition and a partition labeled home.

---

### Post by steve.horsley on 2006-06-25
[QUOTE=editrix]I'm getting "Invalid URI" messages. Presumably, I want to keep the Gnome config files--all the hidden files? And that's what's giving me the messages.
[/QUOTE]
I have never seen that message, and don't know where it's coming from. 

The gnome config files are expendable - they will get recreated if they don't exist. But when you start using your old home directory, you will pick up all the original gnome settings anyway.


> 
Okay, this makes sense. Rename hda7 home.

hda7 is the name of the partition - partition 7 on the first drive. That does not change. You are changing where you mount it in your file tree.
> 
Well, I haven't done it yet, as I don't know what I should keep. Will all those Gnome files be regenerated?
As I said, they get regenerated if needed, but your original home will already have a set with your original settings.> 
My other option is to just reinstall--I don't have anything important on there yet. But if I do reinstall, how do I make sure that the /home partition is what gets used as home? (this may also help others in my boat)
Yes, but the change I suggested should achieve the same thing much quicker.

P.S.
You never need to worry about losing the Gnome settings in .gnome, .gnome2 and wherever else they hide them. Sometimes you have to delete them all to remove a corrupt entry. And they all recreate anyway - when you add a new user you don't go out of your way to create a default set of Gnome files - gnome creates them for itself the first time you run gnome.

---

### Post by editrix on 2006-06-25
[QUOTE=catlett]I didn't read the thread so I don't know what has been mentioned. I just wanted to post the link to Aysiu's guide on moving home. I would just follow the guide and put home wherever you want it. [http://psychocats.net/ubuntu/separatehome.html](http://psychocats.net/ubuntu/separatehome.html)

P.S. Right now it appears you have a home folder on root's partition and a partition labeled home.[/QUOTE]

I followed his old page for Breezy when I installed that. What I (and perhaps others) need now is, what do you do when you've already got the home partition and are installing Dapper. But I think we're getting somewhere now.

Hard to believe I'm the only one who screwed this up :(

---

### Post by digby on 2006-06-25
[quote=editrix]I followed his old page for Breezy when I installed that. What I (and perhaps others) need now is, what do you do when you've already got the home partition and are installing Dapper. But I think we're getting somewhere now.

Hard to believe I'm the only one who screwed this up :([/quote]
Steve's instructions are fine, but I just thought I'd tell you how to avoid this should you reinstall/upgrade/something at somepoint in the future.  When installing from the cd and at the partitioning section, if you manually edit the partition table and have it mount your old home partition as home (and make sure you don't format it, of course), you won't have this kind of problem again.

---

### Post by T700 on 2006-06-25
deleted

---

### Post by editrix on 2006-06-26
[QUOTE=steve.horsley]First you need to understand how Linux mounts other partitions....

Move anything you want to keep from home/myusername to /tmp (e.g. examples directory).

Backup /etc/fstab:
**sudo cp /etc/fstab /etc/fstab-backup**

Edit /etc/fstab (**gksudo /etc/fstab**) and change this line:
**/dev/hda7 /media/hda7 ext3 defaults 0 2**
to this:
**/dev/hda7 /home ext3 defaults 0 2**

reboot

Move the stuff you wanted to keep from /tmp back into your home folder

Hope this helps[/QUOTE]

Oh my Steve, it helps enormously, thanks. I was really wondering why /tmp, except I couldn't seem to move it anywhere else, so ...

But now, I'm not sure it worked as it should.

First off, I didn't have to move the /Desktop and Examples back--they're just there. Second, the Disks utility is telling me that partition 7 is inaccessible. Except it isn't. I can write to it just fine--at least, I copy/pasted a file into the directory, then deleted it, and it didn't complain. So I'm not sure I did it right.

---

