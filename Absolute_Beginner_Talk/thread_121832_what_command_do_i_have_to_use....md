---
title: "what command do i have to use..."
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by borisattva on 2006-01-26
.. to copy a large file structure from a locally mounted HD to a remote folder on the network?

cp does not support smb:// as a destination, and mounting the remote folder to a local directory for some reason [mishandles character encoding]("http://ubuntuforums.org/showthread.php?t=120989") so i dont want to risk losing data.

so i need a company i can submit in terminal to copy local directory to smb://directory 

prefferably with an option to skip files alreday existing and identical (i tried via nautilus unfortunatly my connection is not that reliable and lost several times. plucking through 40000 of files is not appealing)

any help is much appreciated.

---

### Post by GreyFox503 on 2006-01-26
You might want to look into the rsync program.  It is used for backing up/synchronising files between two locations (either over a network or locally).  It backs up the smart way by comparing the files on both ends and then transferring only the differences.  (as opposed to tar or cp)

I use it to make local backups (one hard drive to another), so I don't know the details of making it work over a network.  I think you do need to have it running on both machines, though.

A google search for just the term "rsync" produces good results, like this:

[http://www.ss64.com/bash/rsync.html]("http://www.ss64.com/bash/rsync.html")

---

### Post by borisattva on 2006-01-26
thanks greyfox. i have already been recommended this and reading up its documentation..

its options set is way over my head unfortunatley. ext3 is so much more versatile with so many possibilities..

i'm trying to copy a locally MOUNTED NTFS drive  to a network drive which i THINK is actually a linux file system (its netcenter NAS) but supposedly handles NTFS files as-is. i want to copy with a full preservation, no appending or anything, and i want the process to skip files that are already present from previous Nautilus attempt.

can you tell me if this is a correct command? (i cant afford to lose data through trial and error on this)

rsync -W /media/freq smb://freqpreserve

---

### Post by GreyFox503 on 2006-01-26
OK, I've been doing a little reading up on this.  When copying from a local disk to a remote location, you can either use a remote shell program (like rsh or ssh) or you can setup an rsync server on the remote machine.

The syntax for using a shell program is like this:

```
 rsync [option]... Source [Source]... [user@]host:Dest
``` 

Here is one of their examples (for a remote-to-local copy)

> rsync -avz foo:src/bar /data/tmp

this would recursively transfer all files from the directory src/bar 
on the machine foo into the /data/tmp/bar directory on the local machine. 
The files are transferred in "archive" mode, which ensures that symbolic links,
devices, attributes, permissions, ownerships etc are preserved in the transfer. 
Additionally, compression will be used to reduce the size of data portions of the transfer. 
Some useful options I see:

>  -n _ Do a dry-run, show what would have been transferred (_TRY THIS FIRST_!)

-a     _ archive mode  (This is equivalent to -rlptgoD. It is a quick way of saying you want recursion and
want to preserve almost everything.)

-r     _ recurse into directories

-v    _ verbose output

-p    _ preserve permissions

-W   _ copy whole files, no incremental checks

--delete    _ deletes files from the receiving side that don't existing on the sending side 
So you might want to add some more flags to your copy.  I would read the man-page before you use this, and definitely use a dry-run first (with the -n flag).

One last thing:  I don't know about your setup, but you might have to login to the remote machine as in the syntax above.  And I have no idea if you can use the smb:// notation there.

Good luck.


EDIT:  I just thought:  Depending on the speed of your machine, the amount of data to be transfered, and your bandwidth between machines, it could take a long time to calculate what to send.  Whenever you execute this command (even with -n), it first scans the source and destination directories and compares them to make a list of what to copy and/or delete.

---

### Post by borisattva on 2006-01-26
last night it would give me probelms with connection. i wonder if the other system has to be a PC because this is just a hard drive with a nic and it would reject the connect.

i'll give this another shot tomorrow night though. thanks for all your help.

---

### Post by GreyFox503 on 2006-01-27
Oh, I'm not sure I understood your situation.  To use rsync over a network it requires to you connect with rsh, ssh, or with a remote rsync server.  That definitely means whatever's on the other end has to be running one of these programs.

I've never seen a hard drive that plugs directly into a network like that.  If you could mount it onto your filesystem (as in, a folder somewhere below / ), then you could probably use rsync to copy files "locally" from one place to another, and then the operating system would handle the network transfer.

See if you can mount this hard drive onto your filesystem.

---

### Post by jinxed on 2006-03-04
I just purchased this same NAS, and I am having trouble using it as I would like. Here's what I have figured out so far...

A portscan reveals:
```
Port      State   Service
80        open    www - Web Server
111       open    sunrpc - SUN Remote Procedure Call
139       open    netbios-ssn - NETBIOS Session Service
445       open    microsoft-ds - Microsoft-DS
692       open    unknown
1024      open    unknown
2049      open    Network File System - Sun Microsystems
```


I can connect easily to port 80, as would be expected; WD uses this port as its configuration interface.

I'm honestly not sure that I can do anything with port 111.

139 and 445 seem to be samba related. I did successfully set up Samba to access the default 'Shared Files' directory. Copying files straight to that directory is slow... there's got to be a better way.

692 & 1024... ???? any ideas ????

2049... I tried accessing the NAS as an NFS mount, but I consistently get 'Permission denied' errors. It seems I need to know something special to get in that way.

I could not get rsync or any of the r* commands to work. However, I did a google and found that [this guy]("http://my.opera.com/jcwinnie/blog/show.dml/78011") did get rsync to work. I'm waiting to hear back from him on how he did it...

---

### Post by jinxed on 2006-04-01
A couple of things since this last post...

[QUOTE=jinxed]
A portscan reveals:
```
Port      State   Service
80        open    www - Web Server
111       open    sunrpc - SUN Remote Procedure Call
139       open    netbios-ssn - NETBIOS Session Service
445       open    microsoft-ds - Microsoft-DS
692       open    unknown
1024      open    unknown
2049      open    Network File System - Sun Microsystems
```[/QUOTE]
I noticed, once I updated the firmware, that there's a Mac OS NFS service available from the Netcenter's admin web page. No amount of scouring the WD site would turn up any information on actually using it... figures. ](*,) 

[QUOTE=jinxed]I did a google and found that [this guy]("http://my.opera.com/jcwinnie/blog/show.dml/78011") did get rsync to work. I'm waiting to hear back from him on how he did it...[/QUOTE]

I heard back from jcwinnie, who provided me with some good info... The fstab line I used to mount my Netcenter is
```
//wd-netcenter/xxx /mnt/xxx smbfs credentials=~/.xxx,gid=users,dmask=770,fmask=770,rw,user 0 0
```

The main complaint I have with this is that samba can be somewhat slow. The speed can be improved by following the samba docs speed tuning instructions.

Anyways, using ```
RSYNC -a -v --modify-window=10 [target] [source]
```
should now work like a charm...:-D

---

### Post by adamkane on 2006-04-01
You can retain your character encoding if you browse, rather than mount:
Places -> Connect to Server...

You can mount, if you use the correct mount flags:
mount -o nls=utf8 /share /folder

If all else fails, you can convert your filename encodings after you transfer your files:
[http://www.ubuntuforums.org/showthread.php?t=144297](http://www.ubuntuforums.org/showthread.php?t=144297)
```

sudo apt-get install convmv
convmv -f cp850 -t utf-8 -r --notest *.*

```

---

