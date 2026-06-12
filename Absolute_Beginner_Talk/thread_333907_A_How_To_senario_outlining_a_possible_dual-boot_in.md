---
title: "A How To senario outlining a possible dual-boot installation"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by MindRiot on 2007-01-08
Hi everyone.

For those new to Linux, installing Ubuntu can be a challenge. Below I provide the steps necessary to complete one possible installation scenario you could follow if you plan to share a single hard drive with Windows 2000 or Windows XP, and you answer "NO" to the following question:

"Do you need to see the files you created on the Linux partition from Windows?

If you answered "YES," then this scenario doesn't apply to you. If you answered "NO," then read on.

WARNING! Following the steps outlined in the scenario below will destroy all the data on your hard drive. You will need to re-install Windows. Make sure you back up all the files you want to keep before proceeding. 

Step 1: Prepare Your Hard Drive (Optional)

Following this step is optional and depends on a "YES" answer to the following question:

"Do I want to use Linux to back up Windows?"

If you answered "NO," then skip to step 2. If you answered "YES," then read on.

The advice given below is based on the advice given by Robert Billing in his book "teach yourself Linux"

Visit [www.books.mcgraw-hill.com](www.books.mcgraw-hill.com)

You can use gzip to compress Windows into a large .gz file by using the following command:

gzip </dev/hda1 >Windows.gz

You are telling gzip to compress all the data on /dev/hda1 to a file called Windows.gz. Since gzip is going to compress all the data on the primary partition /hda1, you need to prepare the hard drive by writing zeros across the whole disk by booting Linux from the Live CD (not from the hard drive), and using the command:

dd if=/dev/zero of=/dev/hda.

Then install both operating systems and programs and restore your files. The remaining free space on /dev/hda1 will consist of zeros, so to quote Robert Billing "the gzip compression program will reduce them to almost nothing."

Use the command:

gunzip <Windows.gz >/dev/hda1

to restore the backup.  Keep in mind, the partitions on the hard drive need to be identical to the partition layout when Windows.gz was first created to successfully restore Windows from the gzip file.

Step 2: Partitioning Your Hard Drive

There are two ways to partition your hard drive. You can either use Windows setup or a 3rd party partitioning program. If you installed or replaced your Desktop PC's original OEM hard drive with a retail hard drive, then the retail hard drive should include a partitioning program that will allow you to use a floppy or CD (if you are preparing a second hard drive) to partition your hard drive. If you choose to partition the hard drive with a 3rd party program, Windows will mount each of those partitions and assign them individual drive letters. If you have been using Windows with only one hard drive for some time, you are probably used to having a familiar letter assigned to each of your particular drives. To prevent Windows from mounting those partitions during the Windows installation, you need to use Windows to partition the hard drive during Windows' setup.

Use Windows setup to delete all the partitions on the hard drive, and then create a single partition by specifying the size of the partition that will be home to Windows.  Chances are good that you will need to allocate the lion's share of disk space to Windows. Especially if you play video games that require DirectX.  When people do decide to completely switch to Linux, the migration from Windows to Linux is often long. As a newcomer to Linux, its difficult to gage how much disk space to allocate to Linux since you don't yet have a clue as to how much disk space will be required by the programs you will eventually decide to use in Linux.  If you have an 80 GB hard drive or greater, then allocate 15% to 10%, depending on the size of the hard drive. If you have a 250 GB hard drive, 10% is 25 GB s, which leaves plenty of elbow room for Linux, unless you plan on playing modern video games that support OpenGL under Linux, then you should consider increasing the amount of space to somewhere between 30% and 50% of total disk space.

Suppose you had a 250 GB hard drive, and you decided to allocate 10% to Linux, you would then need to set the partition in Windows setup to 225 GB s. This would leave the remaining free space as unallocated disk space and Windows would not attempt to mount a partition with unallocated space during installation and therefore you would only see the partition on which  Windows was installed to as Local drive C:.           

After you successfully install Windows, you can now install Ubuntu Linux. Boot the computer from the Live CD, and double-click the install icon on the desktop. When the partitioner starts, select the option to install in the unallocated space and setup should take care of the rest of the procedure for you.  If that option isn't available, then select the option to manually partition the drive. Right click on the unallocated space and select new. You need to create at least two partitions. A root partition and a swap partition. You need to specify the format for the swap partition as Linux_swap.  1 GB should be  sufficient size for the swap partition, so reduce the new partition you are creating in the unallocated space by 1 GB, so there remains 1 GB of unallocated space. Then, once again, right-click the remaining unallocated space and select new, then specify the partition as Linux_swap from the drop down list. The list of partitions should now include three partitions, your primary partition with Windows /hda1 and two partitions below marked ext3 and Linux_swap, one indicated by a green box, and the other indicated by a red box. When you are satisfied with the partition scheme you have created in the unallocated space, click forward. If you manually partitioned the drive, you will need to select the primary partition /hda1 as /media/hda1 and then the larger of the remaining two partitions as root (/) and the smaller partition as swap. Once you're done, click forward and the partitioner program will ask you to verify the tasks it intends to perform based on the summary information displayed. If the information is correct, press forward, and the installation will begin.

Hopefully, the installation goes smoothly and you reboot into a fully functioning Ubuntu Linux desktop.

Good luck.

---

### Post by spin2cool on 2007-01-08
I'm not sure this is the best dual-boot advice.  If you create a 225 GB windows (NTFS) partition, none of the data in that space will be writable using Ubuntu.  (There are some beta programs that are working to provide NTFS support, but you run the risk of hosing your hard drive).

Generally speaking, I use 4 partitions:

1) Windows (NTFS) 20 GB
2) Ubuntu / (ext3) 20 GB
3) Linux Swap (swap) (~2gigs)
4) Data (FAT32)  (all remaining space)

Fat32 partitions are natively supported by both windows and linux, and are currently th ebest bet for sharing data between the two.

Honestly, even ext3 would be better than NTFS for your data, because you can use this free driver to access ext3 from windows (with no known problems):  [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by MindRiot on 2007-01-08
As I stated above, the information is based on advice from Robert Billing's "teach yourself Linux." From your comment, I take it uncompressing the .gz file back to an NTFS partition wouldn't be possible.

Anyways, the remainder of my advice regards installing Windows so Windows does NOT mount the partition space that will be used for Linux.  That way, when using Windows, you only have one Local drive.  So backing up Windows to an ext3 formated partition with Windows wouldn't be possible, unless you had Windows mount the the Linux root partition.

However, your advice is appropriate for those having all the partitions mounted in Windows. :)

---

