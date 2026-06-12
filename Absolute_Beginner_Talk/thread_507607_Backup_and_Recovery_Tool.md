---
title: "Backup and Recovery Tool"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by walt+walt on 2007-07-23
Dear all
I have read all these threads about backing up. I have also used GrSync, Sbackup Homebackup, however no scripts, because I am after a gui tool. All the above mentioned (and others too) did only partly serve my needs.

Here is what I am looking for as a usable backup/recovery tool:

- it must have a gui interface
- it should be able to make backups on harddrives 
- it should accept direcrory includes and excludes
- it should either use rsync, incremental and full backups (when and what defined by user)
- it should give a notification after backups with status
- recovery should be easy and directories to restore should be definable.
- it must keep a logfile and this should be easy viewable/understandable by the user

At the moment I use GrSync with about a dozen different files which I have to start separately and shouldn't forget. Hmm. One gets lazy.

I certainly appreciate any hint. 

Many thanks and cheers, walt

---

### Post by stinger30au on 2007-07-23
i use[ syncback freeware]("http://www.2brightsparks.com/downloads.html#freeware") version under wine, works a treat

---

### Post by mips on 2007-07-23
try rsync with one of the gui frontends.

[http://www.debianadmin.com/rsync-backup-web-interfacefrontend-or-gui-tools.html](http://www.debianadmin.com/rsync-backup-web-interfacefrontend-or-gui-tools.html)
[http://www.debianhelp.co.uk/backup.htm](http://www.debianhelp.co.uk/backup.htm)
[http://ubuntuforums.org/showthread.php?t=194849](http://ubuntuforums.org/showthread.php?t=194849)

---

### Post by walt+walt on 2007-07-24
Many thanks to all your help. I will try out KDAR. This looks promising even I couldn't get it started till now. Some funny errors I must follow up.

Again, thanks

---

### Post by Rocket2DMn on 2007-07-24
I use Simple Backup, it was suggested to me a few months ago.  I haven't used the recovery feature at all, but I believe it meets all your criteria, except for the maybe the rsync.  Also, it doesn't give you a status message when it's done, it just finishes silently.
Other than that, I think it's nice.

---

### Post by walt+walt on 2007-07-28
Okay, I have spend hours and hours to check out some of these backup-tools. As I mentioned before, I thought I could settle with KDAR. Unfortunately it bombed out every then and there.

I am really wondering, what linux-profs use to keep a desktop properly backed up or synced. Since USB-Disk-Storage (inmy case here)  are less a problem I also thought to use mirroring. Unfortunately all the howtos and installation-help were either so complex or disencouraging that I just gave up.

Maybe I till hope for a lucky tip which would lead to a tool according to my specs at the beginning of this thread.

Anyway, many thanks forward and backwards. (I do backups manually at the moment which is definitly  plague).

Thanks and regards, walt

---

### Post by akba0012 on 2007-08-25
I have Simple Backup Restore installed in my computer but it is not in my applications menu.

How do i get it on my Applications menu so I can launch the GUI?

I tried to uninstall it and then reinstall it, but that didn't solve it. 

Thanks in advance.

---

### Post by Golyadkin on 2007-08-25
Rightclick the menu and chose "Edit Menu's". Then you can enable the entry. By the way, I though Simple Backup Restore shows up by default under the System preferences part of the menus.

---

### Post by mlentink on 2007-08-25
> **Golyadkin said:**
> By the way, I though Simple Backup Restore shows up by default under the System preferences part of the menus.
It does.

I use it too since a couple of months, works like a dream.

---

### Post by stinger30au on 2007-08-25
> **stinger30au said:**
> i use[ syncback freeware]("http://www.2brightsparks.com/downloads.html#freeware") version under wine, works a treat

got to back you up on this. i have been using it for ages in wine, has never skipped a beat.love it

---

### Post by ashishgoel on 2007-08-29
how can i backup the whole system (including operatin sys) and restore - in event ubuntu doensn't boot???

In win - i had used Acronis Image and Norton Ghost - worked beautifully for Win XP

---

### Post by fallencyi on 2007-08-29
> **ashishgoel said:**
> how can i backup the whole system (including operatin sys) and restore - in event ubuntu doensn't boot???

In win - i had used Acronis Image and Norton Ghost - worked beautifully for Win XP

There are Opensource & Free tools that do a fine job of it (clonezilla, partimage,). But since you said you used Acronis, I just wanted to let you know that it will work fine for linux. Just do a backup from the bootdisk that Acronis uses.

 I had Acronis from before I got into linux, & it is the tool that I still use for imaging my system.

---

### Post by ashishgoel on 2007-08-30
thanx mate

---

