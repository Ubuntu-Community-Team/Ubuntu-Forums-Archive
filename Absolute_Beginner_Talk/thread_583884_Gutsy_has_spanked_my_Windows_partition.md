---
title: "Gutsy has spanked my Windows partition"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by whiffy badger on 2007-10-20
:(:(:(:(
On my laptop I already have Windows XP Media Centre installed. I fancied trying out dual booting with Gutsy Gibbon after previously trying out Feisty without major issues. Gutsy was certainly working fine but now after selecting Windows in GRUB - it crashes after a few seconds so I can't get into Windows at all now.  I used the 1st guided partitioner option when installing.  Thinking that I just need to restore the XP bootloader, I used a XP home recovery disk but I am not able to to get into recovery console to fixmbr and instead I get message up saying that my C drive is damaged or unformatted.

I am about to recover my windows partition by booting into acronis true image, the backup being on my D drive.  There is an explorer style view if you boot into Acronis and I can still see my Windows files do exist.  I urgently  need to get my laptop working again in windows, can anyone suggest what I can do to get windows booting again, otherwise I will have to restore with Acronis and I'm not sure that I will give gutsy another chance to create havoc.

Thanks!

---

### Post by moocow1452 on 2007-10-20
Joy, a partition problem. Tread lightly and make sure to not do anything rash is the best I can come up with. Is your D drive seprate from your C, or a partition?

---

### Post by whiffy badger on 2007-10-20
Thanks!

Just to be clear, I have a C partition (not working) and a D partition where my backups are (extended NTFS partition).  I don't have 2 different drives.

Any ideas?

---

### Post by moocow1452 on 2007-10-20
How extensive is your backup? Is it just files, programs, an entire image?

---

### Post by whiffy badger on 2007-10-20
It's an image of my Windows system 1 month ago.   I should have backed up everything yesterday before installing, but I didn't.

Do you feel that there is any hope of getting it to boot or is my only option restoring this backup?

Thanks

---

### Post by Blue_Lander on 2007-10-20
Did you defragment Windows before you repartitioned it during the install?

If not, then its very likely your windows files were not all at the "front" of the disk and many of them were written over...

---

### Post by whiffy badger on 2007-10-20
yes I did  defragment

---

### Post by bsharp on 2007-10-20
The best option I know of for your situation is boot into a live cd and mount the windows partitions read only and try and see if it can see the files.

---

### Post by whiffy badger on 2007-10-20
I can still see the files on C drive using acronis true image, they are still there

---

### Post by Blue_Lander on 2007-10-20
I'm guessing you used just the regular windows defrag utility. 

Most of the time it won't completely pack everything in the very front and it still leaves gaps. When it completed if the completiton view showed any gaps at all between the colors then its still possible that data was written over. Not *usually* probable, but always possible.

If that is what happened then it would have only written over the files at the end. So most of your data is probably still recoverable, but Windows could be completely shot.

---

### Post by Alan Stancliff on 2007-10-20
> **whiffy badger said:**
> yes I did  defragmentFirst thing is to boot into your Acronis emergency boot disk and attempt to do an incremental backup of your windows. If you're lucky, you will be able to get them all.

Be brave. We all know how much anguish you must be feeling, and we empathize.

---

### Post by ryanVickers on 2007-10-20
I spent about 20 minutes getting my grub to work after installing gutsy, but it worked perfectly afterwards and nothing was harmed, just the menu.lst file was wrong... ;)

---

### Post by whiffy badger on 2007-10-20
I don't think it is defragmentation, I always defrag regularly and have used third party defraggers as well.

 I get an error message when I try to restore the MBR using acronis.  I am not sure  what to do now!

---

### Post by ryanVickers on 2007-10-20
try my "Fix Grub Instantly" (it's not actually *mine* by any means, but ;))

a combination of that and tinkering with the locations (hdx,y) while on the live should make it work eventually :)

---

### Post by whiffy badger on 2007-10-20
Thanks for that Alan

I've selected C partition to back up with Acronis as you said, but I get an error message which reads:

Some partitions contain errors and can only be imaged sector by sector. That I should exit  and check the disk with disk checking tools. Am I sure I wish to proceed.

... without an OS that boots how do I check the disk?

---

### Post by whiffy badger on 2007-10-20
Thanks Ryan

I will burn it to disk and see what happens.

---

### Post by whiffy badger on 2007-10-20
It's not just an MBR issue, this utility isn't getting a windows boot

---

### Post by Alan Stancliff on 2007-10-20
> **whiffy badger said:**
> Thanks for that Alan

I've selected C partition to back up with Acronis as you said, but I get an error message which reads:

Some partitions contain errors and can only be imaged sector by sector. That I should exit  and check the disk with disk checking tools. Am I sure I wish to proceed.

... without an OS that boots how do I check the disk?
I'm pretty much new at Linux too, but here's what I would do. I'd perform the backup sector by sector as an INCREMENTAL backup. The incremental backup might be readable when you get your system together (which you will), and by doing an incremental (not full) backup, you will at least have the base you did a month ago.

If you have access to another computer, you might try to [***_[COLOR="RoyalBlue"]download Supergrub[/COLOR]_***]("http://supergrub.forjamari.linex.org/"). This utility might have been made especially for you. The documentation for Supergrub [***_[COLOR="RoyalBlue"] is on this page[/COLOR]_***]("http://supergrub.forjamari.linex.org/?section=documentation"), and [***_[COLOR="RoyalBlue"]this page[/COLOR]_***]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") has a whole lot more information about these kinds of problems. Herman has a [***_[COLOR="RoyalBlue"]whole site dedicated[/COLOR]_***]("http://users.bigpond.net.au/hermanzone/") to dual booting setups like yours.

I'm actually on a lunch break at work, so I won't be able to look at this thread until much later, but we're all pulling for you, and one of us is going to be able to help you, I'll wager.

---

### Post by whiffy badger on 2007-10-20
Ok my best guess is that somehow my C partition containing windows has been corrupted and  I will also try to restore my C partition and use the super grub disk to boot to  it.  OH Gutsy what have you done!

---

### Post by renegade808 on 2007-10-20
I have the same trouble but I have Vista installed. If you want access to your windows partition without re-installing the back up I suggest using The Ultimate Boot Loader thats the name of the software package you can find it on the net you can use one of the numerous boot loaders on the disk I'm using it at the moment to boot into Vista until I find 
some other solution.
The Ultimate boot Loader is an iso file that you will have to burn onto CD then when thats done make sure your bios is set so you can boot up off a CD/DVD then use that to boot into
your XP  
Hope you find this helpful 
PS, this is my first ever reply:)

---

### Post by Alan Stancliff on 2007-10-22
> **whiffy badger said:**
> Ok my best guess is that somehow my C partition containing windows has been corrupted and  I will also try to restore my C partition and use the super grub disk to boot to  it.  OH Gutsy what have you done!

We're hoping all is working out for you. Please let us know what the upshot is.

---

### Post by whiffy badger on 2007-10-23
Thanks for your replies.  In short all my Windows partitions were corrupted, including the partition with my Acronis backup.  I used a paragon partition manager to chop and change my partitions under windows before installing.  I think this rather than Gutsy was responsible  for corrupting the windows partitions.  I was left with no alternative but to format my HDD and clean install Windows XP MCE again.  I will never use Paragon products again.

---

### Post by ebeard on 2007-10-23
This unfortunately is  a little late. 

My brother just tried a Fiesty install from live disk and it had an grub error 18. He decided not to deal with Ubuntu right now :( or flashing bios (to fix error 18 ), so he put in a windows disk and did a fixmbr. His c: drive went borky and after a little more fiddling it showed up as fat32 (was ntfs) and unbootable. One utility said the partition was unallocated. Clang-clang=buggered partition table. 

He was about ready to wipe and clean install. I remembered a program I used once to fix a buggered partition table. It is testdisk ([www.cgsecurity.org/wiki/TestDisk](www.cgsecurity.org/wiki/TestDisk)). It analyzed and fixed the partition table for me so he tried it (this was 3AM). You can get the Linux version to run using a Linux  live disk. Testdisk analyzed the drive cylinders and found the ones that were supposed to be ntfs, then fixed the table. Basically fixing the partition table saved him a reinstall (and some data loss). Testdisk is under GNU, isn't it great what opensource programs can do.

---

### Post by whiffy badger on 2007-10-24
Thanks for that Ebeard, it might come in very handy in the future!

---

### Post by stella2657 on 2007-10-24
> **whiffy badger said:**
> :(:(:(:(
On my laptop I already have Windows XP Media Centre installed. I fancied trying out dual booting with Gutsy Gibbon after previously trying out Feisty without major issues. Gutsy was certainly working fine but now after selecting Windows in GRUB - it crashes after a few seconds so I can't get into Windows at all now.  I used the 1st guided partitioner option when installing.  Thinking that I just need to restore the XP bootloader, I used a XP home recovery disk but I am not able to to get into recovery console to fixmbr and instead I get message up saying that my C drive is damaged or unformatted.

I am about to recover my windows partition by booting into acronis true image, the backup being on my D drive.  There is an explorer style view if you boot into Acronis and I can still see my Windows files do exist.  I urgently  need to get my laptop working again in windows, can anyone suggest what I can do to get windows booting again, otherwise I will have to restore with Acronis and I'm not sure that I will give gutsy another chance to create havoc.

Thanks!
hi i read a thread a while ago about this problem, it had more to do with windows bootloader being corupeted by the linux install - hope this helps.

---

