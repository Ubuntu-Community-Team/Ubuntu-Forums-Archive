---
title: "A little network advice, please?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by juanzo007 on 2008-01-13
Hey folks...

Newbie Ubuntu/linux user, learning tons and am really enjoying it...  I'd like to pick your brains a bit about using the network I've managed to set up.

I have 1 xp box, and two ubuntu boxes, they can all see each other and share folders (don't ask how i got it to work...!).

My idea is to have the old-timer linux box act as a file and ftp server for the network, and probably will want it to be my linux-tinker-around/experiment box. I'll use the XP box just for proprietary windows apps i need.  And my new linux box (built all by myself and only fried one HDD in the process) will be my primary web/email/linux apps box, and will also regularly backup the file server.

 I have samba already set up on both linux boxes with shared folders.  Do i need an automatic backup application like sbackup?  Let me know if this seems like a reasonable setup or if another configuration or set of apps would be better.  Happy to experiment...

Many thanks!

---

### Post by Xavieran on 2008-01-13
Seems fine to me...however,I would write my _own_ backup script in BASH...something like this (but you're free to adapt it to your wishes...)
```
#!/bin/bash
zenity --question --title "Starting Backup" --text "Starting the backup of your home folder...a slight drop in system responsivness is likely,as these are\ very large files being copied..."
DATE=$(date +%d%m%Y).tar.bz2
tar -cjvf /media/disk /home/xavieran | zenity --progress --pulsate --title "Backup Progress" --text "Archiving..."

```

---

