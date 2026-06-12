---
title: "Partitioning a 60GB HDD"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by manishk on 2006-09-27
Hi,
   In what *ratio* should I partition my hard-disk, if plan to use both Windows XP (Pro) and Ubuntu (64 bit edition).
   Please include the 'common' FAT32 partition which I've read a lot about on these forums!

   Any other suggestions on optimum usage of the resouces.:rolleyes: 

P.S: I'll be using an HP laptop with AMD Turion X2 (64-bit dual core), 512 MB DDR2 RAM.

Thanks in advance:D

---

### Post by darrenm on 2006-09-27
Bit of a difficult one to answer. It's all down to where you intend to keep your files, who large they will be, what you intend to do with each one etc.

If you want to keep everything in a common VFAT partition then maybe 10GB NTFS for Windows, 10GB EXT3 for Linux, 512MB swap for Linux and 45GBish for FAT32 to share between OS's

Install XP first, make the NTFS partition and leave the rest of the drive enpty. Then install Ubuntu and create the VFAT partition with Ubuntu then when installed Grub will have an option for both.

---

### Post by bigken on 2006-09-27
point of thumb always make your swap file twice the size of your ram 
ie 512mb = 1gig

---

### Post by saphil on 2006-09-27
10/10/.5/30 seems like a good set of sizes.  

I am running a Windows/edgy box and I partitioned all the possible linux partitions.  This turns out to be an error because the /usr directory is at 2gb and climbing.  
I gave Windows (2k pro) 5gb of space and it is basically too full.  I am going to have to start all over again at some point and resize the partitions, or flush the partition table and start again.  This is an edgy test box, so I am not doing a heck of a lot with it.  Standard installation of hoary, dist-upgraded to edgy, with maybe 10 other applications.  Don't even have open office on it, but right now

part    Directory  Type  Total      Free   Available   Used
hda1   c:\           fat32  5gb       1gb  .8gb          4.2gb   84% (1)
hda2   /              ext3   3.9gb    3.8g  3.6g         .188gb  4%
   
hdb1   /var          ext3   2.8gb     2.3gb  2.2gb     .427gb  15%
hdb2   /opt          ext3   3.7gb    3.6gb  3.4gb     .032gb   0%  
hdb3   swap         swap  .5gb   
hdb4   /home       ext3   22gb    20.8gb 19.7gb    1.2gb     5%  (2)
hdb5   /usr          ext3   2.8gb    .8gb    .66gb      2gb      75%  (3)
hdb6   /usr/local    ext3   2.8gb   2.7gb  2.6gb      .056gb  2%
hdb7   /tmp         ext3    2.8gb   2.7gb  2.6gb      .032gb   1%  (4)

This is the distribution from standard installations, using no customized install scripts.
1 - If I actually wanted to do much of anything with the Windows OS, I would have to increase the size of the partition, Windows and basic programs (openoffice, Microsoft publisher)  takes up almost 4gb.  Were you to run a shared fat32 space for both OSs, you might  be able to set your windows account directories there.  I haven't figured out how to do that yet.  
2 - the /home directory is the only one that is suggested to be placed on its own partition, so if a user fills it with mpegs or something, it doesn't affect the OS, and also it is essentially portable, if you decude to upgrade your computer to a bigger hard drive or transfer the data to a different computer
3 - /usr is where apt puts all deb files and is also where the kernel image is stored.  When I had kernels on this machine going all the way back to hoary, this directory was extremely full.  I purged all the old kernels I could and used **aptitude autoclean** to get rid of all debs for old unused applications.  

Volitility
 / directory is pretty much the same as it has always been, and does not seem to swell at all.
/opt never does anything at all.
/var goes up by how much shared or Internet-facing stuff you have going on.  The samba and www folders are here by default.  I am doing nothing with sharing or webhosting on this machine, so it stays about the same.  My Linux file server has a separate hard drive for /var/samba because of how many files are stored in there. 
/usr rose to 60% immediately and has edged up since.  It is pretty active.
/usr/local is not all that active, but it might swell if users without sudo accounts were adding software for themselves.
.tmp is volotile, but purges itself well.  There is never any real huge amount there.  

