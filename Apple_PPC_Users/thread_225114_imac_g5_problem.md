---
title: "imac g5 problem"
date: 2006-07-29
forum: Apple PPC Users
---

### Post by guitarjockey1115 on 2006-07-29
OK so i go to disk utility to verify the disk image to see if its ok to burn and i get this.

Verifying volume “Ubuntu_PowerPC_dapper”
Checking HFS volume.
Invalid number of allocation blocks
The volume  needs to be repaired.

Error: The underlying task reported failure on exit


1 HFS volume checked
	Volume needs repair

then it says "the underlying text reported failure on exit".

So then i bunred it to a disc jsut for ufn and it boots the  OS up what nto but it boots it to a blank red screen with the cursor and thats it.

What do I do is it me or is it the file on the servers is bad?

---

### Post by 3rdalbum on 2006-07-29
The Ubuntu CD isn't an HFS-formatted volume, that's probably why Disk Utility is having trouble verifying it. If you want to verify it, check the MD5SUM which is available from the Ubuntu mirrors. (if you used Bittorrent, the MD5s have already been checked for you).

Ignore the next part of the message. Apparantly, Ubuntu just doesn't boot on the iMac G5s.

[SIZE="1"]
Is the date on your computer set correctly? If it's set too far into the past, Gnome will not start up, and you'll get a blank brown screen.[/SIZE]

---

### Post by guitarjockey1115 on 2006-07-29
argh im so confused lol

---

