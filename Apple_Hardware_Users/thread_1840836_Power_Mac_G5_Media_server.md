---
title: "Power Mac G5 Media server"
date: 2011-09-08
forum: Apple Hardware Users
---

### Post by sauma on 2011-09-08
Hey all, 

I've been in the process of setting up a media server using [this]("http://www.havetheknowhow.com/") guide and it's been more or less smooth sailing. I ordered a Samsung 1tb hard drive [(this one)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152185") and this is where the troubles start. 

I first tried formatting it in gparted. It shows up as /dev/sda (sdb is the smaller OS drive), but when I try to format is as fat32 or ntfs it fails and give me an error.

```
GParted 0.6.2

Libparted 2.3
Create Primary Partition #1 (ntfs, 931.51 GiB) on /dev/sda  00:00:01    ( ERROR )
     	
create empty partition  00:00:01    ( SUCCESS )
     	
path: /dev/sda1
start: 2048
end: 1953523711
size: 1953521664 (931.51 GiB)
set partition type on /dev/sda1  00:00:00    ( SUCCESS )
     	
new partition type: ntfs
create new ntfs file system    ( ERROR )
     	
mkntfs -Q -v -L "Storage" /dev/sda1
     	
Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
Corrupt inode.
add_attr_std_info failed: Input/output error.
BUG: Standard information attribute not present in file record.
Couldn't create root directory: Input/output error

========================================

```

Then I tried using fdisk in terminal and it seemed to be working but nothing stuck. sudo fdisk -l left me with a couple hundred lines of ```
16807: @ 0 for 0, type=0x0
``` ending in a "Segmentation fault". 


Any thoughts? Is the drive bad? Do I need to jumper some pins so it plays nice with the ppc?


Ubuntu 10.10
Power Mac G5 [specs here]("http://www.everymac.com/systems/apple/powermac_g5/stats/powermac_g5_1.6.html")
Hard drive is listed above. 

Thanks for the help!

Sam


Update: I got it to format to fat32 with gparted but I'd still prefer NTFS. Any ideas as to why it would do one but not the other?

---

### Post by svtguy88 on 2011-09-08
Hmm.  I assume the drive is attached to the onboard SATA controller?  What if you try something other than ntfs?

Not sure why that would make a difference though...

---

### Post by sauma on 2011-09-08
Yeah that's how it's connected. If you look at the edit, I got it to format to fat32 but NTFS is still a no go.

---

### Post by svtguy88 on 2011-09-08
Oops.  Didn't see that you got it to format as anything.  What about ext2/3/4?  Why do you want to use NTFS?

---

### Post by sauma on 2011-09-08
This machine will sit in the living room and hook up to the tv/stereo and serve as a media dump. Essentially I need it to be seen by a linux machine, a macbook pro and a laptop running vista and a desktop running W7 so I assumed NTFS would be the simplest to share via samba. 

Would ext2/3/4 be just as easy to configure that way?

---

### Post by svtguy88 on 2011-09-08
Yes.  Go for ext3 or ext4 (I don't recall the differences, just that ext4 is newer).  What you are going to do is, once the drive is formatted, set up a share (like a Samba share, or ftp or whatever you prefer) and then you can add permissions to allow other users (the users logged onto your Macbook/Win7/other devices), or if you are comfortable with it, all users, to read and write to your share.

For example, my media "dump" lives on my OS X install right now, which is an HFS+ partition.  I just have OS X set up to share the folders I want (/movies, /music, /whateverelse) to my network, and those with proper permissions can read/write, while others can only read.

---

### Post by sauma on 2011-09-08
I'll see if that works when I get home tonight. Thanks for the help!

---

### Post by sauma on 2011-09-08
While I have you here....

Any ideas about the segmentation fault?

---

### Post by svtguy88 on 2011-09-08
I'm thinking it's probably something NTFS related.  I've never used NTFS partitions (at least not on a PowerPC box), so I don't know what the support is like, if at all.

---

### Post by sauma on 2011-09-10
Ok, I got it formatted as ext2 (3 and 4 just bombed like everything else). How do I get it to mount automatically? I've already added

/dev/sda2 /storage ext2 defaults 0 0

to /etc/fstab. Is there anything else that needs to be done?

Thanks for all your help!

---

### Post by svtguy88 on 2011-09-12
Sorry for the delay.  I was working all weekend.  Anyway, editing /etc/fstab is all that has to be done.  Once you finish editing it, run 

```
sudo mount -a
```

to mount everything.  The only other thing you need to make sure of, is that you have created a mountpoint for your ext2 partition (it is odd, by the way, that ext3/4 failed on you...).  Have you mounted the drive at all using the "mount" command?

Your entry in /etc/fstab tells the system to mount /dev/sda2 to /storage.  I'm thinking this is your error.  Unless you've manually mounted (and thereby, created a mountpoint for) your drive at /storage (this would be simply a folder called "storage" in the root of your file system), you don't have a mountpoint for /etc/fstab to mount the partition to.

This mountpoint needs to be created manually.  Typically, you don't put the mountpoint for another drive in the root of your system, as your /etc/fstab file points to now.  A better place for it would be /mnt/storage or /media/storage.  To do this, run 

```
sudo mkdir /media/storage
```

or point it to /mnt/storage - I think /media/storage follows the "Ubuntu" way for mounting things more, but either is fine. Then just change your entry in /etc/fstab to point to your new mountpoint (ex: change "/storage" to "/media/storage").  Run "sudo mount -a" and all should be well...

---

### Post by sauma on 2011-09-15
Hey! I got it working. Feel free to close this.

---

### Post by svtguy88 on 2011-09-17
Glad to hear it.  Please let us know if you have any other issues getting your media server up and running properly.

---

