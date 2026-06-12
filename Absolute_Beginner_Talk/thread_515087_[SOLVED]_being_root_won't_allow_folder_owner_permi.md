---
title: "[SOLVED] being root won't allow folder owner permission change!?"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by snuffy on 2007-08-01
i have some folders that mysteriously have had their folder owner changed to root, even though i rarely use root.

i opened the relevant folders as root, and right clicked>properties. when i tried to change the owner to my normal user, it said "The owner could not be changed." 

why is it doing this, and how do i change my folders back to my normal user owner permissions?

thanks

tim.

---

### Post by asmoore82 on 2007-08-01
what folders and where?

---

### Post by Inxsible on 2007-08-01
I am more a proponent of the Command Line, so I shall give you the command to change ownership

```
sudo chown -R <your username>:<your group> <path to the folders>
```-R will recursively give you ownership of the folders within those folders. Remove -R if you dont want to do that.

So assuming your username to be tim

```
sudo chown -R tim:tim </path to folder>
```

---

### Post by snuffy on 2007-08-01
i did the following:

```
snuffy@snuffy-desktop:~$ sudo chown snuffy:snuffy "/media/sdb1/snuffys Documents/untitled folder/Albums"
```

and got the following:

```
chown: changing ownership of `/media/sdb1/snuffys Documents/untitled folder/Albums': Operation not permitted
```

i'm probably being stupid, but i haven't a clue. 

any help is much appreciated.

---

### Post by milosz.galazka on 2007-08-01
hello,

What filesystem do you use at sdb1?

---

### Post by Ek0nomik on 2007-08-01
Can you post the output of:

```
sudo fdisk -l
```

```
sudo mount
```

```
cat etc/fstab
```

**Inxsible**:  From his original post he stated that changing the permissiong as root wasn't working.  Whether he does it graphically or via terminal is irrelevant.

---

### Post by Inxsible on 2007-08-01
> **snuffy said:**
> i did the following:

```
snuffy@snuffy-desktop:~$ sudo chown snuffy:snuffy "/media/sdb1/snuffys Documents/untitled folder/Albums"
```and got the following:

```
chown: changing ownership of `/media/sdb1/snuffys Documents/untitled folder/Albums': Operation not permitted
```i'm probably being stupid, but i haven't a clue. 

any help is much appreciated.
Do you have a dual boot?
if so, Windows probably has a lock on the drive. Log into Windows and safely shutdown and then try again. This happens when, Windows for some reason didnt shut down properly

---

### Post by univremonster on 2007-08-01
I had a similar problem (though not a Windows lock) on a USB drive.  My solution, while rather unelegant, went something like this.

*as super-user, unmount the drive using rmdir
*re-mount the drive
*chmod
*chown

Worked like a charm from then on out.  For some reason using only the last two commands in there didn't work.  

Alternatively, if you feel like you know how to, which I don't but it's a slick way of doing things faster, try this

cd /etc
pico fstab

Find the drive you're having problems with and edit the permissions from there

---

### Post by snuffy on 2007-08-01
It's NTFS on that drive. yes, it's dual boot to XP.  i have read/write enabled via ntfs-3g.

sounds like windows could have a lock on the drive.  'my music'  'my pictures' and a couple of other random folders are also locked.

i have rebooted into windows and shutdown again. but the folders are still locked.

tim.

---

### Post by asmoore82 on 2007-08-01
NTFS doesn't store UNIX filesystem permissions;
is there some ntfs3g MAGIC that i'm missing?

---

### Post by snuffy on 2007-08-01
erm...you've lost me. i'm a newbie. i just read a post and installed ntfs-3g ages ago. read/write/everything worked fine until recently.

any ideas?

---

### Post by Ek0nomik on 2007-08-01
> **asmoore82 said:**
> NTFS doesn't store UNIX filesystem permissions;
is there some ntfs3g MAGIC that i'm missing?

Are you trying to help him or do you have a question yourself?  If you are trying to help, you should provide him with documentation or write something so he understands what to do.



