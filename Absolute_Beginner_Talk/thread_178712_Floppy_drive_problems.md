---
title: "Floppy drive problems"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-05-18
Hello all,
just finished my first install of Ubuntu and everything is working pretty well except for a few things.
I tried updating my firefox bookmarks and found that Ubuntu can't mount the floppy.

error: given UDI is not mountable volume

What can I do and how??

Also I am a bit cinfused about getting a command line and where to locate it.
any and all input is always appreciated.

KK

---

### Post by Sef on 2006-05-18
With Breezy there is a bug in the partitioner.  Here is the fix.

[http://www.ubuntuforums.org/showthread.php?t=93139&page=3&highlight=floppy+Drive]("http://www.ubuntuforums.org/showthread.php?t=93139&page=3&highlight=floppy+Drive")

Note: in the directions, you will need to make one small change in line 2:  Change sudo to kdesu.

> Also I am a bit cinfused about getting a command line and where to locate it.

With Kubuntu, it is called Konsole. (Kmenu > System >Konsole)

---

### Post by skinnygmg on 2006-05-18
to find the terminal...

KDE: KMenu > System > Konsole
Gnome: Applications > Accessories > Terminal

---

### Post by KarmaKing on 2006-05-18
thanks, but none of those options on the link worked.  When I downloaded and pasted (sudo dpkg -i pmount_0.9.6-1~breezy1_i386.deb)

error:
dpkg: error processing pmount_0.9.6-1~breezy1_i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
 pmount_0.9.6-1~breezy1_i386.deb

---

### Post by Sef on 2006-05-18
I got it working one time, but later after a reinstall, I had the same problem.  Only got my floppy working when I installed Dapper.  If you want to wait for it to be stable before installing, you only have to wait till 1 June.  There was one small change I had to do, but that was it to get it working.

---

### Post by KarmaKing on 2006-05-18
bummer, all my bookmarks are on the floppy.

after I figure out how to show files between XP an ubuntu I can just take the file from the partition?

I have alot to do on my to do list:)

---

### Post by KarmaKing on 2006-05-18
bummer, all my bookmarks are on the floppy.

after I figure out how to show files between XP an ubuntu I can just take the file from the partition?

I have alot to do on my to do list:)

---

### Post by Sef on 2006-05-18
> after I figure out how to show files between XP an ubuntu I can just take the file from the partition?

Yes. To share files, you need either a FAT32, ext2, or ext3 File System on your computer.  Both Windows and GNU/Linux can both read and write to them.

---

### Post by KarmaKing on 2006-05-18
I set that up alread as a FAT32 it is just  a matter of figuring that out as well

thanks Sef.

---

### Post by Sef on 2006-05-18
You're welcome.  Please keep them questions coming.

---

### Post by KarmaKing on 2006-05-23
today is a good day:)

I finally mounted the floppy..he he he

I am not sure where I read it, but I put in a floppy and pressed format under Apps--system tool--floppy formatter.  Then I left the disk in and went to Places--Computer--Floppy.  I right clicked then pressed mount and bamm bamm!!

---

### Post by Sef on 2006-05-23
> I finally mounted the floppy..he he he

Glad to hear that you got it up and running.

---

