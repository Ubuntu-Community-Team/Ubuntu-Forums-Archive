---
title: "Partitions"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by BigLebowski on 2006-10-16
Hello, having great fun with Ubuntu.. but i have a question:

Is it possible to make a partition with either a Windows App or Linux App that is accessible, Writable/Modifiable by both OS's(Windows XP and Ubuntu)?

I do have a few partitions that i made with a Windows App called partition magic they work great with windows but when i go to go into them on Ubuntu it gives me some "not able to mount" error message, this happens to both NTFS and Fat32

Anyhelp is greatly apreciated

---

### Post by HareBall on 2006-10-16
> **BigLebowski said:**
> Hello, having great fun with Ubuntu.. but i have a question:

Is it possible to make a partition with either a Windows App or Linux App that is accessible, Writable/Modifiable by both OS's(Windows XP and Ubuntu)?

I do have a few partitions that i made with a Windows App called partition magic they work great with windows but when i go to go into them on Ubuntu it gives me some "not able to mount" error message, this happens to both NTFS and Fat32

Anyhelp is greatly apreciated

Somebody else will probably help you more, but the short answer is yes. You can creat a partition that is readable by both OS's. You can read anything in both windows and Linux from Linux, but you need to creat a FAT32 partition to be able to use things both ways.
I pull stuff from XP all the time to Ubuntu.:D  XP doesn't even recognize that I have a second hard drive in this box.[-(

---

### Post by Peepsalot on 2006-10-16
I prefer to use ext3 instead of FAT32.  See my signature: FS-driver.

If you already have a fat32 partition and don't feel like changing it, Linux should be able to read and write to it.  You just have to make sure your fstab is configured properly.  There are instructions on ubuntuguide.org

You can also configure Linux to read any NTFS partition.

I believe there is also *experimental* support for writing to NTFS, but I have not been brave enough to try it.  Basically there is no gaurantee that it won't mess up your data as far as I know.

---

### Post by HareBall on 2006-10-16
> **Peepsalot said:**
> I prefer to use ext3 instead of FAT32.  See my signature: FS-driver.

If you already have a fat32 partition and don't feel like changing it, Linux should be able to read and write to it.  You just have to make sure your fstab is configured properly.  There are instructions on ubuntuguide.org

You can also configure Linux to read any NTFS partition.

I believe there is also *experimental* support for writing to NTFS, but I have not been brave enough to try it.  Basically there is no gaurantee that it won't mess up your data as far as I know.

Do you have to do this from windows? Or can it be done from Ubuntu?:-k

---

### Post by HareBall on 2006-10-16
> **Peepsalot said:**
> I prefer to use ext3 instead of FAT32.  See my signature: FS-driver.

If you already have a fat32 partition and don't feel like changing it, Linux should be able to read and write to it.  You just have to make sure your fstab is configured properly.  There are instructions on ubuntuguide.org

You can also configure Linux to read any NTFS partition.

I believe there is also *experimental* support for writing to NTFS, but I have not been brave enough to try it.  Basically there is no gaurantee that it won't mess up your data as far as I know.

I hate to bump this, but I am afraid it will not get answered from other than the first page.

---

### Post by az on 2006-10-16
Parttion magic is not really what I would reccommend.  The partitioner on the Ubuntu cd is much more stable.

You should have no problems sharing a fat32 partition.  You just have to make sure that you are trying to access it properly.

How are you trying to get to the partition that you created with partition magic?

---

### Post by Peepsalot on 2006-10-16
> **HareBall said:**
> Do you have to do this from windows? Or can it be done from Ubuntu?:-k
Do what from windows?  Use FS-Driver?  Yeah, that's the point.  Windows can't normally read ext2 or ext3 and FS-driver allows it to do this.
Linux always was able to read ext2 and ext3(it is the default filesystem for an ubuntu install), so obviously there is no need for FS-driver in Linux.

In windows, I can read an write to my whole Ubuntu partition as I please.  So you don't even have to necessarily make a designated "share" partition if you don't want to.  Although I suppose it would be safer to only write to a partition that is separate from your Ubuntu system files, becuase it essentially gives you root access.

[quote=FS-driver FAQ] The current version of the Ext2 file system driver does not maintain access rights. All users can access all the Ext2 volumes that a drive letter is created for. For example, if a drive letter has been created for an Ext2 volume, which is the root volume of a Linux installation, you can simply read and modify files such as /etc/passwd and /etc/shadow. User names are readable and passwords of these users can be quite easily cracked and modified!

