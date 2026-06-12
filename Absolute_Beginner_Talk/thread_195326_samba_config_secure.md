---
title: "samba config secure?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by DaBigUA on 2006-06-12
Hello.  I finally figured out how to let the family's WinXP systems around the house visit some shared directories on my computer while I am running Dapper.  Most shares are on mounted NTFS volumes.  After trying the GUI configuration tools, in the end I sort of remade my smb.conf file from scratch.  The problem is it's pretty simple-minded. I don't know if I have left a huge security hole.  All the shared directories are read-only, and my LAN sits behind a Linksys router.  Do I have major security concerns, or can I run with this configuration?  Any replies appreciated.

```

[global]

	encrypt passwords = yes
	netbios name = HADES
	security = share
	socket options = TCP_NODELAY IPTOS_LOWDELAY
	wins support = yes
	workgroup = OLYMPUS

[public]

	path = /home/andrew/MyShare
	read only = yes
	guest ok = yes

[MUSIC]
	path = /media/win_music/Music
	read only = yes
	guest ok = yes

[TV]
	path = /media/win_tv/TV
	read only = yes
	guest ok = yes

[CARTOONS]
	path = /media/win_tv/cartoons
	read only = yes
	guest ok = yes

```

---

### Post by gerbman on 2006-06-13
[QUOTE=DaBigUA]Hello.  I finally figured out how to let the family's WinXP systems around the house visit some shared directories on my computer while I am running Dapper.  Most shares are on mounted NTFS volumes.  After trying the GUI configuration tools, in the end I sort of remade my smb.conf file from scratch.  The problem is it's pretty simple-minded. I don't know if I have left a huge security hole.  All the shared directories are read-only, and my LAN sits behind a Linksys router.  Do I have major security concerns, or can I run with this configuration?  Any replies appreciated.

```

[global]

	encrypt passwords = yes
	netbios name = HADES
	security = share
	socket options = TCP_NODELAY IPTOS_LOWDELAY
	wins support = yes
	workgroup = OLYMPUS

[public]

	path = /home/andrew/MyShare
	read only = yes
	guest ok = yes

[MUSIC]
	path = /media/win_music/Music
	read only = yes
	guest ok = yes

[TV]
	path = /media/win_tv/TV
	read only = yes
	guest ok = yes

[CARTOONS]
	path = /media/win_tv/cartoons
	read only = yes
	guest ok = yes

```[/QUOTE]If they're all read-only then it seems safe enough. If you were to make them read-write then I would set the security option to "user" in your smb.conf file. You could also install the firestarter firewall for additional security (super easy and in the repositories).

---

