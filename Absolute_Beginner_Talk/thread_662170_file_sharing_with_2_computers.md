---
title: "file sharing with 2 computers"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by metalpancake on 2008-01-08
Hi. I was wondering if it is possible to share files between 2 Ubuntu Gutsy systems over a Lan.
Thanks.

---

### Post by Pevichaey5 on 2008-01-08
it is

the internet is just like a global network, you could install apache on the Linux computers, using ftp, but i am sure there are simpler ways to sharing files

---

### Post by metalpancake on 2008-01-08
I heard that you can use Samba, but I don't know any more than that.

---

### Post by bodhi.zazen on 2008-01-08
You can use samba or nfs

Samba : [https://wiki.ubuntu.com/ComprehensiveSambaGuide](https://wiki.ubuntu.com/ComprehensiveSambaGuide)

Nfs : how-to:[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

You can also use ssh : (sshfs) [http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html](http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html)

Apache is likely "overkill"

ftp should only be used if you know how to secure it (vsftp or sftp).

---

### Post by metalpancake on 2008-01-08
Which would  you say is better? Apparently Samba can network windows machines too.:)

---

### Post by PetePete on 2008-01-08
samba is normally used for windows shares... and has been reported as sometimes slow on linux for large files.

if the two hosts are linux then use Nfs as the simplest way.

---

### Post by metalpancake on 2008-01-08
When I followed the tutorial and tried to input:
```
$ sudo apt-get install samba smbfs
$ sudo mkdir -p /media/winshares
$ sudo addgroup smb
$ sudo adduser $USER smb 
```:confused:

It tells me 'command not found'
Maybe nfs woluld be better:)

---

### Post by Hospadar on 2008-01-08
I like ssh, it's really easy to setup, it pretty much always works (just make sure port 22 is open, and if you are behind a router, foreward the port to the machine you want to be visible to the internet.

It's nice because it not only allows you to transfer files (graphically if you want, with a client like filezilla or gftp) but you can also remote control the machine by command line, and even open up graphical apps on the other machine (which you can even do in windows)

Also ssh is secure unlike ftp, which is of course a plus.
samba and nfs are nice as well, but can be a little tougher to set up, and also arn't accessible outside your local network.

---

### Post by bodhi.zazen on 2008-01-08
> **metalpancake said:**
> When I followed the tutorial and tried to input:
```
$ sudo apt-get install samba smbfs
$ sudo mkdir -p /media/winshares
$ sudo addgroup smb
$ sudo adduser $USER smb 
```:confused:

It tells me 'command not found'
Maybe nfs woluld be better:)

Of the two, samba is best if you share with windows.

Put the commands in without the $

> sudo apt-get install samba smbfs
sudo mkdir -p /media/winshares
sudo addgroup smb
sudo adduser $USER smb 

Well, leave the $ with $USER

---

### Post by Demosthenesaus on 2008-01-08
so is NFS or Samba better between Linux machines?  I have another Ubuntu laptop I want to share with, I presume NFS is better then.

---

### Post by metalpancake on 2008-01-08
I did what you said, but:
```
The following packages will be upgraded:
  samba-common smbclient
2 upgraded, 2 newly installed, 0 to remove and 73 not upgraded.
Need to get 12.0MB of archives.
After unpacking 10.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

```
Why abort?  :mad:

---

### Post by bodhi.zazen on 2008-01-09
> **metalpancake said:**
> I did what you said, but:
```
The following packages will be upgraded:
  samba-common smbclient
2 upgraded, 2 newly installed, 0 to remove and 73 not upgraded.
Need to get 12.0MB of archives.
After unpacking 10.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

```
Why abort?  :mad:

No idea. Looks like you system may not be up to date and there may be some conflicts or missing packages.

Try ```
sudo apt-get update
sudo apt-get upgrade
```

Then re-try

> **Demosthenesaus said:**
> so is NFS or Samba better between Linux machines?  I have another Ubuntu laptop I want to share with, I presume NFS is better then.

sshfs is very easy, nice, and very secure.

NFS is easy to set up, but least secure of the 3.

samba is not too hard to set up and has more security then nfs but not as much as sshfs.

---

### Post by airtonix on 2008-01-09
I notice you asked how to share files between two linux machines in a **LAN**. and not between machines over the internet.

The install aborted because you most probably pasted several commands at once.
(when you were required to press Y, the next command intervended and the installer interprets anything other than Y as a N)

do them one at a time.

And yes use NFS.

NFS is faster than samba. : 

NFS: 600mb in 5min
SAMBA : 600mb in 15min

---

