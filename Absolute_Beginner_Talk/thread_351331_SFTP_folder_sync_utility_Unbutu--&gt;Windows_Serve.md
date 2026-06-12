---
title: "SFTP folder sync utility Unbutu--&gt;Windows Server"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by will m. on 2007-02-01
Hello,

I have tried the applications below in the hopes of finding one that would meet my need for SFTP folder sync between my Ubuntu 6.10 build and a Windows server at work that can be accessed using SFTP.

Simple Backup Config - I found that Simple Backup Config is easy to setup but a) I think I actually need a folder sync tool and b) I'm not certain when I invoke backups that anything is actually happening.

Rsync (using Grsync GUI) - The GUI seems straightforward enough but I am really not sure if SFTP is even supported.  If it is I don't see the opportunity to input username and password info.  I tried sftp://username:password@host.domain/directory but this didn't seem to work. 

Unison - I tried some of the same attempts at SFTP protocol as with Rsync to no avail.

I have successfully connected using Filezilla.  I wish I could just find an automated version of Filezilla.  Is there any such utility out there?  

Your patient input would be very appreciated.

Will M.

---

### Post by will m. on 2007-02-01
I have done a little bit of additional research on this and found that "Connect to Server" allows me to connect to the server via SFTP by using the "Custom Location" option and the inputting:

sftp://username:password@host.domain/directory

I can transfer files, no problem.  However, I can't see the files that are already in the directory and when the files I have transferred aren't visible (when I access them on Windows).  Any idea why this happens?

I like the idea of a mounted drive where I could store my files remotely (and where they would be backed up automatically).  I also like the idea of having a directory that, whenever changed would be updated to the remote site that I am trying to access.  But I lack the knowledge of how to use the command-line applications, like lftp or rsync.

Any help would be greatly appreciated.

Will M.

---

### Post by will m. on 2007-02-01
Well, some further exploring in the forums has brought me one step closer.

[http://www.ubuntuforums.org/showthread.php?t=270806&highlight=mount+sftp]("http://www.ubuntuforums.org/showthread.php?t=270806&highlight=mount+sftp")

But the problem I seem to be having is related to Windows login.  When I access my SFTP site I have to provide a username and password (from LDAP).

Is there any way to do this?

Will M.

---

