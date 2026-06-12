---
title: "New server setup."
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by adamosis on 2007-03-19
Hey guys,
So I just setup Ubuntu server on an old Compaq Deskpro. 500Mhz, 385MB memory, 40GB, SCSI controller PCI card, DAT tape drive. I've had some experience with Fedora Core and I've had a Ubuntu LAMP server setup running before. I've never started from scratch though. 

I plan on setting this up as a media server, will likely need apache for a media setup I want and Samba to connect to it from Windows or my Mac.

Any recommenation how I should start this? Do I use apt-get for all of this, or any other software I should run? What do you guys think of the GUI VS. command prompt?
Thanks

P.S. I also want to use this box as a Wii Media center hence the Apache requirment.

---

### Post by LanDan on 2007-03-19
using apt-get? that would be exactly the way to go

GUI vs CLI?
depends on who you ask off course, but when it comes to servers i always use the command line (FreeBSD is what i use for servers)  and nothing else. editing a file to configure some things is actually not so hard and often easier, besides having graphical things slows down your box and gives you extra worries with security and its just another thing that could break.

---

### Post by adamosis on 2007-03-19
I'm not very affraid of the CLI. I've always kinda figured that if you're going to use *nix as a server, CLI is the way to do it. Just requires a little more googling to figure out where and what to get going I guess.

I tend to often make things more difficult than they are. Don't always accept the fact that maybe, yeah it was that easy to setup. hehe.

---

### Post by adamosis on 2007-03-19
How the hell do I change the resolution for the CLI? I've never figured this one out. I usually end up ssh-ing into a box rather then physically work with it.

---

### Post by adamosis on 2007-03-22
Hi all,
So I just setup Samba and I have it running but I can't connect to my shared directory. I've narrowed it down to a permissions issue. I know fat32 is a permissions-free file system, but the shared directory resides on this fat32 partition and seems to only be accessible by root. Since I can't change permissions, is there a way to mount with everyone can write capabilities?

What other options do I have here?
Thanks!

---

