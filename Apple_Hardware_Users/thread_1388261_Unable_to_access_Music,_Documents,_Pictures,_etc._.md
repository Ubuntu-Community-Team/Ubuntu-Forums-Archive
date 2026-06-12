---
title: "Unable to access Music, Documents, Pictures, etc. after mounting Macintosh HD"
date: 2010-01-22
forum: Apple Hardware Users
---

### Post by Atheil on 2010-01-22
I have a Macbook Pro 5,5 with Ubuntu 9.10 installed using rEFIt. When I mount the Macintosh HD in Ubuntu, I am unable to access any of the folders under Users, except Public. I tried changing the permissions in OSX, setting "Read and Write" for "Everyone" on a couple of folders, and, when I log back into Ubuntu, I can see that those are the permissions for the folder, but Ubuntu still tells me that I do not have permission to access the folder. I've tried setting the folder to share, thinking that this must be the reason that I can access Public with no problems, but it didn't work.

I've browsed the internet extensively, and the only thread I could find related to the issue was by someone who had the exact same problem as me (I don't know if they had the same macbook though), and it was never solved (the only advice given was to either change the Ubuntu user number, or change the permissions of the folder).

Any help would be greatly appreciated.

---

### Post by linuxopjemac on 2010-01-23
what happens if you do it as root ?

---

### Post by Atheil on 2010-01-23
> **linuxopjemac said:**
> what happens if you do it as root ?

If I run nautilus as root I can access the folders just fine. But if the permissions are set for everyone, why wouldn't just a regular user be able to access the folders? And why specifically those folders?

---

### Post by jbiggs12 on 2010-01-24
Try logging in on your Mac partition and performing
```
diskutil disableJournal YOURDISKHERE
```
Where YOURDISKHERE is the Macintosh HD partition that can be identified using the
```
diskutil list
```
command. Had the same problem myself on a Linux Mint partition. That should fix it... if not, then try this thread:

[http://ubuntuforums.org/showthread.php?t=740531]("http://ubuntuforums.org/showthread.php?t=740531")

Cheers!!

---

### Post by jbiggs12 on 2010-01-24
Also: once you disable journaling on your mac side, you can open your home folder as root (e.g, /Users/Bob) and right click on, say, "Documents" and change the file permissions using the "Permissions" tab.

---

