---
title: "Some quick server/programming questions"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by radams58 on 2006-01-15
I'm not sure if these are ABSOLUTE newbie questions, but they are pretty close.

I've got a fileserver running now in my home/home office that's a Vector Linux 4.1 Distro.  It's great for sharing my MP3's, TV shows, and Movies but I need to upgrade it and I'd like to switch to a Debian distro.

Here are the things I'd like to do with it, and the solutions I've found so far.

First - No gui, this will be a TUI install only as I'm planning on sticking it in a closet and letting it hum along (which is why I'd like a nice stable linux install).  Which means everything needs to be accessible from SSH (or ideally a web front end)

	Soft Raid - Linux
	Torrent	- Torrent Flux
	Newsgroup - ???
	Printer	- Samba
	Sharing	- Samba
	VPN	- VNPD?
	FTP	- ProFTPD
	HTTP 	- Apache2/PHP5
	Database - MySql
	Router	- ???
	WAP	- ???
	CD Recording - ??? (Web Front End)

I'd like to use an  Airnet AWD154 for the WAP.

I've been digging around trying to find a PHP solution for binary news reading, but as yet have been unlucky.  Same for routing/wap.

Any help or suggestions (or improvements) would be nice.

Oh yeah, here's the prospective hardware:

Proc - Athlon XP 2400 (left over from previous upgrade)
OS HD - WD 8 Gig (left over from Xbox upgrade) (PATA)
FS HD - 4x 7L300S0 Maxtor 300GB Drives (SATA)
Mobo - PC CHIPS M848ALU
Vid - Generic nVidia Vanta
Ram - 512MB PC3200 (Samsung CAS 2.5)
2nd NIC - Airnet AEG100
Wireless - Airnet AWD154
Burner - ND-3550A
Sata - PROMISE SATAII150 TX4 

I'm pretty sure all that AirNet actually has good linux support, (and I'm boycotting LinkSYS) so they're the choice for networking.

Thanks for any thoughts or feedback.  I do appreciate the help and am continuing to pursue answers via a searching.

Rob

---

### Post by bscbrit on 2006-01-15
It should work.  I assume with the software that you are installing that you intend internet users to have access to it?  If so, consider your firewall, antivirus, backup sofware.  I would also recommend setting it up in stages - but you probably were already planning to do that!

Your 'left over' bits and pieces are better than some of my existing workhorses!

---

### Post by honeydew on 2006-09-25
ninan, is a newsgroup client with a web interface... another one is hellanzb which is a cool console based newsgroup client.

---

