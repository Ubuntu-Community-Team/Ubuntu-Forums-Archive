---
title: "Hard drive not showing full capacity"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Tom Brokaw on 2006-08-10
This is a 250 GB Maxtor, freshly formatted as ext3.  Capacity is shown as ~233 GB.  I created a mount point called /media/data, thanks to Catlett.  When I open "data" however, it only shows ~218 GB free.  I actually do need those 15 GB.  Any ideas?

Thanks.

---

### Post by UltraMathMan on 2006-08-10
Hard drives generally don't give you what they say the do, my 100GB drive has something like 91GB available - not sure why that is, or where the rest of it goes but I think they should be marketed as size usable rather than the way they are now.

---

### Post by BitTorrentBuddha on 2006-08-10
The size on the box is what it would be if a gigabyte were 1000 megabytes (it's actually 1024 megabytes.) Therefore if you have a 300 "gigabyte" hard drive according to your box to find out how much you have to do 300*1000/1024 and it comes out to 292.96875, but there's no way you should be missing 32 gigabytes...

---

### Post by Tom Brokaw on 2006-08-10
Right, I'm aware of the difference between marketing's GBs and engineering's GBs.  The actual capacity should be ~233, and that's what it showed (I forget where) before I mounted it.  The only thing I did was create a permission for it, and now "data" is only showing 218 GB.

Thanks for the replies.

---

### Post by jd65pl on 2006-08-10
My hard drive did that once, it wrote zero data on empty blocks which made my drive look more "used" than it was originally, I couldn't find a way to fix this and ended up reformatting

---

### Post by Tom Brokaw on 2006-08-10
OK, here are some screenshots.  I really don't get this, as the drive is listed as "233.8GB Volume" - but then the properties only show 218 free.  I'll try a reformat, as there is nothing on there right now anyway.

Edit: Why would ~4 GB be used, as per the gparted screenie, on a brand new format?  That's about as much as an OS install.  Is that standard for drives of this size?

---

### Post by Metacarpal on 2006-08-10
Open your Data partition in Nautilus and hit Ctrl+H.  Trash folder?

---

### Post by Tom Brokaw on 2006-08-10
OK, reformatted, set permissions again, exact same result, which is at least consistent.

Here's a link to a "normal" size discrepancy explanation:
[http://www.diskview.com/disk-size-discrepancy.htm](http://www.diskview.com/disk-size-discrepancy.htm)

That page gives the magic number by which to divide as 1073741824, and indeed, dividing 250,000,000,000 by 1073741824 gives 232 GB and change.

So I'd like at minimum to regain the "missing" 11 GB, and at best to also regain the 3.79 GB showing as used in the gparted screenshot.

---

### Post by Tom Brokaw on 2006-08-10
> **Metacarpal said:**
> Open your Data partition in Nautilus and hit Ctrl+H.  Trash folder?

Same thing.

---

### Post by jeffathehutt on 2006-08-10
In Linux, some of the hard drive space (5% by default) is reserved for the root user.  It's possible the missing space is actually the reserved space.

---

### Post by Tom Brokaw on 2006-08-10
> **jeffathehutt said:**
> In Linux, some of the hard drive space (5% by default) is reserved for the root user.  It's possible the missing space is actually the reserved space.

Is there a way to change the amount reserved?

---

### Post by jeffathehutt on 2006-08-10
I haven't tested this command, so don't trust it.  Check the man page for mke2fs for more information.  The -m option specifies how much should be reserved.

mkfs.ext3 -m 0 /dev/hdb1

---

### Post by Tom Brokaw on 2006-08-10
OK, I tried that, but it said the drive was already mounted and it would not create a filesystem here.  I unmounted it and tried it again and it said "Permission denied while trying to determine filesystem size"

Seems like this might be the right track, though, thanks.

---

### Post by Third Thoughts on 2006-08-10
> **Tom Brokaw said:**
> OK, I tried that, but it said the drive was already mounted and it would not create a filesystem here.  I unmounted it and tried it again and it said "Permission denied while trying to determine filesystem size"

Seems like this might be the right track, though, thanks.

trying putting a sudo infront of the command. Generally if you have permission errors you should trying running the command with sudo. Sudo means Super User Do, so you end up running the command as superuser, or root.

~Andrew s.

---

### Post by jeffathehutt on 2006-08-10
My mistake...  Yes, put sudo in front of it, it should work then.

---

### Post by Tom Brokaw on 2006-08-10
Cool, that's done it.  Thanks, Andrew and Jeff!  Now all I have to do is wait until all 41676 files are done copying over... in 13 hours...

This is great, though, as about 75% of the stuff I like to do besides surfing is related to the music on my drive.  It's not perfect, as gparted still shows 3.79 gigs used on a newly formatted drive, but I have the "missing" space back.  

[B]If anyone can tell me how to get those extra 4 gigs, too, I'd love to hear how.
[/B]
If anyone should find this thread, here's a synopsis.  I did things out of order, but I think this should work.

Physically install drive and format as ext3:
 
```

sudo mkfs.ext3 -m 0 /dev/hdb1
```

Mount the drive:
```

sudo mkdir /media/data
sudo mount /media/data
```

Edit /etc/fstab appropriately.  Will differ for each computer.

Set permissions:
```

chown -R username:username /media/data
chmod -r 755 /media/data
```

If this looks wrong to anyone let me know and I'll fix it.  Thanks again!

---

### Post by anaconda on 2006-08-10
Well.. 
Inode table uses some space, I would guess, that it would be around your 4GB in a 250GB disk.

you can get more space available by increasing the inode-size. 
(it is the same than block size in a fat partition.) If you increase the block size the table takes less room. 

For a storage drive the block size can be as big as 1-2MB. It means that if you have a file that is smaller than 1MB it would still take 1MB disk space.. With big file sizes it wont matter..

---

### Post by Tom Brokaw on 2006-08-10
> **anaconda said:**
> Well.. 
Inode table uses some space, I would guess, that it would be around your 4GB in a 250GB disk.

you can get more space available by increasing the inode-size. 
(it is the same than block size in a fat partition.) If you increase the block size the table takes less room. 

For a storage drive the block size can be as big as 1-2MB. It means that if you have a file that is smaller than 1MB it would still take 1MB disk space.. With big file sizes it wont matter..

OK, that makes sense.  The vast majority of the files are over 1MB, so it sounds like I could gain some space back by doing this?

I thought I read in the man pages that jeffa recommended that the block size only went to 4096 bytes, or was that something else?

---

### Post by anaconda on 2006-08-10
The block size goes higher too.
Manual partitioner in Debian installer recommends bigger block sizes for partitions with BIGGER data.. There it went up to 2MB. So it is possible. And if it is possible mke2fs should also be able to make those.. But 0,5MB should really be big enough for most purposes.. atleast it is a LOT bigger than 4096 bytes..
just keep multiplying with 2 untill you have big enoug block size..
4096, 8192, 16384... 262144, 524288, 1048576...


and yes -b option in mke2fs sets the block-size

---

### Post by Tom Brokaw on 2006-08-10
Can I adjust the block size after data is on the drive?  Or does it need to be done at the same time as a format?

---

