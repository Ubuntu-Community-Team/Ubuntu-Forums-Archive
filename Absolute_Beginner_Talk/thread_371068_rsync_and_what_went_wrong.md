---
title: "rsync and what went wrong?"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2007-02-26
Having searched and looked at a number of sites re 'rsync' I finally decided to try the method outlined at 'Psychocats.net' With a 1GB Usb 'Netac OnlyDisk' I mounted the usbdisk and it was recognised as /dev/sda and also as /media/usbdisk. I copied the instructions  but changed the details as follows ```
rsync -av /home/harry /media/usbdisk
``` (harry being the file I wanted to backup). The process started but a number of files failed to backup. When finished I went into the usb disk and there was nothing (empty) but on checking the properties of the disk there was now only 907MB left. One other thing was I no longer owned the disk (permissions) and could do nothing with it. I have subsequently reformatted the disk and I now re own it and have successfully copied my home directory to it manually. This I knew how to do anyway. My question if there is a answer, is what went wrong and how do I use rsync in future?
regards

---

### Post by highneko on 2007-02-26
Seems to me like you were trying to copy a directory to a new directory. What maybe I would have done is used a wildcard if that is in fact a directory.

Maybe this?
```
rsync -av /home/harry/* /media/usbdisk
```

---

### Post by Sbarton on 2007-02-26
Hello highneko, my file /folder ' harry' is on my home partition. That is the reason for the code used. Maybe it should just have been ?
```
rsync -av harry /media/usb
```
would that have been better?
regards

---

### Post by highneko on 2007-02-26
Hello. I'm not exactly sure as I have only used rsync a few times before myself. But I would suggest using a wildcard which expands to the names of all files and folders in your home folder when used the way I suggested. Maybe make folders and files for testing rsync so nothing bad happens.

```
[COLOR="DimGray"]# Another way might be to specify a new folder like this:[/COLOR]
rsync -av /home/harry /media/usbdisk/harry
[COLOR="DimGray"]# Or give it a new name maybe:[/COLOR]
rsync -av /home/harry /media/usbdisk/newname
```

Edit: Here's another example which might help:
```
mkdir -p ~/TeStA/a/b/c ~/TeStB; rsync -av ~/TeStA/* ~/TeStB
mkdir -p ~/TeStC/a/b/c ~/TeStD; rsync -av ~/TeStC/* ~/TeStD/newname
```

---

### Post by Sbarton on 2007-02-26
Yes! that may be a better option, as well as experimenting. So has your experience with rsync been without problems? Perhaps you could supply an example that has worked!
regards

---

### Post by highneko on 2007-02-26
I made an edit which has a nice example. I have a local private html page where I keep all my notes. Here's the notes I have when I used rsync last:
```
rsync -rvu --delete /var/www/* root@192.168.0.111:/var/www
rsync -rvu --delete --exclude 'error_report.txt' /var/www/* root@192.168.0.111:/var/www
```
I forget what it does tho. It'll probably kill something. n_n

---

### Post by Brunellus on 2007-02-26
> **Sbarton said:**
> Yes! that may be a better option, as well as experimenting. So has your experience with rsync been without problems? Perhaps you could supply an example that has worked!
regards
rsync is my single most favorite command, ever.

1)  If you have been deleting files on the USB device, be advised that Nautilus does not delete them, but rather moves them to a .trash directory on the device.  Removing that directory manually (from the command line) with 

rm -r .trash

will free up the space that you need.

2)  rsync is sensitive to trailing backslashes in the source argument:

[http://www.mikerubel.org/computers/rsync_snapshots/#Rsync](http://www.mikerubel.org/computers/rsync_snapshots/#Rsync)

personally, I'd have used

rsync -av /home/harry/ /media/usbdisk

which should have backed things up to 

/media/usbdisk/harry

be *very careful* when using the --delete option.  

You might also want to consider unison for syncronizing two directories.

---

### Post by Sbarton on 2007-02-27
OK! Thanks to you all for your input, I am going to learn from those and practice. Thanks for suggestions.
regards:)

---

