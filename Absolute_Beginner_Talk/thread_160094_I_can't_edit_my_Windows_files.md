---
title: "I can't edit my Windows files"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by walterius on 2006-04-14
Ubuntu says my Windows files are read-only because I am not the owner. Of course I'm not the owner: they were created in Windows. Is there anything I can do? ](*,) 

E.g. I want to edit my Journal (Writer), my presentations (Impress) and my spreadsheets (Calc) in Ubuntu O.o as well as in Windows OO.o.

Thanks in advance,
Walterius

---

### Post by Derek Djons on 2006-04-14
If you're Windows partition is NTFS than it's true you cannot edit them. Since Microsoft holds patents on the Filesystem everything is Read Only. There are some (not legal) ways to go around... If I'm right one or more methods are described here on the forum.

---

### Post by sYs^ on 2006-04-14
For example: [http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)

But don't forget:

[COLOR="Red"][SIZE="4"]Ntfs writing support is still experimental! You should not enable it on production machines and/or volumes you don't have backups of. Proceed at your own risk![/SIZE][/COLOR]

---

### Post by hw-tph on 2006-04-14
It is certainly possible to compile the ntfs module with write capability. With recent kernels, this is even considered safe - it is not deemed experimental any longer. However, caution is always good and backups are always essential no matter what you do.