**snuffy**:  Here are some links that you will find useful for getting write/read ability to NTFS filesystems:

[https://wiki.ubuntu.com/ntfs-3g](https://wiki.ubuntu.com/ntfs-3g)

[http://doc.gwos.org/index.php/NTFS-3g](http://doc.gwos.org/index.php/NTFS-3g)

[http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/](http://ubuntuos.wordpress.com/2006/08/02/howto-write-to-windows-ntfs-drive-from-ubuntu-ntfs-3g/)

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Linux systems can't fully use the NTFS file system out of the box, but using NTFS-3G you can get the support so you can take over your NTFS hard drive.

---

### Post by snuffy on 2007-08-01
Ek0nomik, i think you misunderstand me. maybe i should have been clearer. 

read/write on my NTFS is fine.  the problem is with changing ownership permissions. even as root i seem to be prevented from altering folder ownership to my username, which mysteriously (it seems something to do with XP locking them? - dual boot) for some reason, some of the folders/files have changed ownership from my username to root, and they cannot be changed back... even when trying as root.  i therefore cannot modify/move/delete these folders...which as you can imagine, is bloody annoying!

any advice would be appreciated.

tim.

---

### Post by Ek0nomik on 2007-08-01
I would unmount the partition, than change the permissions of the folder in /media by doing something like:  'sudo chown username:username /media/yourmountpoint'

Then, mount the partition again.

---

### Post by snuffy on 2007-08-02
i tried unmounting the hard drive using:       sudo umount /dev/sdb1
then       sudo chown snuffy:snuffy /media/sdb1
then       sudo mount /dev/sdb1

but its still exactly the same. :-(

---

### Post by asmoore82 on 2007-08-02
Ahh I see ...

NTFS filesystems cannot store UNIX filesystem ownership/permissions.
the workaround for this is that the system gives ownership of all files on
the filesystem to the person who mounted them...

so try unmounting with root access and mounting them as just plain you

```
~ $ sudo umount /dev/sdb1
~ $ mount /dev/sdb1
```

if that doesn't work; post the contents of your "/etc/fstab" file

---

### Post by Ek0nomik on 2007-08-02
> **asmoore82 said:**
> Ahh I see ...

NTFS filesystems cannot store UNIX filesystem ownership/permissions.
the workaround for this is that the system gives ownership of all files on
the filesystem to the person who mounted them...

so try unmounting with root access and mounting them as just plain you

```
~ $ sudo umount /dev/sdb1
~ $ mount /dev/sdb1
```

if that doesn't work; post the contents of your "/etc/fstab" file

That is actually what I meant to convay in my posting.  I meant for him to mount it without 'sudo'.  Thanks for clearing it up.  :)

---

### Post by snuffy on 2007-08-03
> **asmoore82 said:**
> Ahh I see ...

so try unmounting with root access and mounting them as just plain you

```
~ $ sudo umount /dev/sdb1
~ $ mount /dev/sdb1
```

if that doesn't work; post the contents of your "/etc/fstab" file

ahhh... i see. i'll try mounting without the sudo then. i'm away for the weekend, so won't be able to try this til monday. i'll let you know whether it worked.

i'm learning all the time! thanks.

---

### Post by snuffy on 2007-08-04
```
snuffy@snuffy-desktop:~$ sudo umount /dev/sdb1
snuffy@snuffy-desktop:~$ mount /dev/sdb1
mount: only root can mount /dev/disk/by-uuid/42F0-02BF on /media/sdb1
snuffy@snuffy-desktop:~$ 
```

brick wall. :-(

---

### Post by snuffy on 2007-08-08
anyone any ideas?

---

### Post by snuffy on 2007-08-10
i figured out a way to fix it. 

i went into windows, created new folders for the ones that were locked, and moved their contents into these new folders. 

it seems to have worked.  still no idea why it happened or why i couldn't fix this seemingly simple problem from within ubuntu.

thanks to all those that gave my help along the way.

thanks.

---

### Post by ryanlhjess on 2008-01-28
sudo chown -R tim:tim </path to folder>

thanks

---

