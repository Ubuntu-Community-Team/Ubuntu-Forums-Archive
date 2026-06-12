---
title: "networking problem w/ vista"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by braves4life@cox.net on 2007-07-27
I am having a problem connecting to a windows Vista shared folder using Ubuntu 7.04.  

I can connect and stream files using both a macbook and using the media center extender of the Xbox 360.

On the ubuntu machine I can connect to the vista machine using the local IP address and the Places->connect to server... menu. I am able to see the folders in the share for the most part, but when I'm navigating through the folders I usually get the following error(for example):

"Nautilus cannot display "smb://192.168.1.136/media/Podcasts". Please select another viewer and try again"

When I am able to navigate to a file and then double-click to open and stream I get this message from Totem Movie player:

"An error occurred"
"Could not open location; You may not have permission to open the file."

If instead I try to copy the file to the Ubuntu computer sometimes it will start and then quit but I can actually play small part that copied over.

I have followed every guide I could find about setting up Samba and smbfs and do not care about accessing the Ubuntu drive from vista because it will be used for streaming media only.  Any ideas about what is wrong?

I have set both user names and passwords on both machines to be identical and have tried it without the windows firewall.  I don't know what my next step should be.

Thanks for any help!

---

### Post by rich.bradshaw on 2007-07-27
Next step logically would be to replace Vista with Ubuntu on the other computer.

I've never got samba working in 4 years...

---

### Post by braves4life@cox.net on 2007-07-27
Well I don't think I'll do that because I like having the Media Center Edition for streaming to the xbox360.  

What could the problem be if I can access the files from the mac but not the linux computer?

---

### Post by morequarky on 2007-11-06
I tell ya, that network share stuff is way too painful.  It should be so much easier.  same network bingo it works...no no...have to have the same windows 'group'.  lame.  absolutely lame.  it took me hours just to get my ubuntu computer to download files from a folder i shared on a mac on the same switch/router/access point.  

there should be a simple tick box on ubuntu network settings that says, tick this and any computer on the local (LAN) network can access any shared folder you specify as shared(note: your computer will be hidden from the network if no folder is currently designated as sharing)  aka you must share some folder or all ports are shut and thus other computers on the same LAN won't be able to find you.

why is it that it's so difficult?  

ok, how about documentation.  next to the smb settings should be a howto on setting it up in laymans terms.

is it really easier to set up file sharing between two ubuntu boxs?  maybe debatable.  i haven't done it in a long time.

---

### Post by timcredible on 2007-11-06
vista is a closed system that's not meant to work with anything except other microsoft systems - rather than trying to get linux to connect to a proprietary microsoft sharing system, why don't you install a standards-based file sharing system like nfs on your vista machine so that you can easily connect to it from anything?

---

