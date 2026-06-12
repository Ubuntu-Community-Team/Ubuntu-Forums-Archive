---
title: "filesharing help"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Connollyir on 2008-01-13
Hi. I'm very new to this and I need to transfer files across a network. Now I am used to Windows style drag and drop gui and I want to know how to set that up to transfer files between a Windows XP computer and my Ubuntu machine. Any help is very appreciated.

-Ian

---

### Post by rivalarrival on 2008-01-13
Well, there's a couple ways to do it.  You can access your windows network shares by clicking places > connect to server (works pretty much the same as my network places > create a new network place)

If you want to be able to pull files off of the Ubuntu machine using a windows machine, you'll want to setup Samba Server.

In either case, you might want to check out ubuntuguide.org.

---

### Post by HermanAB on 2008-01-13
The easiest way is with FTP.  Go here ([http://filezilla-project.org/](http://filezilla-project.org/)) and install filezilla client and server on Windows.  Then run gftpd on Linux.

Cheers,

Herman

---

### Post by Connollyir on 2008-01-13
I have Samba installed in the Linux box and I've enabled sharing on a folder on my desktop. On the Windows machine I have a disk drive set to share. Both are configured to use MSHOME as the work group, so everything should work right? but every time i try and access the files on either computer I am prompted for a user name and password. Regardless of the user name and password I use (obviously including my own accounts but others too) I cannot access anything. Any help?

-Ian

---

### Post by Connollyir on 2008-01-13
bump

---

