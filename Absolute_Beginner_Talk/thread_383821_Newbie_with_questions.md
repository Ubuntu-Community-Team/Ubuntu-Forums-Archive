---
title: "Newbie with questions"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by mariewhitehead on 2007-03-13
I want to set up a wireless home network. I have 2 computers- one- an older desktop Dell that I want to make the main computer for the network and on which I recently installed ubuntu 6.06 as the only OS on the system. (And am loving it BIG TIME!!!) The other is a 2 year old Dell notebook with WiFi running WinXP. I recently purchased a linksys wireless modem that can be used with both systems. I have an external 100 GB drive and a new Lexmark all-in-one printer (non-network type) that I would like to connect to the Linux computer, but be able to print, see files on the external HD with the windows laptop if needed.

The questions:
1. How to set up the computers (one with Linux, the other with Windows as I have allot of money invested in iTunes music and videos)  and software to be a network? Do I need to install unbutu server or can the desktop install take care of this?
2. When I installed ubuntu, I somehow missed the part where I could manually set the partition. Anyway to do that without reinstalling? I want part of the old computer to be a storage spot for archived files I may want at sometime in the future but don't want to keep  on my laptop or on the external hard drive.

MizMarie

PS- where do you get those cool coffee bean pics?

---

### Post by raja on 2007-03-13
1. You can set up a network with windows computers easily with the desktop install itself. Samba allows sharing folder with a windows network. You can set it up from System --> Administration --> Shared folders.

2. You can boot with the live cd and then use gparted to shrink the main ubuntu partition. With the free space created, you can make your storage partition.

---

### Post by VaporTrace on 2007-03-13
Perhaps this is a forum violation but I have had a lot of help with the guide at [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

Ah the simplicity of Ctrl+f

---

