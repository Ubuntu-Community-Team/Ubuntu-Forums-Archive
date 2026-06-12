---
title: "Windows XP/Ubuntu Dual boot, plus common files"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by Sunni on 2007-06-16
Hey guys, I'm just starting off with Ubuntu and was wondering if people could offer me some support with what I wish to do.

I'm going to be installing Ubuntu on my laptop. I'd like to do a dual boot for the time being with Windows XP. I'd also like to have a third partition with my files/documents.

I've tried the live CD and it works well on my laptop. All my hardware gets recognised.

I've got an 80gb hard-drive in my laptop.

Here's a few things I'd like to ask questions about:

1. Firstly, any easy guide on how to setup an XP and Ubuntu dual boot?

2. I want to make three partitions. One will be NTFS for Windows XP. Second will be whatever filesystem Ubuntu uses for Ubuntu. The third partition I want for common files - i.e. media files (mp3s), videos, documents (openoffice files) etc. How do I go about doing this? The third partition for the files - what file system should it be and how do I make this partition? As an example, if I'm working on a particular .doc file in openoffice in Ubuntu and in Microsoft Word in Windows, I want to be able to open the file up in either OS, edit it, save it, etc. How would I do this?

3. Knowing I've only got 80gb, roughly how would you recommend I split this up? How much space will Ubuntu with perhaps a few extra installed programs take up? Would 15gb do for the Ubuntu partition?

That's all for now. I'll be starting completely fresh, i.e. I can do a clean format of my hard-drive and install either OS first. A step by step guide on what to do to achieve my goal of a three partition and dual boot setup would be most appreciated :)

Thanks.

---

### Post by drowner on 2007-06-16
Install Windows first. You don't need to fresh install if you don't want to, but you can. If you don't, then defragment several times

[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) <-- for installing with the livecd

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) <-- for installing with the alternate CD

2. Ubuntu will use the ext3 file system. You can make a 3rd fat32 partition, which both systems will be able to read and write. Ubuntu will read NTFS no problem, and now, using some technology called ntfs-3g, can actually write to it too. But a fat32 partition for document storage is easiest, to start with.

3. [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) <--- planning your partitions. I've only got 30gig, so its no problem with 80! You will need about 6-10gig to install ubuntu, max, and then your data. I don't know how much windows XP needs, probably about 20gig? So the rest could be data if you wanted. Oh, and you'll need up to 2gig for a 'swap' partition!

I hope they help

---

### Post by Sunni on 2007-06-16
Hey drowner, that was great. The third link really explained exactly what I was asking about.

But I now need to ask...

What is the best option for the "common files" requirement?
1. Make a FAT32 partition.
2. Make an NTFS partition and use NTFS-3G.
3. Make a /home ext3 partition and use "Ext2 Installable File System for Windows"

Are there any disadvantages with any of these methods? Obviously FAT32 has its problems. Option 2 seems like a good option but are there any issues with using NTFS-3G? (Is NTFS-3G reasonably fast at writing to NTFS partitions?)

Thanks!

---

### Post by drowner on 2007-06-16
Well, you are right about the problems with FAT32, but I suspect for plain data storage, it should function OK.

I don't run windows, and have never used ntfs-3g or the windows ext reader, so I can't comment. Peroonally, I think the fat32 option is probably the easiest to begin with. Provided you shutdown correctly from windows especially, you shouldn't have any troubles.

Does anybody else have advice?

---

### Post by drowner on 2007-06-16
> **Sunni said:**
> Hey drowner, that was great. The third link really explained exactly what I was asking about.


Indeed.

psychocats and herman are brilliant.

especially herman, who is australian like me, and whose advice i followed for my first ubuntu (breezy badger)

:D

---

### Post by wataboutbob on 2007-06-16
Hi.

I've been using ntfs-3g extensively and I've never run into any problems with it - by way of data loss / corruption. They've really come a long way in terms of stability.

As for your 80 GB HDD, this would be my recommendation.

If you only install Windows + Office 2003 + Photoshop + KL Codec and no games, a partition size of 10 GB is more than adequate (I only use 8 GB myself of which 3.5 GB is still free) Ofcourse, once installed, right-click on My Documents and move your folder to another partition - say D: (that way your files are also secure)

So;

hda1 = c:\SYSTEM => 10 GB NTFS
hda2 = d:\DATA => 60 GB NTFS
hda3 = about 9 GB for / and /home in ext3 (remember, files are being saved in d: anyway)
balance for swap.

