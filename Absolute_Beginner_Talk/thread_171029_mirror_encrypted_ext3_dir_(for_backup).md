---
title: "mirror encrypted ext3 dir? (for backup)"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by gregconquest on 2006-05-05
Hi,

I have had Ubuntu Dapper Beta on my notebook PC for about two weeks now (installed after a crash -- needed to reinstall Windows -- glad I tried Ubuntu first). Now I am trying to figure out a backup strategy. I have developed a vision of what I'd like to do. Could some of you look over this and give me some feedback, please?

On my desktop PC (no ubuntu installed yet), I'd like to have two directories:
FatDocs (a FAT32 "My Documents", used by both Windows and Linux)
LinDocs (encrypted ext3, mirrored/synchronized with FatDocs)

Windows and Linux apps will share the FatDocs folder. Linux will synchronize the FatDocs and LinDocs directories, then synchronize the encrypted LinDocs directory with a remote host (my gregconquest.com domain via FTP, or google's gdrive, or amazon's S3, etc.)

That's my vision -- now my questions:
1) Can some Linux app (or command line script) easily keep the FatDocs and LinDocs synchronized?
2) Can it also do something similar with a remote host? I think I might actually want three backups -- one always current mirror, and two archives.
3) Can an ext3 directory be encrypted and still appear transparent on my machine to Linux apps (Open Office, Thurnderbird, Firefox bookmarks, etc.)? In other words, if ext3 is capable of encrypting a directory, can I use it as though it were any other directory without noticing the encrypted status?
4) Would such a backup on a remote host be both very secure if hacked/discovered and be easy to restore on my machine from?

Any help, or suggestions for alternatives, would be greatly appreciated.
Greg Conquest

search keywords: backup strategy, archive,

---

### Post by louis_nichols on 2006-05-05
DUDE, that's an ambitious thing! REALLY ambitious!!! Hope it works out. I've never tried any of that, but I think [this esearch]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=encrypted&titlesearch=Titles") on the wiki might be a starting point.

Can I ask why, though, you need an encrypted ext3 setup? Windows can't read it anyway, since it has no drivers.

---

### Post by professor_chaos on 2006-05-05
I cant speak to the ext encryption, but I use "rsync" to sync files on linux-unix-and windows systems. rsync uses "ssh" to do remote communication with *nix systems and I use smb to mount windows directories I wish to backup. So, my scheme is as secure as ssh and smb. To make rsync work without user intervention, you need to use a secure ssh key to store your password. 

I'm sure there's some graphical interfaced backup utility to do this, but I'm happy with rsych. 
Heres an example script I wrote to backup automatically with a cron job.

```
#!/bin/bash

dest=/mnt/driveA/backups/daily/
logpath=${dest}logs/
bkdate=`date +"%y%m%d"`

#options for rsync
rs="rsync -vruL"

#directories to backup and command to backup. Works on links
$rs /home/user/backuplinks $dest > $logpath/daily.$bkdate
```

---

### Post by gregconquest on 2006-05-06
My thanks to both louis_nichols and professor_chaos. 

Louis, thanks for the link. That does help me. And as to why I need an encrypted ext3 setup (which Windows can't read), I *thought* that would be the way to keep my files secure from interception/reading by someone else. It doesn't matter that Windows can't read that directory; it was to be a mirror of the Fat32 Documents folder. Fat32Docs is the working directory for Windows and Linux. The encrypted ext3 directory was to be just there for the purpose of synchronizing -- with both Fat32Docs and with the remote host. Ext3Docs would have been sort of an encrypted gateway.

Yet, per 
[https://wiki.ubuntu.com/CheapSecureEncryptedRemoteVolumeHowTo?highlight=%28encrypted%29](https://wiki.ubuntu.com/CheapSecureEncryptedRemoteVolumeHowTo?highlight=%28encrypted%29) 
[http://tinyurl.com/rckwf](http://tinyurl.com/rckwf)
Ubuntu can mount the remote volume and transparently encrypt everything going there. This obviates the need for the ext3 docs directory, it seems. I'll work more on this -- and report back if and when I find something interesting.

Thanks again,
Greg Conquest

---

