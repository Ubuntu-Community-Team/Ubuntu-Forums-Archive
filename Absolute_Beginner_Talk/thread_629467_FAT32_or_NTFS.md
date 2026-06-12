---
title: "FAT32 or NTFS?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by agerfe on 2007-12-02
I'm ready to install Ubuntu Studio on my second hard disk. I have created two partitions there and will be installing on the first partition.

Now, I don't know which format I should give to this partition prior to installing. The second partition, as well as my first hard disk, is on NTFS.

I need to be able to open the files stored there with either Ubuntu or Windows.

Should I format this partition as NTFS or as FAT32?

agerfe

---

### Post by mdpalow on 2007-12-02
FAT32 if you need windows to be able to read/write to this partition as well.

---

### Post by antharr on 2007-12-02
You can format as either. Linux now has the ability to read and write to NTFS partitions with ntfs-3g. I have used it for months now and have no problem.

---

### Post by mdpalow on 2007-12-02
I'm having a little difficulty following your post, so just to be clear...

If I was installing Ubuntu onto a hard drive, I would format it EXT3. However, if I was formatting a second partition that I wanted both Ubuntu and Windows to be able to read and write to, I would format that partition using FAT32.

Ubuntu can read/write to an NTFS partition, but Windows cannot read/write to a EXT3 partition.

---

### Post by jken146 on 2007-12-02
There is an ext3 driver for Windows out there.  A google search will find it.  I would recommend installing a Linux distro on a partition formatted in a Linux filesystem (ext3, Reiser...).

---

### Post by jken146 on 2007-12-02
Found the link: [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by jken146 on 2007-12-02
I guess I should say that this is not ideal as there are issues with file permissions that arise when using ext3 in Windows.  For example, and if I'm not mistaken, this driver allows anyone in Windows to read and write to files in /bin.  If you have a / partition that is separate from your /home partition then you don't need to mount / in Windows at all and this might become a moot point.

---

### Post by antharr on 2007-12-02
Are you using the second partition for a Windoze install or just for storage?

---

### Post by monte48lowes on 2007-12-02
I would not recommend using NTFS. Windows has issues cleanly unmounting the drives. Search the forums here for issues mounting NTFS. Second, I would not use FAT32 since it is not a journaling file system. If the computer crashes or power is lost when the disc is in the process of writing, your information may be lost. 

I have all of my partitions formatted as ext3, with the exception of the one WinXP is installed on. I use the fs-driver to read my linux partitions from windows (which isn't very often :D ).

Mike

---

### Post by ptn107 on 2007-12-02
ext3

---

### Post by ubutufan on 2007-12-02
Hi
Your Ubuntu installation should be on ext3.
Windows XP is on NTFS.
Now, if you need another partition (let's call it share-partition) so that you write files using any of the two operating systems (that is ubuntu or windows), your best choice for that partition is NTFS. The reason is simple. Because it is a safe filesystem (unlike FAT32 as explained by another member) and Gutsy and or Windows can access it SAFELY.

---

### Post by Bigbird999 on 2007-12-02
This newb followed a really good how to dual boot with Windows on a laptop, It suggested:
a windows partition for os and programs  mine is 6 GB ntfs
a shared partition both Linux and Winodoze can read/write 9 GB fat32
a Linux partition 4 GB ext3
a swap partition 1 GB linux swap

It worked first time with no issues for this total linux newb.  It was invaluable while trying to get linux wireless and internet access going.

I would boot in windows, come to these forums get answers or links to how tos etc. Save the web page to the fat32 partition.  Boot into linux, open the saved web page from the fat32 partition and follow the instructions to get Ubuntu going.  I also made images of bot the windows and linux partitions with a windows program (Acronis).  These are stored on the fat32 partition and if I ever bork either installation I can restore it in about 10 min.  I have done ths 3 or 4 times as I learn/break Ubuntu and/or try different distros like mint.

Just for ease of use and to ensure that both windows and Ubuntu can read write to the same partition without screwing around with installing more programs and changing permissions, FAT 32 is the easiest for a newb.

BB

---

### Post by HermanAB on 2007-12-02
From a purely technical point of view, it is best to use Ext3 with a special Windows driver.  This solution is more mature than using NTFS with a special Linux driver.

Don't use Fat32 if you can help it, since it is not robust.

However, dual booting is so 20th century.  The modern solution is to install VMware or Virtualbox and run Windows in a window on Linux.  This is much more convenient than dual booting, where after a few minutes you invariably find that you are running the 'wrong' system.

'Hope that helps!

Herman

---

### Post by agerfe on 2007-12-02
Thanks guys!
Of course, I was referring to a partition that would be shared by Windows and Ubuntu. I realize now I didn't explain myself correctly.
After reading all your posts and making some calls I've decided for NTFS. FAT32 is not safe and have my doubts about EXT3 working correctly even with the driver for Windows.
Thanks again to all of you!

agerfe

---

### Post by lewisskinner on 2007-12-02
> **antharr said:**
> You can format as either. Linux now has the ability to read and write to NTFS partitions with ntfs-3g. I have used it for months now and have no problem.

Oh cool, I didn't realise that!  Does gusty come with this by default, or do I need to download ntfs-3g separately?

---

### Post by monte48lowes on 2007-12-02
If you choose to use NTFS be aware there are times when ubuntu will not mount the drive. This most often occurs after a recent windows session. Sometimes windows does not cleanly unmount the drive leaving data in the journal that needs to be written to the partition before accessing data is allowed. The only fix is to boot back into windows and perform a normal shutdown.  

Mike

---

### Post by gaspard.leon on 2007-12-02
ubuntu includes NTFS drivers by default now.. however, if windows shuts down incorrectly and "flags the NTFS partition dirty" ubuntu will not mount, (or mount readonly?) the NTFS partition, you can fix it by booting back into windows and letting it run chkdsk...
(... note this has not happened to me yet...)

NTFS in linux works really well now.

I have not tried ext3 in windows but i suppose that would work well too...

if you're dual booting you need to have windows installed on an NTFS partition (I don't use and don't recommend FAT32 for anything other then say USB sticks etc)

since you already need windows installed on an NTFS drive, you might as well make it your storage medium.. depends on why you're hanging on to Windows.. as another poster mentioned you can run windows under VirtualBox very easily for non-game applications.

Gaspard

---

