---
title: "All network fast except for samba"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by getut on 2006-12-07
Wow... I'm having problem after problem with Ubuntu Edgy on my new install on my new PC. I haven't even gotten the sound issue worked out here [http://www.ubuntuforums.org/showthread.php?t=310938](http://www.ubuntuforums.org/showthread.php?t=310938) yet and it now seems I have a networking issue.

I'm wondering if my rig is just too new to be using Linux based on the sound problems above and network issues below that prompted this thread.

The newest issue I have is network related. I have set up samba and have it running and allowing connections properly, its just that it is horribly slow. I'm sharing a media drive with DIVX movies and MP3s. It takes 5-6 minutes just to select some of the larger files, then when it finally does select and start, it can't even keep the buffer full. Other protocols run fine such as when serving up FTP data. Even SMB works fine when pulling FROM a windows station but not serving it up over SMB with samba.

I don't think this could be a driver issue since samba seems to be the only thing affected, but here is additional possibly relevant information? The ethernet driver is NOT included in Ubuntu. I had to find it and compile it myself and then insert it. The motherboard is an ASUS P5L-MX with integrated Attansic Gigait NIC.

---

