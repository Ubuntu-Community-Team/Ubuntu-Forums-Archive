---
title: "Disk space allocation question"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by James SoCal USA on 2007-05-14
When creating partitioned drives in various Wx OS versions partition size determines the minimum amount of disk space allocated allocated per small file, record, etc.  Typically 4K up to 64K.  This means that for a large number of small files placed on a very large partition there is a tremendous amount of wasted space.  

1. Being new to Linux can anyone provide information on the way space is allocated on a linux partition, by sector, by groups of sectors (lumps, granules, etc.), typical sector size, 256, 512, 1024, etc?  

2. Iin Linux, can file size exceed the 4Gig limit of non-NTFS files/records in Wx OS versions?

3. When saving a new file to a fragmented disk when various small files have been deleted leaving a large number of small spaces available on the disk is there a master sector record of these vacancies where direction to the next file segment is located or is the information for the next location stored in the data of the currently being read portion?

4. When using long file names, exceeding 13 characters in various version of Wx, do additional directory locations get opened to handle the extended file name information?  In Wx this is very important in the root level as there is only a limited number of directory entries available.  When in a folder this restriction is removed but when the total number of characters in the path become to numerous problems show up when trying to burn CD or DVD backups.

5. In Wx ZoneAlarm is an effective software firewall helping to secure the user from outside attacks, note the word helping, as well as making it more difficult for legitimate software on the system to access the internet without permission.  Is there a similar program available for Lx machines or a way, other than programmin - my programming days ended about the time Wx became popular- to create a similar protection?

While these are being directed to the Ubuntu group I realize they tend to be generic type questions and should apply to many distros but Ubuntu or Kubuntu are presently being considered for my small home/office for use on the server & destops.  There are some apps that I must use that will not likely work on an Lx platform but wherever I an I intend to more as far from Wx as possible.  For those requiring Wx I will be trying to setup a Wx virtual machine on the Lx base.  I will also be needing to share files, printers, etc. between the Wx & Lx platforms.

I hope this is not to much for a single post but any help will be greatly appreciated.  I presently use FF, TB & OO on the Wx platform so those will move to Lx "seamlessly" I hope.

James

Even though I was logged in the system claimed I was not when I went to preview this message?  I had to log in again?  Normal?

---

### Post by hartz on 2007-05-14
I am not an expert on Linux file systems, but you will find that Wikipedia answers many of your questions,  Have a look at this page: [http://en.wikipedia.org/wiki/Comparison_of_file_systems#Comparison](http://en.wikipedia.org/wiki/Comparison_of_file_systems#Comparison)

Note that Linux supports many file systems.  ext2 / ext3 and reiserfs are the most commonly used ones however.

Note: The only practical difference between mounting a file system as ext2 and mounting it as ext3 is, when you have it mounted as ext3, a small region of the disk space is allocated to maintain a "journal", sometimes called a log or intent-log, of the operations being performed.  This journal wraps and helps to maintain the integrity of the file system.

Also you need to distinguish between "posix" standard limitations, such as the file-name and path maximum total length.  Linux complies to the posix standard, even when implementing EXT2, Reiser-FS, etc, all of which in the file system has got support for hugely long file systems.

The EXT2/3 file system does not use pre-allocated directory entries for any directories, not even the root.  And long file names do not take up more than one entry anywhere -  Long file names are natively supported, not an after-though feature.

Files can be much larger than 4 GB.  2TB and larger files are supported, but be aware that the program that open the file can sometimes be the limiting factor.

Zonealarm does two things:  It controls access to network ports, both for opening ports for listening and for allowing packets to be received by the listening applications on ports, and secondly it controls what applications can run and/or open network connections.

In Linux this is not a single tool's function.  The control of packet flows are done by iptables.  Controlling of opening of ports is a separate issue which I do not know what applications are available to do this.  Ditto controlling what applications are allowed to run.

However in Linux the built-in security means that every process (program) that runs, is running under some effective User-ID.  The process can only do what that User-ID is allowed to do, eg what files it can modify, what ports it can listen on, etc.  the root user can listen on any port and read/write any file, but normal users are limited.  This gets long, but suffice for me to say that this security is what prevents "malware" from functioning.

It is worth knowing that Unix and Linux file systems cannot normally become corrupted while they are mounted.  The only possible exception is bugs in the file system drivers, and these have been pretty much sorted out.  This guarantee however doesn't hold if the system loses power without unmounting the file system and committing all IO to the disk device.

Your move to Linux will not be seamless.  Don't expect it to be, and you'll save yourself a lot of frustration.  Be prepared to struggle with a few things, and be eager to learn from those.

I can tell you one thing from many many years in the computer industry:  If everything "just works", you will not learn from it.  You only learn when you battle to get something to work.

---

### Post by James SoCal USA on 2007-05-15
Thanks Hartz3.

I will be checking into it further.  Having come into this during the 1's & 0's days setting switches etc. designing hardware and then software it has been a continuing process that will continue well into the future.  One advantage, and disadvantage, those of us from the past have is that we know what it took to get where we are and all there is today was built on what came before.  A good understanding of the past systems generally gives a better understanding of those in place now after the basic learning curve has been past.  That said it also sometimes gets us bogged down with details the newer folks just breeze on by as they do not see them.

Perhaps there will be someone else that can answer the space allocation questions as that goes to the heart of drive space efficiency and why I have small paratitions in Wx for small files and larger partitions for the larger files.  Much more effective use of the real estate that way.

James

---

### Post by hartz on 2007-05-16
Hi James,

Don't take offense at this, but your repeated use of Wx and Lx (!!$$??!) makes you sound like a wanabescriptkiddyhacker and your using of the Windows file systems as references for basing your "investigation" on seems like you know only windows.

Linux was NOT based on Windows.  It is a Unix clone, it uses (mostly) the GNU utilities to create a full user environment, and it inherited more than a little from the Minix work that went before it, not the least of which is the original Linux file system.

Space allocation is based on direct and indirect (nested) inodes.  Allocation unit sizes vary, depending on which file system you talk about and with some file systems even between files.  Also depending on the file system, allocation policies vary, but nowadays Unix file systems mostly all use some variation of the biggest-fit approach to minimize file fragmentation.  Some file systems goes a step further and implement copy-on-write to further minimize fragmentation (read-performance optimized).  Some makes all of this into tunable options.

Linux today is still bound to the physical disk block-size of 512-bytes.  This is the raw device level smallest possible allocation unit (I've heard that there is work to change this archaic system, though it breaks compatibility with existing controllers, BIOSes, operating systems, drivers, etc).  Allocation for data takes place as a number of "clusters" - contiguous blocks.  The size of a cluster is also a tunable setting within the file system, and defaults of around 4KB is typical.

Considering your technical background, I think you will appreciate this little "talk" I found: [http://perl.plover.com/yak/ext2fs/](http://perl.plover.com/yak/ext2fs/)

---