for Ubuntu, about 8 GB is reasonable I think. Its my main OS so any torrents I download I save it in its native partition before moving it to the DATA ntfs, so thats why I've given it more space than Windows. Adjust if you feel otherwise.

Good luck.

---

### Post by Sunni on 2007-06-17
JazakAllahu Khair wataboutbob - I'll work with those partitions, and I'll try an NTFS data partition with NTFS-3G.

Sorry my questions will end at some point I'm sure... but:

If I were to install apps for Ubuntu, where would they be installed to - I would assume to the /home partition? (Or the NTFS data partition?) Just asking because I was thinking of splitting the ext3 + /home partition you suggested in to two partitions - one for the OS, and another for the /home, so I can easily upgrade the OS plus install any additional apps on the /home partition. That sounds okay, right?

And finally... Is there anyway to have one app for both OSs? For example, I'm happy to use OpenOffice on Windows and Ubuntu. Is there anyway I can use one installation in both OSs? Or would I have to install two instances of the software?

Thanks once again.

---

### Post by drowner on 2007-06-17
Hi again.

If you want to use openoffice under windows and linux you will need 2 openoffices.... linux and windows use entirely different programs.

linux programs are not 'installed' to a place like windows programs are... you wont choose where they go as such, linux will put them in the place programs are meant to go.... but say a 10-15gig partition for linux will be MORE than enough for as many apps as you are likely to install, and if your data is going to be saved on the NTFS partition, then your home partition wont need to be big either.

[http://www.arsgeek.com/?p=520](http://www.arsgeek.com/?p=520)

That gives you a decent overview of the filesytem, if you are curious

---

### Post by Sunni on 2007-06-17
Thank you drowner, you've been great help. I appreciate it :)

Gonna go ahead and set it all up now!

Sunni.

---

### Post by wataboutbob on 2007-06-17
> **Sunni said:**
> JazakAllahu Khair wataboutbob - I'll work with those partitions, and I'll try an NTFS data partition with NTFS-3G.

Sorry my questions will end at some point I'm sure... but:

If I were to install apps for Ubuntu, where would they be installed to - I would assume to the /home partition? (Or the NTFS data partition?) Just asking because I was thinking of splitting the ext3 + /home partition you suggested in to two partitions - one for the OS, and another for the /home, so I can easily upgrade the OS plus install any additional apps on the /home partition. That sounds okay, right?

And finally... Is there anyway to have one app for both OSs? For example, I'm happy to use OpenOffice on Windows and Ubuntu. Is there anyway I can use one installation in both OSs? Or would I have to install two instances of the software?

Thanks once again.

you're welcome Sunni. I've just come off a marathon reinstallation session with Vista for my laptop. While I can certainly appreciate the improvements MS have made with the OS (in terms of speed of operation and a general polished look) seeing that my main OS is Ubuntu, there was no need to give Vista a 15 GB partition when my XP only took 8 GB, so I went about removing it and putting my Partimage backups of XP and Fiesty.

For the question regarding your application installation and /home folder - yes, it will help having a seperate /home folder when you're upgrading your OS. And with Ubuntu, seeing that we can expect Gutsy to be released in Oct 07, that's probably a good idea.

As Drowner already mentioned, you'll need to install OOffice seperately for both windows and Ubuntu. Under linux, OOffice comes installed so I still say that even with XMMS, Zekr (a very good Quran research tool), Opera, Amarok, Google Earth, Picassa and Thunderbird, you'll only need about 10 GB maximum - but nothing wrong in giving more space for future eh?

Insha Allah, everything will be good for you. Welcome to Ubuntu.

Habeeb

---

### Post by whistle on 2007-06-18
@wataboutbob

I thought partimage support for NTFS was only "experimental?" Did you run into any errors when backing it up?

---

### Post by wataboutbob on 2007-06-18
> **whistle said:**
> @wataboutbob

I thought partimage support for NTFS was only "experimental?" Did you run into any errors when backing it up?

yes, that was a scary moment when it said "experimental" But it worked and I have been able to restore both the Windows SYSTEM partition as well as Feisty's / with it without errors.

However, seeing how Norton Ghost 2003 makes a nice image size of only 1.7 GB versus 2.4 GB for partimage, I might go the way of Ghost if space became an issue... hmm... I wonder if Ghost 2003 can make / restore an image of Feisty's ext3 without errors.

---

