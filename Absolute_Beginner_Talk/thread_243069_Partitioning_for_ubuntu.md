---
title: "Partitioning for ubuntu"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by AndrewLZ on 2006-08-24
Hello Everyone,

Here's the partition layout I'm looking for:

I have a 100GB (93GB usable) hd in my laptop and an external HD that I want partitioned in the following way:

Windows System    - 25GB  NTFS (already exists)
ubuntu root       - 10GB  ext3
Shared Partition  - 58GB  (??)
200GB External HD - 200GB (??)

I'd like the 58GB and the 200GB to be as cross compatable as possible. I'm still dependant on Windows (until I check compatability with WINE and VMware), so I want to make sure there are no errors on either Linux or Windows.

So should I install ext3 support in Windows and run them both as ext3 or should I install NTFS support in ubuntu and run them both as NTFS? (Fat32 has a 4GB file size limit so it's not an option for me)

Thank you in advance,

Andrew

---

### Post by Ziox on 2006-08-24
> **AndrewLZ said:**
> Hello Everyone,

Here's the partition layout I'm looking for:

I have a 100GB (93GB usable) hd in my laptop and an external HD that I want partitioned in the following way:

Windows System    - 25GB  NTFS (already exists)
ubuntu root       - 10GB  ext3
Shared Partition  - 58GB  (??)
200GB External HD - 200GB (??)

I'd like the 58GB and the 200GB to be as cross compatable as possible. I'm still dependant on Windows (until I check compatability with WINE and VMware), so I want to make sure there are no errors on either Linux or Windows.

So should I install ext3 support in Windows and run them both as ext3 or should I install NTFS support in ubuntu and run them both as NTFS? (Fat32 has a 4GB file size limit so it's not an option for me)

Thank you in advance,

Andrew

I would suggest to run both of them as ext3 or ext2 because NTFS w/ write support in Linux isn't as stable as ex3/2 support in Windows

---

### Post by steve.horsley on 2006-08-24
I suggest install EXT2/3 support in Windows. NTFS write support in Linux is still not mainstream.

You are missing a swap partition. 1 Gig should do.

---

### Post by AndrewLZ on 2006-08-24
Wow. Quick responses =). Ok thanks a lot guys,file:///usr/share/ubuntu-artwork/home/index.html this is what I was leaning towards (many say ext3 is a better file system anyway), I just wasn't sure.

Look forward to using ubuntu instead of Windows (as much as possible :-D )


- Andrew

PS. Thank. I forgot about the swap file. I disabled it in Windows because I have 2 gigs which I almost never fill up (even with VMware running with 1GB hehe).

---

### Post by Chachee on 2006-08-24
Just so you know the FAT32 limitation was imposed by MS so that people woudl convert to NTFS.  I have done the same thing you are looking at, here's my layout - 
 
C: - 11 gigs NTFS
E: -  100 gigs NTFS (unable to backup/convert)
D: or hda3 - 123 gigs FAT32 (partitoned with Fedora Core 5, recognized by both OSs)
/hda2 - 157 gig XFS

JT

---

### Post by AndrewLZ on 2006-08-29
Hey Everyone,

I've partitioned my HD as mentioned above (except the 200GB external is still NTFS).

What I've found is that Windows support for ext3 is really crappy so I've uninstalled ubuntu for now and it's back to 2 partitions of 25GB and 68GB. 

I'm still really hesitant about switching completely to ubuntu, so would it be possible to just run it completely off of a 30GB USB HD without even installing a boot loader on the primary HD?

Until I'm sure I can completely switch over, I want to keep the two systems isolated. If anyone has any better suggestions or ideas for me I'm open for those too =)

Thanks,

Andrew

---

