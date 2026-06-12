---
title: "Ubunto 9tb file server, to be read/write from Mac."
date: 2009-06-03
forum: Apple Hardware Users
---

### Post by AndyLyons on 2009-06-03
Hi

Total newbie here so sorry if its a simple question to you all, and simple answers please :-)

I am just about to put together a new media/file server and thought would give Ubuntu a go.
It will consist of 8 Sata Drives totaling 9TB.
This box will then be connected via Gigabit Ethernet to a Mac mini connected to an LCD and a Macbook for playing back movies/music/photo slideshows etc.

What I need to find out is how best to format the drives to make sure they are be both Readble and Writable from the Macs (running Leopard).

At the moment the drives are formatted in Mac HFS+ and in various enclosures attached to the Mac Mini, so would quite like to avoid having to move all the data off, reformat and copy data back on.

Would appreciate any advice on best way to accomplish this, and also any things I need to be aware off during my first Ubuntu build. Some of the files are over 5gig so I know that FAT is a no go.  

Incase it makes a difference, hardware is 
**[B]Gigabyte motherboard EP45-UD3R & Intel E5200 Dual Core 2.5ghz, 2 gig Crucial Ram.**[/B]


Hope you can help

Thanks

Andy

---

### Post by Spartan.II.117 on 2009-06-03
I believe hfs+ support is  still read only under Ubuntu, so your best option is probably ext3, which your macs should be able to read just fine, so if possible, copy the contents of the first drive onto another (or others), format the first one, then rotate the data(from hfs+ to ext3) of an entire drive, then format that one and move the next ones data to it. I hope this makes sense.

---

### Post by AndyLyons on 2009-06-03
Thanks for the Reply Spartan.

Do you think Ubuntu will ever get read/write for HFS ?  or is it all down to Apple ?

Dont want to really have to recopy everything from disk to disk especially as not all disks are same size, so dont mind waiting a few months if its due to be sorted out in the next Ubuntu Release.

Cheers

Andy

---

### Post by AndyLyons on 2009-06-04
Hiya Spartan

I tried a test disk formatted to EXT3, and the mac could read it but could not write to it.

What I need is for the Macs to be able to Read + Write to the Disks that are stored in the ubuntu machine, being accessed via Gigabit network.

Am I doing something wrong on the EXT3 setup ?

Or should I reformat in NTFS which I can access from the Mac by using the NTFS3G + MacFuse.

Is this the best route to achieve full read + write from the Mac to the Ubuntu box ?

Thanks again for you help

Andy

---

### Post by ad_267 on 2009-06-04
If the Macs are accessing the server over the network, then I don't think it matters what file system is used. 
This is only an issue when the hard drive needs to be directly accessed by two different operating systems, for example when dual booting or using a removable drive.

If the Macs can't write, then this is a file sharing issue, not a file system issue right? How are you sharing the drives? Samba or NFS?

Or am I missing something here?

---

### Post by cyberdork33 on 2009-06-04
> **ad_267 said:**
> If the Macs are accessing the server over the network, then I don't think it matters what file system is used.

Bingo. In that case, your mac only needs to support the format that the files are shared with. The sharing method is essentially the filesystem.

Also, Ubuntu can read/write HFS+, just not journaled HFS+.

---

### Post by Spartan.II.117 on 2009-06-05
> Also, Ubuntu can read/write HFS+, just not journaled HFS+.

This is correct, and is also the issue with macs not writing to ext3, you must disable journaling form the mac but then you will be able to read/write from ubuntu.

similarly if you format the disk as ext 2 you can read/write from a mac.

---

### Post by cyberdork33 on 2009-06-05
> **Spartan.II.117 said:**
> This is correct, and is also the issue with macs not writing to ext3, you must disable journaling form the mac but then you will be able to read/write from ubuntu.

similarly if you format the disk as ext 2 you can read/write from a mac.
if the driver even works for you... :)

---

