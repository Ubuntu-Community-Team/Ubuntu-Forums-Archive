---
title: "To defrag or not???"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by Brigrat on 2006-01-31
As I am new to this world of Ubuntu.  Is there such a thing in Linux as the old M$ defrag???  I have got my machine running and want to delete some programs that are needed as I have found replacement for.  Any Help????

---

### Post by tntc1978 on 2006-01-31
Ubuntu does this automatically everey 30 times you boot. And it's quite fast compared to M$.

---

### Post by xXx 0wn3d xXx on 2006-01-31
you don't need to defrag, the filesystem for ubuntu is way more efficent then windows and it is designed to minimize fragmention.

---

### Post by mstlyevil on 2006-01-31
[QUOTE=Brigrat]As I am new to this world of Ubuntu.  Is there such a thing in Linux as the old M$ defrag???  I have got my machine running and want to delete some programs that are needed as I have found replacement for.  Any Help????[/QUOTE]

All file systems fragment to one degree or another. It is not neccesary to defrag Linux because the fragmentation hardly affects performance and it just does not fragment to the degree of Windows.

---

### Post by kewl1uk on 2006-01-31
[QUOTE=tntc1978]Ubuntu does this automatically everey 30 times you boot. And it's quite fast compared to M$.[/QUOTE]

I was wondering about that. It happened to me tonight when on reboot a text screen came up saying that I hadn't done something-or-other for 30 boots and it was going to force it - can't remember exactly what that something-or-other was. But after that it booted and the screen resolution was completely messed up with everything big. But on reboot again everything was back to normal. Is it actually supposed to do that?

---

### Post by mstlyevil on 2006-01-31
[QUOTE=tntc1978]Ubuntu does this automatically everey 30 times you boot. And it's quite fast compared to M$.[/QUOTE]

Bulls**t!

---

### Post by AmboyGuy on 2006-01-31
fsck is like Scandisk in windows
From the 'man fsck' page > NAME
       fsck - check and repair a Linux file system

SYNOPSIS
       fsck [ -sAVRTNP ] [ -C [ fd ] ] [ -t fstype ] [filesys ... ] [--] [ fs-
       specific-options ]

DESCRIPTION
       fsck is used to check and optionally repair one or more Linux file sys&#8208;
       tems.   filesys  can  be  a device name (e.g.  /dev/hdc1, /dev/sdb2), a
       mount point (e.g.  /, /usr, /home), or an ext2 label or UUID  specifier
       (e.g.   UUID=8868abf6-88c5-4a83-98b8-bfc24057f7bd or LABEL=root).  Nor&#8208;
       mally, the fsck program will try to  handle  filesystems  on  different
       physical  disk  drives  in  parallel to reduce the total amount of time
       needed to check all of the filesystems.
 
It will report the amount of fragmentation but not de-frag.
So every 30 reboots the system runs fsck and generates a report, it doesn't attempt to fix anything.

---

### Post by tc10b on 2006-02-07
Hi I know this is slightly off topic but I installed Ubuntu on my laptop and have been using it fine for about a week.

Now whenever it boots it tells me that it has to run a check of some kind. When it does this it continuously comes up with the error message:

Buffer I/O Error /hda

I know my hard disk is fine because windows runs fine.

I don't know how to stop it and get into Ubuntu. :confused:  Can anyone help me?

---

