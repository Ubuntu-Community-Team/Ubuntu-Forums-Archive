---
title: "pulling information from a crashed hard drive.......how to??"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2007-05-19
Hi:

My problem is that I am attempting to get emails from a hard drive I previously used on this computer. I removed that drive - which was running Breezy if I remember right - and installed a new drive and OS... being Edgy Eft. This system runs fine for the most part except for the occasional problems that need to be tweaked.

What I have not been able to do is read any data from the hard drive that was loaded with Breezy - the drive I removed last year after I could no longer boot from it (this occurred after I attempted to reinstall some archived files . . . doing this seems to have caused the hard drive to crash).

At this moment, I have the hard drive - I will call it the Breezy hard drive for simplicity - hooked to this computer via a PCI/IDE connector.

When I boot this computer from its Edgy Eft hard drive, the Breezy hard drive shows up as the hde drive with partitions hde1, hde2, hde5 ... normal, right? for a hd with the Ubuntu/Linux system loaded on it.

Anyway, I cannot mount any of the partitions from the Breezy drive even though they show up in the /dev/ folder.

I thought, perhaps, that booting from a Knoppix CD would allow me to peruse the Breezy hard drive - but the only drive partition that shows up is hde1 and when I click on that using the Knoppix desktop browser thing I get nothing - well, a lost + found folder, actually. But that's it. The hde2 and hde5 drives do not show up in Knoppix.

Now, perhaps you are asking why I don't try to find the email I need from the backup discs - well, the problem is it was doing this kind of thing which caused the Breezy computer to crash in the first place.

Also, I cannot remember - but it seems Breezy and/or Hoary used a different email program than Evolution?? I'm not sure - I searched for an answer on the Net but did not find one.

Ok, that's enough for now. If anyone can post help, links, whatever I will really appreciate it. I might need these emails in a legal action so they are important.

Thank you for your time and assistance in advance.

--GM

---

### Post by Happy_Man on 2007-05-19
Hmmm.... what errors does it give when trying this command in terminal:

```
mkdir /media/test
mount /dev/hde5 /media/test
```?

---

### Post by GMachine_24 on 2007-05-19
Hi:

Thank you for your prompt reply.

The computer creates the directory

/media/test

without a problem. Then:

<start code>

user@computer:/$ sudo mount /dev/hde5 /media/test
/dev/hde5 looks like swapspace - not mounted
mount: you must specify the filesystem type
user@computer:/$ 

<end>

Question: Are the email files I want on the hde5 partition? I, obviously, am pretty new at this.

Again, thank you for your help.

--GM

---

### Post by Happy_Man on 2007-05-19
Ah, sorry, no they're not, that's the old swap partition. Try
```
mount /dev/hde2 /media/test
```

---

### Post by GMachine_24 on 2007-05-19
This is the result:


<begin>

user@comp:~$ sudo mount /dev/hde2 /media/test
mount: you must specify the filesystem type
user@comp:~$ 

<end>

If it's any help, I heard the hd discs start spinning when I entered the command.

--GM

After reading up a bit on the mount process,  I believe the command must be in the form:

[B]
sudo mount -t ext /dev/hde2 /media/test[/B]

(w/out the bold) where 'ext' is the type of partition - in this case, hde2 is an extended partition - however I cannot figure out what to put where the 'ext' is to delineate the partition as extended. I tried "extended", "ext" "Extended" "ext3" ... none of which worked.

E.G.:

<begin>

user@comp:~$ sudo mount -t ext /dev/hde2 /media/test
mount: unknown filesystem type 'ext'
user@comp:~$

<end>

---

### Post by GMachine_24 on 2007-05-19
After doing some research, I attempted to mount the partition using ext2 for the partition type, which I believe is correct. This is what I got:

<begin>

user@computer:~$ sudo mount -t ext2 /dev/hde2 /media/test
mount: wrong fs type, bad option, bad superblock on /dev/hde2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
user@computer:~$

<end>

So I decided to check the dmesg file and found this

<begin>

user@computer:~$ dmesg | tail
[ 8805.395491] attempt to access beyond end of device
[ 8805.395528] hde2: rw=0, want=4, limit=2
[ 8805.396713] EXT3-fs: unable to read superblock
[ 9828.126887] cramfs: wrong magic
[ 9828.130416] attempt to access beyond end of device
[ 9828.130580] hde2: rw=0, want=4, limit=2
[ 9828.130898] EXT3-fs: unable to read superblock
[10247.165617] attempt to access beyond end of device
[10247.165647] hde2: rw=0, want=4, limit=2
[10247.167411] EXT2-fs: unable to read superblock
user@computer:~$

<end>

As a result, I decided to check for bad blocks by using this command:

<begin>

user@computer:~$ sudo badblocks /dev/hde1

<end>

And, apparently, this process is still running.

If bad blocks are found, there is information how to hide/fix the problem on this url:

[http://linux.about.com/od/linux101/l/blnewbie5_13.htm](http://linux.about.com/od/linux101/l/blnewbie5_13.htm)

If anyone knows of another way or if this is a bad idea, please let me know ASAP.

Thanks.

GM

---

### Post by Happy_Man on 2007-05-19
No, it said... you were trying to mount an extended partition, instead of the logical inside. Kill the bad block search and try to mount /dev/hde3.

---

