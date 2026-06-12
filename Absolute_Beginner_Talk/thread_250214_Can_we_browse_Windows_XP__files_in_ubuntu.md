---
title: "Can we browse Windows XP  files in ubuntu"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by JuniorNA on 2006-09-03
Hey guys...

Just had a quick question. Just installed ubuntu and I'm learning as I go .

I was able to get to network neighborhood and actually see the windows 2000 server pc and windows XP machine. I have all my network files on 1 servr to make things simple. I was able to click on the computer name, but it said that I cannot browse this computer. 

Can ubuntu see windows files? I believe the drive that I was trying to access on the win xp machine was fat32 .

Is this at all possible? 

thanks

---

### Post by mssever on 2006-09-03
It's very possible. Did you nter the proper username/password (as defined by the XP machine? It's also possible that something could be mis-configured on the XP machine.

---

### Post by JuniorNA on 2006-09-04
> **mssever said:**
> It's very possible. Did you nter the proper username/password (as defined by the XP machine? It's also possible that something could be mis-configured on the XP machine.
Thanks for the help. 

THe XP machine seems to be ok. I have 5 laptops in the house, all connecting to the XP machine with 2 300g drives. We share nothing locally on any laptop, everything is stored on 4 or 5 different folders on the network share of the XP machine. Never had a problem with that drive or the XP computers connecting to it. 

Now the thing is. I can connect to other computers in the house that are running FAT32 partitions...I have 2 laptops that are running FAT32 and I can browse all their files and folders on their machine...

But the SHARE DRIVE, the one that i really want to get...is 200 gigs of NTFS. I dont think ubuntu is setup to read NTFS partitions, maybe there is a way for ubuntu to read NTFS partitions. 

I know thats probably the problem since I'm 2 for 2 when browsing a network that has fat32...but i'm 0 for 4 when browsing a computer that is running NTFS. 

Any suggestsions?

---

### Post by breuerp on 2006-09-04
If you have samba installed (sudo apt-get install samba), you'll be able to read/write to the NTFS partitions as long as they're shared out on the Windows machines.  I have a Win2K3 server running one of my share drives at home (have to have something to break) and it works just fine with Samba.

---

### Post by bluefrog on 2006-09-05
the simplest thing to do is using the address location in nautilus (see natilus prefrences for that).

enter
smb://ip-of-your-xp-2003-2000-machine/c$
at the prompt enter the name of your windows administrator (usually administrator) and his password.

you will have access to all C (can do the same for D or whatever partition you have on your windows machine.

James

---

### Post by JuniorNA on 2006-09-05
ok, im assuming this will be a command line driven mapping feature? 

Anyway to get this "GUIfied"

---

### Post by bluefrog on 2006-09-05
from nautilus...

---