Therefore the current Ext2 file system driver does not fit for installations which require restrictive rights policies. It should be sufficient for your computer at home, which is used by one or a few users only. Furthermore, you should create drive letters for a root volume of a Linux installation only if you know exactly what you are doing. [/quote]

---

### Post by Peepsalot on 2006-10-16
> **HareBall said:**
> I hate to bump this, but I am afraid it will not get answered from other than the first page.
I subscribe to threads I post in so I always see replies.

---

### Post by HareBall on 2006-10-17
> **Peepsalot said:**
> Do what from windows?  Use FS-Driver?  Yeah, that's the point.  Windows can't normally read ext2 or ext3 and FS-driver allows it to do this.
Linux always was able to read ext2 and ext3(it is the default filesystem for an ubuntu install), so obviously there is no need for FS-driver in Linux.
Yes use FS-Driver. How do you go about using it. I don't have any partitions on my windows drive to install it in. How do I go about using it? I really don't use Windows much anymore, but sure as I boot it up, I think of something I need from Ubuntu.

---

### Post by thephotoman on 2006-10-17
Okay, here's the deal.

It's possible to read/write NTFS in Linux now, but it's still in beta, so before you follow the instructions to which I'm about to link, I suggest backing up your data on that NTFS partition.

The stuff that you need for NTFS is related to the NTFS-3g project, so named because it's the third attempt at getting stable read-write support on NTFS partitions in Linux.  I could go into a long history here, speaking from memories on using Captive (which was more dangerous and involved loading the official NTFS drivers into a pre-alpha WINE environment), but that's really going to bore you.  

Follow the instructions [here]("https://wiki.ubuntu.com/ntfs-3g?highlight=%28ntfs%29").    I wish you the best of luck with them.

As for the FAT32 partition, that should be mountable in Linux by default.  In the future, follow others' suggestion and use GParted (which also has its own LiveCD, which weighs in at 25MB) or fdisk, which comes with all live Linux distros.  Partition Magic isn't really the best option for partitioning.

---

### Post by BigLebowski on 2006-10-17
"Parttion magic is not really what I would reccommend. The partitioner on the Ubuntu cd is much more stable.

You should have no problems sharing a fat32 partition. You just have to make sure that you are trying to access it properly.

How are you trying to get to the partition that you created with partition magic?"


Ah to access the partition(Fat32 partition made on Windows) i go into the my computer equivelent of Unbuntu where it shows all the drives and i click on one and it says its not mountable.


And yes i use Fat32 the most because thats what programs like Truecrypt require.

---

### Post by Peepsalot on 2006-10-17
> **HareBall said:**
> Yes use FS-Driver. How do you go about using it. I don't have any partitions on my windows drive to install it in. How do I go about using it? I really don't use Windows much anymore, but sure as I boot it up, I think of something I need from Ubuntu.
It's really not that difficult.  Did you follow the link?  It's in my signature...

Next time you boot into windows, go to that website.  Download the program and double click it to install :rolleyes: .  The program will have a setup where you choose any existing (ext2fs or ext3fs) partition and assign any available drive letter to it.  If your Ubuntu parition uses the right type of file system(which it should by default) then you can now read and write on that partition from windows.

---

### Post by anaconda on 2006-10-17
> Ah to access the partition(Fat32 partition made on Windows) i go into the my computer equivelent of Unbuntu where it shows all the drives and i click on one and it says its not mountable.

that means that it is not a removable device, and that it is not mountable using pmount, which is meand for removable devices.

What you want is to mount a fixed disk. It can be done either manually from terminal, or if you want it to be mounted permanently you can add that partition to your /etc/fstab -file.

Manually it goes like this:
sudo mkdir /mnt/fat32disk
sudo mount -t auto /dev/xxxx /mnt/fat32disk

you have to change the xxxx to whatever your partition name&number is..
if your hard-disk is IDE (=PATA) then it is hdaX or hdbX.. If your disk is SATA, then it is sdaX, or sdbX.. and the X is the number of your partition.

easiest way to find out the name&number of your partition is to type:
sudo fdisk -l
in terminal, propably you can also see it in your "my computer equivelent of Ubuntu"..

EDIT: after mounting the partition manually you can acess it in /mnt/fat32disk folder that you just created..

---

### Post by BigLebowski on 2006-10-17
Thanks :) ill try that out looks hard :P

Btw that FS driver looks nice but from what i rwad in your quote could be bad for the security paranoid people like me.

---

### Post by randiroo76073 on 2006-10-17
Thats all well & good if you're running an NTFS based OS, but I run 98se[my choice,2 hdds], what to do now?  NP from Linux, read/write perfect but 98se doesn't see Linux.

---

