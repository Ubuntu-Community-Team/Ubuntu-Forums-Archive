---
title: "Symbolic Links Break"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2008-03-10
I have a portable hard drive with a lot of video files in a downloads folder, which is the destination for my rss fed bit torrent dls.  This folder is monitored by a script which grabs metadata for each new download every thirty minutes and creates a link to each new download.  The link is created like this: <CODE>ln -s -f /original/file/name/path /new/link/path</CODE>

The script also inserts all of the metadata about new files it finds into the MythVideo MySQL database.  It then monitors the database for items deleted from the database and then deletes the corresponding files in the Downloads folder.

The way all of this works is that all I have to do is run MythVideo > VideoManager > Scan and all of the files are managed from within the program.  And, if I want to do delete a file, all I have to do is remove it from the Manager database from within the on-screen setup and all of the related data (including the original large file) is removed.

Here's my problem: For some reason, occasionally the links break.  And when they do, MythVideo manager sees them as disappeared, and deletes the links.  When that happens, my originals are also removed by the script.  

So what's going on?  Is it because the links are cross drives?  Or, here's something: the portable drive is Fat32 and the links are stored in my /home directory for user /tv on an Ext3 partition.  Any ideas?

-Mike

---

### Post by mikeserv on 2008-03-10
Bump.

---

### Post by mikeserv on 2008-03-11
Bump.

---

### Post by Arkenzor on 2008-03-11
One possible explanation would be mounting issues; if your external drive failed to mount for some reason, then the links pointing to its contents will be considered "rotten".

Don't know if that's the cause of _your_ problem though; external USB drives have been giving me a good taste of hell these days and I'm getting somewhat paranoid...

---

### Post by mikeserv on 2008-03-11
Nah, I considered that. When the links break, it's never all of them, just a few here and there.  And besides, the drive is mounted in the fstab and remains mounted the entire time.  And here's another weird thing: last night I decided to check on one of these broken links.  I opened up the properties of the broken link in GNOME and checked the path of the target.  The target was there, with no issues getting to it.  

I think it might have to do with seek time on the fat32: the drive is really slow.  So I'm considering that if the drive is busy with one file (like allocating file space for new downloads in ktorrent) then some of the other links might break.  And once they break they don't "heal" themselves as soon the file becomes available again.  

So what I might do is reformat the drive with the journaled EXT3 system and see if the problem persists.  Besides, the fact the the fat32 drive can't hadle filesizes over 4gbs is a real annoyance, anyway.  The truth is, I 'm not entirely sure why I chose fat32 in the first place: I have the ext2 driver on my Vista machine.  

Then, if the problem does persist, I'll have to write a acript that will search the folders for broken links, and, after finding them, regenerate them, so long as their target path is still available.

-Mike

---