Each of these partitions lose 1 or 2 hundred meg as overhead, and on a small disk like the one I have, this is a bad thing.

---

### Post by manishk on 2006-09-28
Hmmm..thanks a lot guys

But Saphil, I'm totally totally new to Linux, and anything '*non-Windows*'. So I dint get anything of what you said, but I'm ready top learn!;)

---

### Post by Loffe_ on 2006-09-28
FAT32 for a 45GB partition is not very good. Fragmentation is a hell. I recommend that you make it a ext3 instead.

There is an easy way to give Windows access to is [http://www.fs-driver.org/](http://www.fs-driver.org/)

//Loffe

---

### Post by saphil on 2006-09-28
Sorry, I didn't notice I had gone so far.  

I agree with using ext3 for  large shared partition, or, give Windows 20GB and don't have a share if you never want to trade anything from one OS to the other, or if there are some users using the windows side who do not use the Linux side..

Wolf

PS the Ext2IFS.exe app worked great to let me have access to my Linux side stuff.

---

### Post by manishk on 2006-10-10
I just checked out the link you gave me...

In the FAQ section it says 

> What limitations arise from not maintaining access rights?
The current version of the Ext2 file system driver does not maintain access rights. All users can access all the Ext2 volumes that a drive letter is created for. For example, if a drive letter has been created for an Ext2 volume, which is the root volume of a Linux installation, you can simply read and modify files such as /etc/passwd and /etc/shadow. User names are readable and **passwords of these users can be quite easily cracked and modified**!

Does that mean, passwords in Linux is NOT safe??

---

### Post by anaconda on 2006-10-10
That means that if you boot to windows you can access and modify anything from the linux-partition. eg. you could edit /etc/shadow -file and change user passwords. 

It is the same if you boot with knoppix liveCD.. then you can access the linux partition with root (admin) rights and modify anything.

BUT passwords can't be easily cracked, because they are encrypted. Changing is possible, but cracking not.

So it is not really any problem. Just be careful that you wont accidentally delete anything you dont want to delete..

fs-driver is a good and reliable program. I wouldn't use fat32 anymore..

---

### Post by saphil on 2006-10-11
It is a good hint to maintain physical security around your computer, isn't it?  Anybody with a knoppix disk -- or in this case -- your Windows password, can access and muck with your Linux files as a superuser.  If you are concerned about physical access to your machine, remember to use as strong a password for the administrator account as possible, and rename the administrator account.  Set your screensavers to require password, and avoid the temptation to let Windows boot to an open user account (even an account of minimal permissions).  

Brute-force cracking can take a long time, but the first thing an attacker is going to do is a dictionary attack on your passwords, and there are not that many words in the English language to go through.  A password made of "real words" is real easy to crack.  This goes for all of your passwords, not just specifically Windows ones.  

There are 256 possible characters in the ASCII chart, including all numbers, letters, accented characters and punctuation.  The longer and more random your password, the better.  to crack a 2-character password requires the cracker to try 256x256 possible combinations (65,536).  If each character = 1 byte and a byte is 8 bits, then this is about 16,384 cycles of a 32bit cpu.  Clock-speed of a cpu is how many cycles per second.  An average Pentium III running at 500mHz should crack your 2-char word in  0.000032768 of a second.  a little slower than 300 thousandths of a second.
An 8-character password has 256^8 possible combinations (18,446,744,073,709,551,616), this would take about 29 years to crack on my slow processor here, and a 9-char password...
(4,722,366,482,869,645,213,696).  A 9-char word would take 236,118,241,434.83 seconds to crack.  Rounded, this is approximately 7482.14 years.

My brain is whirring, and it is 3:30 am here in GA.

---

### Post by manishk on 2006-10-11
Thanks (again)

My brain is whirring too! :)

Can Win passwords also be changed this way?

---

### Post by saphil on 2006-10-11
A short answer..  Yes.  Don't leave your computer in a vulnerable spot.  Only let people you trust have "alone time" with your computer.  Lock your screen if you must be away from your computer.  Windows or Linux (or UNIX or any other operating system I can think of) is vulnerable to physical attack.

---

