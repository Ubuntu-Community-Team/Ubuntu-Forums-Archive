---
title: "Need help setting up file server"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Atmosphere on 2007-05-17
Again like 90% here am linux noob. I have read several threads that answered these questions of mine but since i read them at work i had not bookmarked them and can't seem to find them again.

Basically the computer currently runs windows server 2003 and does the following/or i need it to do the following after i install ubuntu over it.
- Store mainly media files on 4 seperate HDD's in NTFS to share to two other systems running XP/vista
- Used to rip DVD's
- Used to download torrents
- Primary HDD is used only for OS
- Used to copy cd/dvd's from time to time.
- is only a box and controlled through RDP.
- share a Canon LBP 1100 printer to 2 windows systems and 2 linux systems

if anyone happened to be smarter then me and bookmarked references that could help me out i'd be very grateful.

---

### Post by RichGuk on 2007-05-18
> **Atmosphere said:**
> Again like 90% here am linux noob. I have read several threads that answered these questions of mine but since i read them at work i had not bookmarked them and can't seem to find them again.

Basically the computer currently runs windows server 2003 and does the following/or i need it to do the following after i install ubuntu over it.
- Store mainly media files on 4 seperate HDD's in NTFS to share to two other systems running XP/vista
- Used to rip DVD's
- Used to download torrents
- Primary HDD is used only for OS
- Used to copy cd/dvd's from time to time.
- is only a box and controlled through RDP.
- share a Canon LBP 1100 printer to 2 windows systems and 2 linux systems

if anyone happened to be smarter then me and bookmarked references that could help me out i'd be very grateful.

- Mounting NTFS for read/write: (before for sharing), mount NTFS - search the forums or [click here]("http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html")

- Rip DVD's: something like dvdRip I think

- Torrents: for Kde something like KTorrent (unsure for Gnome :P), or you could install Java and use Azereus

- HDD for OS: That's fine just put Ubuntu here :p

- Copy CD/DVD's: Again for KDE I'd use k3b, great bit of burning software but I'm unsure on Gnome.

- RDP: Not to sure how to get this working but I'd normally just use VNC or FreeNX.

- Share files/printer: Install samba, search the forums for guides :)

---

