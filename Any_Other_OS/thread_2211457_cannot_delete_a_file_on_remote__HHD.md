---
title: "cannot delete a file on remote  HHD"
date: 2014-03-16
forum: Any Other OS
---

### Post by capo1949 on 2014-03-16
Hi All
I am using Mint Mate 16
I cannot delete a file, as detailed in the attachment. The file 'archive'  exist when I do an 'll' and yet advised that it does not exist,
I want to delete some of the contents. I tried using caja under root privellidges and the system advised input/output error.
I tried changing the permissions but couldnt as you can see. 
Hope someone can help me
Graham

---

### Post by howefield on 2014-03-16
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by Carl H on 2014-03-17
What does this return?

```
file archive
```

---

### Post by capo1949 on 2014-03-17
graham-Studio-1558 Seagate Expansion Drive # file archive
archive: ERROR: cannot open `archive' (No such file or directory)
graham-Studio-1558 Seagate Expansion Drive #

Thank you for your prompt response

The files I am trying to delete are archived from BIT back in time results and are mp3 files.

Many thanks

---

### Post by Carl H on 2014-03-17
This is odd. Are you definitely in the right directory? Can you do these commands and then post the output?

```
pwd
```
```
ls -al | grep archive
```

---

### Post by capo1949 on 2014-03-17
graham-Studio-1558 Seagate Expansion Drive # ll
total 144
drwx------  1 graham graham      0 Mar 15 11:48 .
drwxr-x---+ 3 root   root     4096 Mar 17 14:44 ..
drwx------  1 graham graham      0 Mar 16 16:32 archive 
drwx------  1 graham graham 143360 Mar  9 20:47 MyVideos
drwx------  1 graham graham      0 Mar 15 12:27 recent back ups
drwx------  1 graham graham      0 Nov  4 23:37 $RECYCLE.BIN
drwx------  1 graham graham      0 Aug 25  2013 System Volume Information
drwx------  1 graham graham      0 Nov 11 13:53 .Trash-1000
graham-Studio-1558 Seagate Expansion Drive # ls -al | grep archive
drwx------  1 graham graham      0 Mar 16 16:32 archive 
graham-Studio-1558 Seagate Expansion Drive # pwd
/media/graham/Seagate Expansion Drive
graham-Studio-1558 Seagate Expansion Drive #

---

### Post by steeldriver on 2014-03-17
The simplest explanation would be that the directory name looks like [FONT=courier new]archive[/FONT] but isn't (e.g it has a trailing space, or unicode characters). Assuming you've checked that (using tab completion for example) then the next question would be what is a "remote HHD" and how is it exported / mounted. If it's via nfs then there are a few possible gotchas (syncing? subtrees?). Or is it in fact a pluggable **local** drive (as suggested by the /media mountpoint)?

---

### Post by capo1949 on 2014-03-17
Hi
Thx for your prompt response.

[COLOR="#000000"][COLOR="#FF0000"]Apologies it is a local plugable HDD[/COLOR][/COLOR]

 I do not use tab completion as I usually use caja for file manipulation and not cli
I used caja to succesfully remove the other files in the archive directory, when I tried to remove the music files the system alarmed
'Error when getting information for file '/media/graham/Seagate Expansion Drive/archive /graham-Studio-1558/graham/3/new_snapshot/backup/home/graham/Music/Woody Herman': Input/output error'. See caja image attached and for results of 'df' and also reult using GPARTED

I hope this info helps to resolve the proble.

Many thanks for your time

---

### Post by steeldriver on 2014-03-17
I'm not familiar with caja but 'Input/output error' in most contexts indicates a low-level read/write error (perhaps bad blocks on the disk... or the archive file is corrupted?)

---

### Post by capo1949 on 2014-03-17
thanks for that, but can you offer a solution to the deleting problem using cli?

---

### Post by Carl H on 2014-03-17
I agree with steeldriver; it sounds like the file or the disk might be corrupted. 

I can see that your HDD is formatted as NTFS. It might be worth plugging it into your Windows machine to see if that can read it. (NTFS is Windows' file system). 

Ubuntu has a program called ntfsfix, in the ntfsprogs package, which may be able to repair a damaged NTFS disk.

---

### Post by capo1949 on 2014-03-17
hi
I can play these mp3 file from archive and they are good? so I dont think they are corrupted

---

### Post by Carl H on 2014-03-18
How do you access them?

---

### Post by capo1949 on 2014-03-18
I double click on the mp3 file on the HHD in question, using caja, system opens Banshee and plays Woody Herman file.

Yet when trying to delete music files the following error is reported
'Error when getting information for file '/media/graham/Seagate Expansion Drive/archive /graham-Studio-1558/graham/3/new_snapshot/backup/home/graham/Music/Woody Herman': Input/output error'.

---

### Post by Carl H on 2014-03-18
Your original question was about changing the permissions of archive. 

Copy this and paste it into a terminal :- 
```
chmod ugo+rwx  "/media/graham/Seagate Expansion Drive/archive /"
```

Now cd to /media/graham/Seagate Expansion Drive and ll - what are the permissions of archive now? 

If you didn't get any errors, copy and paste these commands, one at a time.
```
cd "/media/graham/Seagate Expansion Drive/archive /"
```
```
ls -al
```

What do you get?

---

### Post by capo1949 on 2014-03-18
thanks for your prompt response

---

### Post by Carl H on 2014-03-19
Okay, so you've cracked it. ;)

You can now cd into whatever directory you want and delete which files you want to delete.  Or you can probably type cd and a space in the terminal, then navigate to the appropriate directory in Caja, and then drag the folder icon from the path bar into the window. (You can do this with most file managers, I've never used Caja but I assume it will work). 

However...    you said that this archive was created by some file backup system? In which case it's quite likely that there will be some sort of database somewhere containing info about all the files in the backup. So even if you can delete them, it might not be such a good idea, as you may then find that your backup doesn't work properly afterwards.

This could explain why the permissions were set so you couldn't delete them.

---

