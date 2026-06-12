---
title: "Problems with file sharing! help and/or opinions needed"
date: 2007-04-17
forum: Apple PPC Users
---

### Post by versatilehearts on 2007-04-17
i have an iBook G4 running MacOS 10.4.9, Windows PC running XP Home, and an iMac G3 running ubuntu 6.10 (not hip to the naming conventions yet, sorry)

what i want to do is be able to save/transfer files (mainly videos) from the PC and iBook to the iMac as it has (for some reason) the largest hard drive in the house. so far i can pick up the PC with the iBook and vice versa but bupkis as far as the iMac picking up or being picked up by either other system. i am very unskilled as far as linux command line goes so a GUI solution would be perfered. also i have concerns about file system issues (as i know that OSX dosent like to write to NTFS as HFS is invisible to XP). 

any help or advice would be great! thanks in advance!

---

### Post by bogoliubov on 2007-04-18
Both Ubuntu and OS X uses "Samba" to share files and printers with Windows. 
The settings can be a bit tricky, but in Ubuntu you simply go to Administration -> File sharing, then set it up to you liking. You might have to change firewall settings in Ubuntu.

---

### Post by bogoliubov on 2007-04-18
I just remembered that you can try MacFuse as well. It essentially allows you to mount for instance SSH shares in the Finder. You can also use SSH-FS in Ubuntu. About windows I don't know (never use it).

This way you can mount stuff over SSH (secure connection) and copy your files...
The drawbacks are that MacFuse is still a bit experimental, and you might need to do some work in the terminal to get everything up and running on both machines.

MacFuse: [http://code.google.com/p/macfuse/](http://code.google.com/p/macfuse/)

---

