---
title: "Recovering lost partitions (data)"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Jimmey on 2007-11-05
I had three partitions on a 60GB drive. Ext3, ext3 Linux bootable, and Fat32, in that order.

I wanted to delete the first EXT3 partition, move the second to the very left, and then expand it to take up the space.

Midway through this operation, Gparted crashed. The partition was moved but not resized, and half my data was missing (some remained - my /home was gone, but some folders like /lib and /usr stayed).

I tried using testdisk to recover the partitions, but the deep search returned 6 results for Linux partitions - Listing files on these partitions returned a message that the filesystem was corrupt.

Since this, I have recovered everything from the last Fat32 partition, and reformatted the whole drive EXT3, so, I don't expect for there to be much hope. Perhaps crucially, though, I've not yet written _anything_ to the drive.

Is there _any_ way that I could recover _anything_ that went missing? I've already prepared myself for life without whatever I lost, but it might be nice if I can recover a few bits and bobs :-P

Any help is greatly appreciated. 

Thanks

---

### Post by hyper_ch on 2007-11-05
Use your backups ;

---

### Post by WorldTripping on 2007-11-05
I've sucessfully used GetDataBack on a Fat32 drive.

Looks like they have a Linux version of the disk explorer app too.

[http://www.runtime.org/]("http://www.runtime.org/")

You do have to pay, though the demo is free.

Also, you have to install it on a different drive, though you can use it on a bootable CD.

Good Luck

---

### Post by az on 2007-11-05
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

Obtain a larger drive and connect it to your computer.  Image the whole drive (or at least the area on the disk where you lost partitions) using gnu-ddrescue.

Then, data-carve the image for whatever you want (jpegs, Openoffice documents, Word Documents....)

You can use the Ubuntu live cd, or just run the rescue-remix live cd, since it already has all the tools you will need.  See the documentation or ask on the discussion section.

You are correct, that moving a partition or even formatting a partition doesn't delete most of your data, although, you may experience some data loss.

Good Luck.

---

### Post by AusIV4 on 2007-11-05
I've used PhotoRec, which comes with TestDisk, to recover files on a couple of occasions. You need another device to recover them to, but I found it to be very good at getting things back.

---

### Post by Jimmey on 2007-11-05
> **az said:**
> Obtain a larger drive and connect it to your computer. 


I don't think I can - this error happened on my biggest drive, and I don't have any money to buy a bigger one :-( Is it possible to do this on a smaller drive? The majority of the data on this big drive was on a FAT32 partition that remained fine - I still have all that data. The partition that was fubarred was around 17GB, and it had around 16 GB of files on it. They're the ones I would like back...If that makes a difference?
> 
Image the whole drive (or at least the area on the disk where you lost partitions) using gnu-ddrescue.


Do you know how I can select which bits of the drive I wish to image?

Thanks

---

### Post by az on 2007-11-05
> **Jimmey said:**
> 
Do you know how I can select which bits of the drive I wish to image?

Thanks

Sure.  Since both partitions were at the beginning of the drive, just image the first 17 gigs (or whatever the size of both partitions was).

Alternatively, you can just run the data carving software on the first part of the disk and tell it to save the files on a mounted partition where there is enough space.

---

### Post by Jimmey on 2007-11-06
> **az said:**
> Alternatively, you can just run the data carving software on the first part of the disk...

Any recommendations on which software to use?

I don't know how to use testdisk to do this.

Thanks - I appreciate your help!

---

### Post by az on 2007-11-06
> **Jimmey said:**
> Any recommendations on which software to use?

I don't know how to use testdisk to do this.

Thanks - I appreciate your help!

Foremost or photorec (or both).

---

### Post by NT4usB on 2007-11-06
I used e2fsck to recover a borked drive last night. Worked pdg, afaic.
Would it be worth a try in this case?

---

### Post by az on 2007-11-07
> **NT4usB said:**
> I used e2fsck to recover a borked drive last night. Worked pdg, afaic.
Would it be worth a try in this case?

If you don't want to run the risk of further data loss, you should image the disk (or the portion of the disk) and try to fsck the filesystem on the image - do not work on the original.

---

### Post by NT4usB on 2007-11-07
> **az said:**
> If you don't want to run the risk of further data loss, you should image the disk (or the portion of the disk) and try to fsck the filesystem on the image - do not work on the original.

On that I agree, 100%.
Just have a look in my /etc/..., bkup after bkup of the files I tinker with...

I was curious about fsck vs all the third party apps mentioned in this thread.

---

### Post by Jimmey on 2007-11-20
I've used photorec to recover a great deal of the files. However, it only partially recovers some.

There's an option to search for .blend files, Blender 3D's file format. It's recovering 800+ of these files where I'm sure there were no-where near as many as this. Some of the .blend files it's recovering are around 400MB, which is practically impossible. And when I try to open any of the recovered .blends, Blender complains that the file is "incomplete".

To be honest, I'm just wanting for one, single, specific .blend :-( The rest, I can live without. 

Do I have any chance at rescuing this .blend?

Thanks

---

