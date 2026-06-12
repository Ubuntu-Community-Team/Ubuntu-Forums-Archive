---
title: "Rm -R deleting stuff...."
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Julolidine on 2006-12-03
Well, I think I made a little booboo, and I don't know what to do.

Anyways, I was following the directions to mount an FTP site 

[http://www.ubuntuforums.org/showthread.php?t=53480&highlight=mount+FTP](http://www.ubuntuforums.org/showthread.php?t=53480&highlight=mount+FTP)

with LUFS.  

so I wanted to see if everything was in its right place, and I did something like
 sudo lufsmount ftpfs://xxx:xxxx@192.168.1.68 /mnt/test/


then I saw it worked, so I wanted to make it to a more normal name

so I typed

sudo rm -r /mnt/test/

instead of unmounting it.  Then I heard my network drive chunking away, so I immediately killed it.

Did I remove stuff from my network drive via sudo rm -r?

I killed it almost instantly, but I'd like to either find out what I deleted if I deleted stuff, or undelete what I did delete if possible.  :confused: :confused: :confused: 


I know dumb mistake, and I realized it almost immediately, but I'm still new-ish here.

---

### Post by KhaaL on 2006-12-03
ouch... well, if you logged in with write permission then yes, you might very well have erased some data. anyhow, all hope is not lost because there are some live CD's out there that does restore deleted files (delted files arent really deleted, merely marked as deleted so future data can replace them). 

The most important question however is, what type of filesystem were those deleted files on?

---

### Post by Julolidine on 2006-12-03
It would be FAT-32, is there anyway of telling what was deleted?  I can see that all of the major folders that were there before are still there, but..... I don't know about individual files.  

Theres a lot of files on the drive (250GB) and lots of folders that include pictures and so on, so I can't even figure out what is gone.  

Nothing is in the trash bin.  If I log in on windows (its a dual boot) can I try some sort of recover file option?  I have written nothing to it in the meantime, so fingers crossed.  

](*,)

---

### Post by KhaaL on 2006-12-03
erk! you shouldn't boot the computers OS on which the hard has been erased, that could risk getting more data being lost as it writes to its pagefile.

I admit I have no idea what recovery tools there are for linux, but two live CD's that comes to mind that *might* help you is System rescue CD and Hirens CD (I used hirens CD before and I can say from experience that it will help you in this task).

good luck, and hopefully a linux guru will give you a more appropiate answer :)

---

### Post by Julolidine on 2006-12-03
Well the thing is once again, this is a mounted FTP network drive - so its not exactly clear in my mind the OS where the 'deletion' would be tracked.  

I'll keep this computer turned on though, however, I have another computer that I can use to scan it.  Does it do some sort of journaling on the computer that tracks what's been deleted?

---

### Post by KhaaL on 2006-12-03
> **Julolidine said:**
> Well the thing is once again, this is a mounted FTP network drive - so its not exactly clear in my mind the OS where the 'deletion' would be tracked.  

I'll keep this computer turned on though, however, I have another computer that I can use to scan it.  Does it do some sort of journaling on the computer that tracks what's been deleted?

So it's a stand-alone network drive? then you can mount it again as read-only and you'd be pretty safe scanning it. 

And I don't think that FAT32 do journaling, nor does linux keep a log of deleted files (unless you'd use the -v switch which gives feedback to the console on whats being deleted).

---

