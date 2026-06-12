---
title: "Create new folder on network share???"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by s1mple_M4N on 2006-08-22
Hi all.

I have a dual-boot XP/Dapper PC connected to a Windows home network of 3 machines. One is a basic file server (music, video, document backup).

Through the forums and wiki I have found excellent help to enable me to mount network shares to access files, but I am having trouble finding information about copying files from Ubuntu to the Windows file machine or creating a folder in one of the shared drives.

I have read that Linux has trouble writing to NTFS (server machine) - could this be my problem?

I keep getting permission errors when trying to create folders or copy/paste files. Is there something I need to do with the server to allow my Ubuntu system?

Any advice appreciated.

Thanks,

RoyJ

---

### Post by stig on 2006-08-22
> **s1mple_M4N said:**
> Hi all.

I have a dual-boot XP/Dapper PC connected to a Windows home network of 3 machines. One is a basic file server (music, video, document backup).

Through the forums and wiki I have found excellent help to enable me to mount network shares to access files, but I am having trouble finding information about copying files from Ubuntu to the Windows file machine or creating a folder in one of the shared drives.

I have read that Linux has trouble writing to NTFS (server machine) - could this be my problem?

I keep getting permission errors when trying to create folders or copy/paste files. Is there something I need to do with the server to allow my Ubuntu system?

Any advice appreciated.

Thanks,

RoyJ

Have you tried looking at the Samba links on the Sticky: "READ THIS FIRST prior to posting - IMPORTANT links" at the top of the Absolute Beginners Talk page? You might find these useful. Good luck!

---

### Post by s1mple_M4N on 2006-08-22
> **stig said:**
> Have you tried looking at the Samba links on the Sticky: "READ THIS FIRST prior to posting - IMPORTANT links" at the top of the Absolute Beginners Talk page? You might find these useful. Good luck!

Thanks, I had a good look through some of the links there. A lot of it is over my head or just too long-winded.

I have been able to mount shared folders as drives when Ubuntu boots and can access all shared files on the XP box. That much is OK.

The XP box only serves files and has two users - administrator and limited user (which is logged on all the time). Limited user has no password.

Any ideas?

Thanks again,

RoyJ

---

### Post by Iowan on 2006-08-22
> **s1mple_M4N said:**
> I have read that Linux has trouble writing to NTFS (server machine) - could this be my problem?
AFAIK, this is still true, and may be your problem.  You might be able to build a FAT32 partition on the Windows box that both systems can access.

---

### Post by mariner09 on 2006-08-23
I didn't think NTFS played any role when browsing a network file share.

I use NTFS on my XP machine and if I tell it to share "My Documents" I can read it no problem.  I do select the option to make it read-only when creating the share.

I also noticed, just now, that trying to write to the share gives me an error that I don't have permissions, so a little more playing will have to be done.

---

