---
title: "Reliability of hfs+ under ubuntu and alternatives to hfs+ for sharing"
date: 2008-03-14
forum: Apple Intel Users
---

### Post by Debilski on 2008-03-14
Hi,
I know that these questions have been asked several times, but I feel like I can never be sure on how up-to-date the informations are, I&#8217;d rather ask again.

I am using a Dual Boot with OS X and Xubuntu Hardy (pretty much newest updates with the -10 mactel kernel &#8211; the -11 kernel wouldn't give me wireless lan) on a Nov &#8217;07 Santa Rosa MacBook.
Having studied several setup guides, I finally set up my environment in that I use one partition hfs+ jornaled for OS X, one partition ext3 for Linux and a final one hfs+ without journaling as a partition for data and general stuff which I might need under both OSs, such as music and images for virtualbox.

The hfs+ support under ubuntu seems okay when it gets to occasional writes, so for storing data this works.
But as I am also doing some cross-compiling for both linux and mac I need to actively work on the partition (I really don't want to sync everything all the time &#8211; things can get pretty large there).

Now to the problem: Yesterday while I was working on the hfs+ partition, I noticed that some files I had been writing to suddenly were empty and it was not possible to refill them. Shortly afterwards, Linux crashed. (Caused by this? I don&#8217;t know.)
I then booted to OS X to have the disc tool check the partition; at first it said there were some errors and I better save everything but somehow it could clear the errors from disc.

Well, I clearly don't want that to happen again, so my question is, is the hfs+ really that unreliable or could there have been another problem causing this.
I find it really hard what to think of the hfs+ implementation in ubuntu since I haven&#8217;t read any results from test suites or anything. The NTFS-3g people for example claim having done all this.
So if anyone knows anything more about the reliability of *current* implementations of &#8216;secondary&#8217; file systems in OS X and Ubuntu *under stress and high load*, I&#8217;d really appreciate any comments.

Because of these claims from the NTFS-3g people I thought about using NTFS on the data partition, even without windows. Any thoughts to this? Will I need windows after a crash in order to check the fs or is this possible from Ubuntu/OS X?

Or should I rather take FAT32? (The Ext2fsx driver makes Leopard unstable and gave me also corruption when I tried it; this will maybe be an option when finally someone comes with a working Macfuse ext3 driver.)

I hope someone&#8217;s got more insight in all this than I do.

Thanks

---

### Post by cyberdork33 on 2008-03-14
> **Debilski said:**
> Well, I clearly don't want that to happen again, so my question is, is the hfs+ really that unreliable or could there have been another problem causing this.
I find it really hard what to think of the hfs+ implementation in ubuntu since I haven&#8217;t read any results from test suites or anything. The NTFS-3g people for example claim having done all this.
So if anyone knows anything more about the reliability of *current* implementations of &#8216;secondary&#8217; file systems in OS X and Ubuntu *under stress and high load*, I&#8217;d really appreciate any comments.

Because of these claims from the NTFS-3g people I thought about using NTFS on the data partition, even without windows. Any thoughts to this? Will I need windows after a crash in order to check the fs or is this possible from Ubuntu/OS X?

Or should I rather take FAT32? (The Ext2fsx driver makes Leopard unstable and gave me also corruption when I tried it; this will maybe be an option when finally someone comes with a working Macfuse ext3 driver.)First, I would like to point out that it is not an issue with Ubuntu, it is an issue with Linux in general. They have done a very good job of trying to reverse engineer hfs+, but alas there are still problems. 

I would definitely recommend FAT32 above anything else as long as the filesize limitations are not a factor for you (2GB Files are the largest you can store). After that I would say NTFS.

---

### Post by Debilski on 2008-03-14
Thanks for the advice.

> **cyberdork33 said:**
> First, I would like to point out that it is not an issue with Ubuntu, it is an issue with Linux in general. They have done a very good job of trying to reverse engineer hfs+, but alas there are still problems.

Is hfs+ support actually still being worked on? The launchpad site directs me to a dead ftp-server and on sourceforge I found a project giving out stuff for the 2.4 kernel. Or has all the support moved into 2.6 directly? I&#8217;m just wondering where this lack of up-to-date info comes from. Or am I missing something?

> **cyberdork33 said:**
> I would definitely recommend FAT32 above anything else as long as the filesize limitations are not a factor for you (2GB Files are the largest you can store). After that I would say NTFS.

Shouldn&#8217;t it be 4GB or is there some other limitation? (Oh, I just read about exFAT which surmounts this limitation, but I don&#8217;t think there will be any linux news, say, before easter.)
Seriously, the file size could be a problem. Especially with the images for virtualbox; and having to sync these 10G files back and forth all over again&#8230; I don&#8217;t know.
But I&#8217;ll think about it.

As for NTFS, do you think it is okay using it without the help of a native Windows? I recall that some time ago when I had a crash the NTFS driver wouldn&#8217;t let me mount the drive without a check before, but it also said that I would be better off doing this in Windows. This made me a little cautious but maybe the driver itself was just being cautious and it really shouldn&#8216;t have been a big problem&#8230;

So, actually, I might try it with NTFS. (I&#8217;m quite appealed by the absurdity of the situation, having the &#8216;most proprietary&#8217; alien file system as a mediator between Linux and OS X.) But I think I&#8217;ll wait for a few more comments on real life usage with the NTFS drivers. Also from the OS X Macfuse side.

---

### Post by cyberdork33 on 2008-03-14
> **Debilski said:**
> Is hfs+ support actually still being worked on? The launchpad site directs me to a dead ftp-server and on sourceforge I found a project giving out stuff for the 2.4 kernel. Or has all the support moved into 2.6 directly? I&#8217;m just wondering where this lack of up-to-date info comes from. Or am I missing something?It is part of the kernel now, no separated development.

> **Debilski said:**
> Shouldn&#8217;t it be 4GB or is there some other limitation? (Oh, I just read about exFAT which surmounts this limitation, but I don&#8217;t think there will be any linux news, say, before easter.)
Seriously, the file size could be a problem. Especially with the images for virtualbox; and having to sync these 10G files back and forth all over again&#8230; I don&#8217;t know.yes it is 4GB. I don't know where the 2GB came from. There really is no good filesystem for sharing between... maybe ZFS if there is a good linux driver yet.

> **Debilski said:**
> As for NTFS, do you think it is okay using it without the help of a native Windows? I recall that some time ago when I had a crash the NTFS driver wouldn&#8217;t let me mount the drive without a check before, but it also said that I would be better off doing this in Windows. This made me a little cautious but maybe the driver itself was just being cautious and it really shouldn&#8216;t have been a big problem&#8230;

So, actually, I might try it with NTFS. (I&#8217;m quite appealed by the absurdity of the situation, having the &#8216;most proprietary&#8217; alien file system as a mediator between Linux and OS X.) But I think I&#8217;ll wait for a few more comments on real life usage with the NTFS drivers. Also from the OS X Macfuse side.FAT32 is probably the most widely supported, but i has the limit issue. NTFS is the next best bet since the FUSE tools have been developed. I don't really use them though, as I just have a shared network directory that I use for such things. HFS+ is very closed... hard to develop. IDK why the lost interest in ext3 for OS X...

---

