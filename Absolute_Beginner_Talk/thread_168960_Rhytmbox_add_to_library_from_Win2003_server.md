---
title: "Rhytmbox add to library from Win2003 server"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by theking2 on 2006-05-01
Being a lucky (?) owner of a Win2003 server with all my legal mp3 files (honestly, I've actually bought all those CDs!) I want to add them to the Rhythmbox library. I have a "media on Win2003" icon sitting on my desktop and there is one in "Places". Don't ask me how they got there it needed some twiddling and tweaking. I can open them fine and they show my MP3s. Yet, when I try Import Folder Into Library there are no such icons in the left hand side. I've browsed my complete harddisk and did not find the shortcut file (pardon the MS jargon) that points to the Win2003 server. 
How do I import a folder to the Rhytmbox Media Player when the files sit on a smb file share?

---

### Post by underdog5004 on 2006-05-01
what filesystem is the Win2k drive? NTFS? Fat32?. Depending, you may find help in the help document...just click on "Ubuntu starting guide" (or something similar, can't remember the name. It's the bottom selection on the main help page) and follow the instructions under the "How do I make NTFS mounted on boot and read-only?" section or the "How do I make FAT32 mounted on boot and read-write?", depending on the filesystem you've got. You may also want to edit /etc/fstab if you want the drive to be mounted on boot.

---

