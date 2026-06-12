---
title: "A few problems (fat32, etc)"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by doubledave on 2007-06-02
I'd like to start out by saying any help is very much appreciated, but I'm sort of new at Ubuntu, so bear with me.

First, I have Feisty 64 installed.  I dual-boot XP, and it took me forever to get my wireless card working, so if there's any way to save the current Ubuntu setup, I'd be happy.

Here are my problems:

A week ago I changed the filesystem on one of my harddrives, so that I could access and edit my music collection under both xp and ubuntu.  It was previously NTFS, but I couldn't get the plugin to work right to edit files, so I moved all my music to an external, changed to FAT32, and then copied all the music back.  This was fine under Windows, and all my files are intact, but the only problem was Ubuntu couldn't see the files.  I can't remember exactly what the message was, but something along the lines of me not being logged in as 'root', and my permissions being messed up.

So what I did was try to change the Ubuntu login (I didn't change passwords or anything). so that I could login as root by default.

Upon rebooting, Ubuntu froze with the spinning circular cursor, and continues to do so every time I start it.

I tried starting up in the equivalent of 'safe-mode' but it's the same song and dance.

1. Basically, I need to know how to save Ubuntu from the command line (or whatever the hell it's called) during boot.

2. If Ubuntu can be salvaged, I'd really like to get the FAT32 drive back up and running.

3.  And if I can get off the ground and running again, is there any way to login automatically on startup as 'root'?  I hate having to put in passwords every time I want to do ANYTHING.  I'm the sole user of this computer, and I know the security is there for my benefit, but it is really tedious.

Again, thanks to anyone out there who can help, sorry about the long post, and I'll provide any info that is needed.

---

### Post by AlexenderReez on 2007-06-02
Firstly...ubuntu or linux itself is NOT windows...which even anybody never touch computer then press power on....play around a while then he/she will master easily.....i mean that you need to depend on tips and tutorials section to learn,that is the only fast way to master linux........by the way---->


> If you want to enable root account (which is not recommended) enter the following command.

$sudo passwd root

This will prompt for a new root password and once you confirm it, you can start using the root account to login.

If you want to disable root account in ubuntu you need to lock the root account by using the following command

$sudo passwd -l root

If you want to work on a root console you’d better use the following command

$sudo -i 

---

### Post by doubledave on 2007-06-04
thanks for that, and i understand that linux isn't windows.

as for the first parts of my question...

any advice on what to do?

since then i've managed to muck up more stuff, and i need to edit the GRUB- but, like i said, i can't even get into the operating system.

---

