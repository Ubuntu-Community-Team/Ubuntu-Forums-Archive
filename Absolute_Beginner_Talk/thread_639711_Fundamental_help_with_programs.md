---
title: "Fundamental help with programs"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by EZ2NV on 2007-12-13
I am a life long Windows user who has recently installed Ubuntu 7.10.  I'm having a hell of a time figuring it out!  I've downloaded e-books, searched these forums all night, and racked my tiny little brain.  But I'm still missing a fundamental piece of the puzzle when it comes to installing AND using programs.

Whenever I installed a programs in Windows, it appeared in the start menu so I'd always know where it was and how to get to it.  Now, whenever I install a program using the Synaptic Package Manager, I have no idea how to run the program...how to use it!  The Add/Remove application process is easy enough, and the application is visible under the applications tab, but I have no idea how to use a program I install using the Synaptic Package Manager.  For instance, I'd like to password protect a couple folders, so I downloaded cfs (Cryptographic Filesystem) using the Synaptic Package Manager.  Sooo...now how the hell do I use the damn program??

ANY assistance would be greatly appreciated!  PLEASE help a complete newbie out!

---

### Post by skrribble on 2007-12-13
some programs in linux can only be run using the terminal, and i suspect this is one of them

here is a how to for cfs
[http://www.ibiblio.org/pub/Linux/docs/faqs/security/Cryptographic-File-System](http://www.ibiblio.org/pub/Linux/docs/faqs/security/Cryptographic-File-System)

---

### Post by EZ2NV on 2007-12-13
I see!  Thank you so much!  I suppose that ndiswrapper is another program that can only be run in Terminal?  I need to use it to make my wireless card work.

---

### Post by RomeReactor on 2007-12-13
Hi. Yes, ndiswrapper is a command line program, but you can install a graphical front end for ti called **ndisgtk**; look for it in Synaptic, or to install from the terminal:
```
sudo apt-get install ndisgtk
```

There doesn't seem to be a graphical frontend for cfs, though.

Welcome to the forums!

---

### Post by EZ2NV on 2007-12-13
Thank both of you for your help, though I have another question.  I installed ndiswrapper and ndisgtk.  But now where do I find ndisgtk so I can use it?  Sorry I'm having such a difficult time grasping what should be an easy concept...

---

### Post by skrribble on 2007-12-13
open a terminal and type
```
sudo ndisgtk
```

---

### Post by EZ2NV on 2007-12-13
Beautiful!!  Thank you so much!  So I can see that using Terminal is going to be integral to efficiently using Ubuntu...Time to start studying!

---

### Post by Jet8225 on 2007-12-13
I'm having the same problems as him with bit torrent. Does anyone know how to run it?

---

### Post by skrribble on 2007-12-13
i would recommend using the program "deluge" for torrents

go here to get it
[http://www.getdeb.net/release.php?id=1758](http://www.getdeb.net/release.php?id=1758)

---

### Post by The Cog on 2007-12-13
> **EZ2NV said:**
> Beautiful!!  Thank you so much!  So I can see that using Terminal is going to be integral to efficiently using Ubuntu...Time to start studying!

If all you want to do is launch a program, you can also:
1) press Alt-F2 and type the program name into the popup box, or 
2) right-click the desktop and create a launcher icon.

But yes, the command line is immensely powerful and worth learning a few basics.

---

### Post by RomeReactor on 2007-12-13
> **EZ2NV said:**
> I installed ndiswrapper and ndisgtk.  But now where do I find ndisgtk so I can use it?
You cna find it in "System->Admnistration->Windows Wireless Drivers".

> **Jet8225 said:**
> I'm having the same problems as him with bit torrent. Does anyone know how to run it?
Just double-click on a .torrent file, and BitTorrent will show up asking you where to save the file; if you close it before the download is finished, you can resume by double-clicking the .torrent file again, and this time it will ask you if you want to continue with the download. Otherwise, you can edit the menus (right-click on the menus in the top panel, and select "Edit menus"). In the left pane, select "Internet", and on the right check the box for "BitTorrent".

PS: [Deluge]("http://deluge-torrent.org/downloads.php") is indeed awesome.

PPS: [The terminal]("http://www.linuxcommand.org/") is also awesome.

---

