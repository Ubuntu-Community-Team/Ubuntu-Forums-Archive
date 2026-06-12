---
title: "TimeMachine Backup with ubuntu and smb share"
date: 2012-02-04
forum: Apple Hardware Users
---

### Post by winniwinter on 2012-02-04
Hi,

I have a little problem configuring my ubuntu server for backing up my mbp with lion and time machine.

First of all I should say something about my setup. 

Server: old WHS with VMWare running ubuntu 11.10
client: Macbook Pro OSX Lion

I started with an Windows HomeServer to Backup my windows machines and used it as a fileserver (I mean the old WHS Version not 2011). After some time I wanted to get to know linux a little bit better. That's when I installed vmware vSphere and installed ubuntu in a small vm. 
This works pretty good. I installed different services which are pretty cool and stable.
Now I found out that it's possible to configure ubuntu for the TimeMachine backup. 
The main problem is, that the vm where ubuntu is running on has not very much disk space. That's why I mounted a smb share on ubuntu (/media/tm_backup) which I wanted to use for my TM backup. I set the permissions for files+folders to 777
The volume shows up on my mbp(lion) but when I start the backup it says:

> 
Make sure your computer and the backup disk are on the same network, and that the backup disk is turned on. Then try again to back up.I changed the location to the local file system (/backup/tm) and this worked.

Is it not possible to use a mounted volume in ubuntu for the time machine backup?

Logs on my mbp say:
> 
04.02.12 14:28:10,615 com.apple.backupd: Mounted network destination at mountpoint: /Volumes/winniTimeMachine using URL: afp://daniel@ubuntu.local/winniTimeMachine
04.02.12 14:28:28,461 com.apple.backupd: Creating disk image /Volumes/winniTimeMachine/winniMBP.sparsebundle
04.02.12 14:29:03,434 com.apple.backupd: Backup failed because the network destination disk was ejected or disconnected unexpectedly!
04.02.12 14:29:04,446 com.apple.backupd: Error 57 creating backup disk image
04.02.12 14:29:04,446 com.apple.backupd: Failed to create disk image /Volumes/winniTimeMachine/winniMBP.sparsebundle, status: 57
04.02.12 14:29:05,452 com.apple.backupd: Backup failed with error: 26
Pls help! :)

---

### Post by deba on 2012-02-04
Maybe some of this info may be of use to you?

[http://www.pronetworks.org/forums/configuring-ubuntu-to-store-time-machine-backups-t109371.html](http://www.pronetworks.org/forums/configuring-ubuntu-to-store-time-machine-backups-t109371.html)

[http://www.tristanwaddington.com/2011/07/debian-time-machine-server-os-x-lion/](http://www.tristanwaddington.com/2011/07/debian-time-machine-server-os-x-lion/)

---

### Post by xdracco on 2012-09-24
you won't be able to use TimeMachine if you're using an SMB volume. You'll need to use Netatalk as netatalk has a time machine specific parameter for the volume you want to use. Just FYI....

---

### Post by svenole on 2012-10-26
I've used TimeMachine as a backup device for my Linux (ubuntu) laptop using SMB for a long time. This has worked flawlessly. However, after upgrading to 12.10, I've got into trouble. I use SBackup. In 12.10 it stops in the middle of the backup session with an "STARTTLS not sent" error message. Several GB of data has been transferred before this happens. This indicates that something happens during the session that destroys the SMB session and it is consistent ( happens every time ). I assume that there is a config issue someware, but I have not been able to fint it yet. 


- Sven

---

### Post by svenole on 2012-10-26
Actually i found that the backup process from SBackup on an ubuntu 12.10 laptop also worked perfectly well. The error I saw was from the process of sending the log of the backup process by email to myself where the email information provided to SBackup was wrong so that it could not contact the smtp server. 

So the conclusion is that SMB connection from ubuntu 12.04 and 12.10 to Time Machine works as a charm.

---

