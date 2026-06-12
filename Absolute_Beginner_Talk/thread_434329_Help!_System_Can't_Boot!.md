---
title: "Help! System Can't Boot!"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by skrimpy on 2007-05-05
I was typing an article when my system completely froze.  I rebooted the computer and now I get this error:

 ```
dev/sda2 contains a filesystem with errors
```

and a whole bunch of stuff about forced checks and then that automatic filesystem checks failed.  I get told I'm in read-only mode and booted to a root prompt in the command line.  I'm told just before that that apt-get doesn't exist and indeed it seems almost everything doesn't exist.  

My basic filesystem is still there but something appears to be hosed.  Please help.  I am really really worried about this.  I hadn't done a backup of my system yet this week and I did a lot of work.  If it is hosed I am screwed.

All attempts to log into a recovery mode also fail.  Help.

---

### Post by Happy_Man on 2007-05-05
Ow. That burns. I'm pretty sure the only thing you can do at this point is reinstall. Hopefully, you have a /home partition... if you don't, make one when you're reinstalling.

---

### Post by srt4play on 2007-05-05
I will suggest booting with your ubuntu cd and fsck it from a terminal.

sudo fsck /dev/sda2

---

### Post by skrimpy on 2007-05-05
> **srt4play said:**
> I will suggest booting with your ubuntu cd and fsck it from a terminal.

sudo fsck /dev/sda2

I get this:

```
 [ 1103.062397} Buffer I/O error on device sda2, logical block 6029378
Error reading block 6029378 (Attempt to read block from filesystem resulted in hort read) while doing inode scan.  Ignore error<y>? yes

Force rewrite<y>?
```


And my system is hanging there.

Should I tell it yes?

If this does mean I need to reinstall does anyone know if there is any way I can mount an external hard drive while it is in this state and backup my home folder?

---

### Post by speedygeo on 2007-05-06
I have the same problem!!!!
URGENT!!
I cant reinstall!](*,)

---

### Post by hessiess on 2007-05-06
has your hdd died? if you carnt reinstall it sounds like a posabilaty?

better educated people corect me if im wrong

---

### Post by skrimpy on 2007-05-06
well in case this is helpful, though it represents a security breech imho, I was able to get my files.  This was very easy for me because my filesystem is tailored for easy backup.  And when I get this sorted out I think I'll go for daily backups and I'm going to figure out how to lock up this security issue.  Though I'm thankful for it right now.

I was able to log in using the Live CD and mount my Ubuntu filesystem.  I then changed to root in a terminal and changed permissions on my home directory (and also my www directory where my websites mirror on localhost).  I was then able to mount an external harddrive and transfer my files to that from the livecd.  

I don't know if I ought to have been able to do this so easily as it does seem a security breech but right now I'm grateful for it. 

I think my problem is my harddrive.  My computer must have tried to write to a bad sector.  With my files backed up I have no problems reinstalling, which I'll do and backup viligently while I wait for my new harddrive to come in m(_ _)m.  Then I'll do daily backups and put a boot password on my system m(_ _)m

---

### Post by srt4play on 2007-05-07
I have a couple of thoughts on your experience.  About the "security breech", keep in mind that once someone has physical access to the machine there pretty much is no security except maybe filesystem encryption and a lock on the case. Check the website of your hard drive's manufacturer for maybe a diagnostics boot disk or some tools you can use to figure out if the drive is salvagable.

---

