---
title: "Getting closer with samba"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by mohnkern on 2007-08-30
Getting very closer with Samba.  I've got unprotected directories working, but password protected directories aren't:

Here's my smb.conf file (with comments)

[global]
	workgroup = CASA
	server string = %h server
	security = SHARE
	encrypt passwords = No
	obey pam restrictions = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[music]
	path = /fs/shared/music
	guest ok = Yes

## The Music Directory Works

[Videos]
	path = /fs/shared/videos
	create mask = 0700
	guest ok = Yes

#The Video Directory works

[michael]
	comment = michael
	path = /fs/michael
	username = michael
	valid users = michael
	admin users = michael
	read list = michael
	write list = michael
	read only = No
	only user = Yes


This share doesn't work.  When I attempt to map to i it It prompts me for a user name and password (like I'd expect) however, when I put in the user name michael, and the password I set with smbpasswd (I even set it with passwd to make sure) , it doesn't work right.

I expect it's probably something at the top, I just don't know what it is.

---

### Post by mohnkern on 2007-08-30
Here's additional information:

mohnkern@Casa-Scott:/fs/michael$ smbclient //127.0.0.1/fs/michael -U michael 
Password: 
Domain=[CASA] OS=[Unix] Server=[Samba 3.0.25a]
Server not using user level security and no password supplied.


I expect it's because I don't have authentication set to USER, but if I do that, then I can't connect to any of the shares.

---

### Post by mohnkern on 2007-08-31
Got it figured out...

---

