---
title: "edgy eft - Hunting down azureus"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by vaihde7 on 2007-03-13
I've got a real newbish issue here. I installed azureus via apt-get and it installed ok. It even works ok when launched from the automatically created launcer in app menu, but brought up 2 weird things: 

1) I can't open .torrent files with it by using "open" in it's file menu; the .torrent files gray out. I have to drag+drop them to azureus from nautilus to make 'em work. Strange. 

2) I'm trying to make azureus the default app for .torrent files (right click a .torrent file, open with other application. I don't get any list there, so I need to browse the executable) but I can't seem to find the bloody executable! I've tried all in my power from searching and locating and finding with my normal and root accounts, nothing.

The only file including "azureus" seems to be the azureus.desktop (/usr/share/app-install/desktop). Anyone got a clue where do azureus files go when installed automatically by apt-get and why am I not able to see them?

Can someone help me with these two joints?

Thanks

---

### Post by swoskow on 2007-03-13
1.  What are you doing with the open torrent file?  Are you trying to load the torrent for seeding?
The reason I ask is you don't need this unless you are seeding.  If you are downloading a file just double click and follow the instructions in the dialog box.

To open the files just locate the files (the location you instructed Azerues to download too) and open with whatever program you need (if they are music files then open with your player etc).    - (My apologies if you know all this, I don't know how familiar you are with Azerues).

2.  To find the files go   file>open torrents>torrent file>Add Files      the Add files is in the upper left of the dialog box.

You also do not have to go to the files to make changes in how Azereus works - go to tools>options   -  depending on if you set it up as beginner, intermediate or advanced you will have many options to change (including where it puts files).

I hope this helps

---

### Post by vaihde7 on 2007-03-15
Stranger it gets.. I haven't done anything about it and now it seems to work indeed. Great.

---