Another option is using [Captive NTFS](http://www.jankratochvil.net/project/captive/) which uses the Windows NTFS driver (ntfs.sys) to provide the read and write support.


Håkan

---

### Post by catlett on 2006-04-14
Are you invoking root priveleges when you call up the files? You have to be root to change anything not in your home folder. For example if you just entered gedit windows/journal you would just be a user and not root, and thertefore not be able to alter anything. To be root you have to invoke it by using "sudo" (superuser do. This is Ubuntu's way of a user becoming root without logging off as user, logging on as root and then logging out and on again). So to edit you would have to enter sudo gedit windows/journal and then it will ask for a pawssword. Enter your user password.
You can't just go to a file and double click like in windows. That wiull only work in the home folder. Anywhere else you have to call up the file with root priveleges. Hope this makes sense I have to go and wanted to add a bit about root because I don't think your talking about ntfs problems.

---

### Post by RRS on 2006-04-14
If you create a fat32 partition you can copy files into it from your windows partition while in Ubuntu then read and write from either operating system.

I've found this reasonably convenient and it's probably the safest method. 

Also, though the partitions are shown as owned by Root I've never had a problem doing this while logged in as User.

---

### Post by xenmax on 2006-04-14
RRS: See if this thread helps [http://www.ubuntuforums.org/showthread.php?t=144321&highlight=umask](http://www.ubuntuforums.org/showthread.php?t=144321&highlight=umask)

---

### Post by xenmax on 2006-04-14
Oops, wrong thread - ignore last post. Sorry about that.

---

### Post by RRS on 2006-04-14
[QUOTE=xenmax]Oops, wrong thread - ignore last post. Sorry about that.[/QUOTE]

Actually it may help, compared my fstab with the one shown and I'm missing a 0 after umount (3 instead of the 4 shown)

I'll edit this evening when I have more time, thanks.

Edit: oops, meant umask instead of umount.

---

### Post by xenmax on 2006-04-14
The mask is in octal - the first 0 indicates that i guess

---

### Post by Sutekh on 2006-04-14
[QUOTE=RRS]Actually it may help, compared my fstab with the one shown and I'm missing a 0 after umount (3 instead of the 4 shown)

I'll edit this evening when I have more time, thanks.

Edit: oops, meant umask instead of umount.[/QUOTE]
The umask sets the permissions, not the ownership.  If you would like to change the owner of the FAT partition mount, then you need to add the uid/gid flag to the fstab entry.

The uid/gid flag sets the ownership/group ownership of the partition to the user id given.  You can find out your user id and group id with the command```
id
```you will be returned something like this```
**user**@ubuntu:~$ id
uid=1000(**user**) gid=1000(**user**) 

```
All you need to do is change the fstab entry to look something like this
```
/dev/hda1   /media/windows   vfat   iocharset=utf8,**umask=000,uid=1000,gid=1000**   0   0
```
Now the user **user** owns the mount and the group ownership belongs to **user** using the options **uid=1000,gid=1000**.

The permissions are set to read/write/execute  for owner/group owner/everyone using the **umask=000** option


[quote=xenmax] 	The mask is in octal - the first 0 indicates that i guess[/quote]
That what I had previously thought, but after some experimentation found that it's not like that.

The umask could have 1,2,3,4 digits and still work.  It seems as though the umask works backwards in assigning permissions from everyone -> group owner -> owner.  If all the numbers are not specified it is assumed that working backwards they get full permissions.  So using one digit applies to everyone else and then assumes full permissions for the group owner and owner.

If you had a umask=3, for example, which would allow read only permissions for everyone, it will automatically give the owner and group owner full permissions.  Its as though umask=3 is the same as umask=003.   

In the same way, specifying a umask=33, which would give read only access to everyone and read only access to the group owner,  automatically gives full access to the owner.  So umask=33 is the same as umask=033.


Funnily enough specifying a umask=3333, still works and gives read only permissions to the owner, group owner and everyone else.

---

### Post by xenmax on 2006-04-14
[quote=Sutekh]
If you had a umask=3, for example, which would allow read only permissions for everyone, it will automatically give the owner and group owner full permissions.  Its as though umask=3 is the same as umask=003.   

In the same way, specifying a umask=33, which would give read only access to everyone and read only access to the group owner,  automatically gives full access to the owner.  So umask=33 is the same as umask=033.


Funnily enough specifying a umask=3333, still works and gives read only permissions to the owner, group owner and everyone else.[/quote]
Ok. I took your experiment one step further. You can have umask=33333 or umask=7333 and you still get same permission as 0333 - which is read-only for user,grp and everyone. 
So in effect, it ignores all digits except last 3 which matter - but not quite - it probably does a range check on entire string/number first i guess - none of digits can be anything but [0-7] - so umask=0888(obviously will not work) or umask=8333 or even umask=80333 dont work - mount gives an error and quits.

---

### Post by walterius on 2006-04-14
RRS,

<snip>
If you create a fat32 partition you can copy files into it from your windows partition while in Ubuntu then read and write from either operating system.

I've found this reasonably convenient and it's probably the safest method.

Also, though the partitions are shown as owned by Root I've never had a problem doing this while logged in as User.
</snip>

My understanding of what you said is: I create a FAT32 partition whilst in Ubuntu and then, whilst still in Ubuntu, copy Windows files into it. I can then edit them in Ubuntu and they will also be available in Windows.

1. I think I understand enough about copy (sudo cp) to copy the files.

2. How do I make the FAT32 partition?

I forgot to mention that all my Windows partitions are FAT32.

I also forgot to mention that my system is *not* dual boot. It is *multi* boot. See the partitions list below. I can boot to any of four Windows OS's plus Linux.

My Windows partitions are:
o Windows 2000 main system (I'm in that now)
o Windows ME
o two more Windows 2000 partitions for various testing purposes
o Windows ME, which I use for purposes not available in Windows 2000.
o My Documents (it has its own partition so all OS's can share the same logical My Documents)

o Plus the two normal Ubuntu Linux partitions.

Sorry for the windy post.

Walterius

---

### Post by Sutekh on 2006-04-14
[QUOTE=xenmax]Ok. I took your experiment one step further. [/QUOTE]
Good stuff.  I'm not sure why I stopped at 4.

[quote=walterius]
2. How do I make the FAT32 partition?[/quote]
You could use [GParted](http://gparted.sourceforge.net/).  You can install this from the Ubuntu repositories```
sudo apt-get install gparted
```Only use this options if you have multiple hard discs, as the disc must be unmounted to partition.

If you only have one hard disc you should consider the [GParted LiveCD (30MB)](http://gparted.sourceforge.net/livecd.php) or  [DiskDrake](http://ubuntuforums.org/showthread.php?t=114142).  

If your hard drives are already full, you will need to do some resizing and moving of partitions.  I use GParted quite often to delete/create partitions, but Ihaven't yet needed to do some resizing so I can't really offer and advice on that.   Check out the GParted web page for better documentation and some screenshots.

---

### Post by RRS on 2006-04-14
walterius

> I forgot to mention that all my Windows partitions are FAT32.

I also forgot to mention that my system is *not* dual boot. It is *multi* boot. See the partitions list below. I can boot to any of four Windows OS's plus Linux.

My Windows partitions are:
o Windows 2000 main system (I'm in that now)
o Windows ME
o two more Windows 2000 partitions for various testing purposes
o Windows ME, which I use for purposes not available in Windows 2000.
o My Documents (it has its own partition so all OS's can share the same logical My Documents)

o Plus the two normal Ubuntu Linux partitions.

Sorry, I had incorrectly assumed you were only dual booting with Windows XP which uses NTFS rather then fat32, which Linux is unable to write to.

In your case it would seem like your initial question of mounting with the correct permissions is more applicable and you should be able to use  your existing "My Documents" partition instead of creating a new one as I had suggested.

I've been away from the computer all day and have only briefly scanned the postings from Sutekh and xenmax but it would appear they have the answers to both our questions.

BTW, who is shown as the owner, root? If so then sudo should work for you to open and edit from terminal.

Sorry again for the sidetrack, I haven't owned a computer long enough to have any experience with 2000 or ME. Before XP I had only some forgotten knowledge of early DOS.

---

### Post by RRS on 2006-04-14
Sutekh

> The uid/gid flag sets the ownership/group ownership of the partition to the user id given. You can find out your user id and group id with the command
```
id
```

you will be returned something like this
```
user@ubuntu:~$ id uid=1000(user) gid=1000(user)

```

All you need to do is change the fstab entry to look something like this
```
/dev/hda1 /media/windows vfat iocharset=utf8,umask=000,uid=1000,gid=1000 0 0
```

Now the user user owns the mount and the group ownership belongs to user using the options uid=1000,gid=1000.


Worked like a charm, thanks :)
I also did the same edit to my XP partition so each shows me as the owner with read and execute permissions in both and write permission in the fat32.

This would appear to be a solution for walterius also, thanks again.

---

### Post by walterius on 2006-04-16
I want to thank everyone for their help. :KS  I am now happily editing my Windows (FAT32) files in Ubuntu. Many people pointed the way, but the thread below finished the job, finally giving me the breakthrough I needed:

[http://www.ubuntuforums.org/showthread.php?t=144321&highlight=umask](http://www.ubuntuforums.org/showthread.php?t=144321&highlight=umask)

Finally I can edit, delete, move, and copy--not just Windows files, but also Ubuntu files. This is the first time I have actually been able to DO anything in Ubuntu!

Also, instead of pointing Ubuntu to five windows partitions, it only needs one: the MYDOCS partition. (All my Windows installations use a common partition, MYDOCS, as a replacement for their My Documents folders.)

Thanks again,

Walterius

---