### Post by Sbarton on 2007-02-27
Success with ```
rsync av /home/harry/ /media/usb
```. It seems the extra backslash after 'harry' appears to have done the trick. There was though some failings (see attachment).
Just a couple of more questions if you do not mind answering Brunellus.
1. What did the extra backslash mean in the argument that made it succeed?
2. If I type the same code again will rsync save just the changes in the home/harry folder?
3. If you can make out the attachment failings why did that happen?
Thanks for your time and expertise.
regards

PS: This has been an instructive lesson using rsync, and amazed me at the speed that it ran at. If I can get the incrementals to work as well then it is a great backup program.

---

### Post by Sbarton on 2007-02-28
To answer my own No.2 question, I tried it and it did not save additional changes as I hoped. Oh! well back to the drawing board to try to figure it out. I have tried to make some sense of the 'mikerubel' site, it's obviously me, but I'll keep trying.
regards

---

### Post by Sbarton on 2007-02-28
Well this is the latest! I installed 'grsync' as suggested in one post. I have now tried 3 backups using 'grsync' where I have added just 1 extra file each time in the 'source'. Each backup saved the changes in the 'source' to the 'destination'.:lolflag: So this suits me at present. I will struggle on with 'rsync' to improve my knowledge. However, I would add that the GUI method for me is better. I would hazard a guess that it's the same for many others. It's great knowing the terminal language but that's just it 'KNOWING'. Even after a year with linux I am still struggling. Maybe a age thing or to many years just clicking the mouse. Nothing wrong with that though!!
regards

---

### Post by kinson on 2008-01-13
> **Brunellus said:**
> rsync is my single most favorite command, ever.


be *very careful* when using the --delete option.  

You might also want to consider unison for syncronizing two directories.

I love rsync a lot too, since I'm crazy about data backups...I value my photos a lot.

I face the usual problem with anybody who fools around with an external hdd backup (I think). I don't know what to format it to. 

1) NTFS, I'm not too trusting of ntfs-3g..some people say its a little dangerous
2) FAT32, no files bigger than 4gb(though I'm not sure if I have any), but mainly there is some problem with the timestamps I believe between rsyncing from ext3 to FAT32, as it copies everything over again
3) ext3, I'll have problems sharing my stuff/backups with other people. But I'll just carry around the ext3 read installer for windows :p

That said, I'll probably format my backup external drive to ext3.

I currently use this to backup my stuff:
```

rsync -av /sourceEXT3folder /destNTFSfolder/ > report.log

```

but was thinking of adding the '--delete' flag in the future, as I don't wanna leave stuff that I've already deleted...it'd be kinda stupid. I just wanted to ask, whats the danger of using the --delete flag? i don't wanna suddenly wipe everything from my drives, as I only keep 2 copies - the originals, and the backups on the external.

much thanks in advance :)

Btw, I was trying to backup today, and I got this error, any idea?
```

kinson@kinbuntu:~/Desktop$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3             266G  232G   21G  92% /
varrun                506M   76K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  128K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M  9.3M  497M   2% /lib/modules/2.6.15-29-386/volatile
/dev/sda2             5.9G  3.5G  2.5G  59% /media/bridge
/dev/sdb1              15G   15G  165M  99% /media/usbdisk
/dev/sdb5             219G  211G  7.7G  97% /media/New Volume
/dev/sda1              20G   16G  4.2G  79% /tmp/disks-conf-sda1
kinson@kinbuntu:~/Desktop$ rsync -av /home/kinson/Data/ /media/New\ Volume/Data\  130108/ > /home/kinson/Desktop/DataBackup130108.log
rsync: writefd_unbuffered failed to write 4 bytes: phase "unknown" [sender]: Bro ken pipe (32)
rsync: write failed on "/media/New Volume/Data 130108/Backup_Backup/Comics/Spide rman/Ultimate Spiderman/Ultimate Spiderman #013.cbr": No space left on device (2 8)
rsync error: error in file IO (code 11) at receiver.c(291)
rsync: connection unexpectedly closed (1432059 bytes received so far) [generator ]
rsync error: error in rsync protocol data stream (code 12) at io.c(434)
rsync: connection unexpectedly closed (148608 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(434)
kinson@kinbuntu:~/Desktop$

```

Cheers,
Kinson

---

