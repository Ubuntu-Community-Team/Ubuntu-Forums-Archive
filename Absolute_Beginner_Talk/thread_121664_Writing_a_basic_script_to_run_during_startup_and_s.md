---
title: "Writing a basic script to run during startup and shutdown"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by tsvim on 2006-01-25
Ok, I'm quite a newbie to Linux.
I figured out how to install Ubuntu, to set screen resolution and some other basic stuff.
I've got a windows partition using NTFS, another partition FAT32 with music, photo album, movies etc.
My Documents is on the NTFS.
I understood that it's quite a hassle writing to a NTFS partition.

What I'd like to do is have a script running on logon of linux copying a bunch of files from NTFS (including my Skype contacts and history :-) ) to linux. Then when I shut down copy them to a temporary resort on FAT32.
And although this is not a windows forum if somebody knows how to make a batch file that would copy those files back to NTFS it would be nice. Although I suppose I could figure it out by myself.

Thank you great folks,

T

---

### Post by linuxden on 2006-01-25
Are your skype contacts not on the skype servers??? just like in yahoo and msn???

what other files are you trying to copy over??

---

### Post by tsvim on 2006-01-25
I suppose they should be, but for some reason the linux version doesn't download them. Maybe I messed something up during the Skype installation? (Used Automatix)

The other files are documents (excel, word etc) I'm working on. I'd like to try working Linux only, but when my wife logs on she won't touch the computer unless it's windows. As we keep our Document files together and they're neatly organized, it would be quite a pain to copy them to my FAT partition and have to reconfigure the registry to work on it as My Documents.

---

### Post by linuxden on 2006-01-25
[QUOTE=tsvim]I suppose they should be, but for some reason the linux version doesn't download them. Maybe I messed something up during the Skype installation? (Used Automatix)

The other files are documents (excel, word etc) I'm working on. I'd like to try working Linux only, but when my wife logs on she won't touch the computer unless it's windows. As we keep our Document files together and they're neatly organized, it would be quite a pain to copy them to my FAT partition and have to reconfigure the registry to work on it as My Documents.[/QUOTE]


Are your contacts online at the time? i think you have to click something in skype settings to show your offline contacts otherwise its just going to be empty when none of your contacts are online...

With regards to the excel and word docs...

When you take a document off a FAT32 partitions and bring it into linux side of computer it wont delete it on the FAT32, it just copies it... so you could always just edit the docs on linux and then replace them on FAT32....

---

