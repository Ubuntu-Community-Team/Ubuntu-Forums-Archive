---
title: "A little bit confused"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-11-14
Hi folks!

I have some technical problems with one of my HDDs (the one I have Ubuntu installed upon), I feel like it's dying so I have to reinstall both Ubuntu and Windoze (which I unfortunately need to keep for school assignments... they want us to work in either Borland C++ 3.11, ok, or M$ Visual C++ 6, yuck !). 

The problem is that I now want to put Ubuntu on my other HDD (which I believe to be a little bit more "safe"), which is seen in my BIOS (Compaq Computers Corporation Setup Utility, or so it reads in the title bar) as "IDE Primary 0". The faulty HDD is seen as "IDE Secondary 0".

I know that the "IDE Primary 0" HDD is the Master one, and that the "IDE Secondary 0" HDD is the Slave one.

(I also have 2 CD-ROMs which are labelled by BIOS as "IDE Primary 1" and "IDE Secondary 1", but I don't think that's important.)

Alright so here's the situation now:

IDE Primary 0   - partition 1 - FAT32
IDE Secondary 0 - partition 1 - NTFS
IDE Secondary 0 - partition 2 - EXT3

And the desired situation is:

IDE Primary 0   - partition 1 - EXT   (for my Ubuntu install :D)
IDE Secondary 0 - partition 1 - FAT32 (for Windoze, yuck)
IDE Secondary 0 - partition 2 - NTFS  (for other personal files)

And that brings up the question: at a fresh install of both XP and Ubuntu, will it be possible to meet the configuration above ? I mean, I've lost count of how many times I installed Windoze before, but I only did it on my Master HDD, not on my Slave HDD.

The reason I wanna do this is that I have to install Windoze first and Ubuntu second for keeping the MBR ok, and the reason for "switching" the HDDs at this particular install is that my actual Slave HDD is the one that's dying...

I hope I got it clear and straight and I really hope you could help me get past this problem, because I'll start my re-install as soon as I get home (I'm at school right now) and if I mess up something I won't be able reach the forums...

Thanks in advance,

LLRNR

PS - I'd also like to know what do you recommend for doing something more than a mere format, I mean I'd like to know if it's possible to isolate the bad clusters by some kind of a special maneuvre / tool. Because if I do a simple reformat, I guess the bad blocks will just do their game again and ruin all my work in a couple of days... :(

---

### Post by monkieie on 2006-11-14
Does this help?

[http://www.ubuntuforums.org/showthread.php?t=286303&highlight=format+drive]("http://www.ubuntuforums.org/showthread.php?t=286303&highlight=format+drive")

Concerning your drive problem, have a look at this; I have never tried it but it may be worth a shot...

[http://www.linux.com/guides/sag/x1079.shtml]("http://www.linux.com/guides/sag/x1079.shtml")

---

### Post by Average Joe on 2006-11-14
I would say that it would just work fine. Worst case scenario is that Windows doesn't want to install on a slave disk, but I don't think it will be a problem. If it is, then you could maybe temporarily uncouple your master disk, and make your current slave a master disk just for the installation of Windows.

I wouldn't no any good tools to isolate bad clusters etc. Maybe the default Winodws disk check (chkdsk) has some options for that. I would also recommend to make your Windows partition NTFS. I think even Microsoft recommends that for disks bigger than 500 MB. If Windows insists on installing it on FAT32, you could use the convert command in Windows after the installation to make it NTFS. Having less defragmented files is probably better for your (crappy) hard disk.

---

### Post by LLRNR on 2006-11-14
Thanks for the tips ! I read extensiveley so this is what I came up with... Please check and see if it looks ok, I really need to get the thing started, I got my hands on a tool made by the manufacturer of my faulty HDD and they claim it's gonna take o long while... I actually feel _jailed_ without a working PC :(

So here's what I've been thinking about:

IDE Primary 0 - Ubuntu :
partition 1 - ext2 (for /boot)
partition 2 - swap
partition 3 - ext3 - root partition
partition 4 - ext3 OR ntfs ??? - for /home

IDE Secondary 0 - WinXP and general-use files :
partition 1 - ntfs (for Windoze...)
partition 2 - ntfs ??? for general-use files (documentation, books, music) - if the filesystem is ntfs, I will be able to access the files in this partition from both Ubuntu and Windoze, right?!

I don't know if I figured this right, so I'm asking for your help and patience, I should start right away (lol it's 8 pm here and I don't think I'll get more than 2 hours of sleep this night hahaha :lol:)

LLRNR

---

### Post by CatKiller on 2006-11-14
**DON'T** use NTFS for your Home partition. Just... don't.

And for storage accessible to both Windows and Ubuntu, FAT is probably a better bet. You'll need to hunt down the ntfs-3g howto if you want to experiment with writing to an NTFS partition from Linux. You can read NTFS OK straightaway though. For that matter, there's a driver to allow you to use ext3 partitions in Windows, so you can have a sensible filesystem instead.

---

### Post by LLRNR on 2006-11-14
Thanks CatKiller... I thought it's not good to use NTFS for the /home partition, but I just wanted to be sure; I'll happily use EXT3 instead. 

And for the last partition which I'd like to be accesible to both Ubuntu and XP, it's ok if I use NTFS if I just want to _read_ from Ubuntu, right ? (Like reading lots of PDFs and listening to music)

I've been advised not to use FAT32 on a crappy HDD, so I guess I'll just go with the NTFS for IDE Secondary 0, 2nd partition, huh? :-k 

LLRNR

---

### Post by CatKiller on 2006-11-14
> **LLRNR said:**
> And for the last partition which I'd like to be accesible to both Ubuntu and XP, it's ok if I use NTFS if I just want to _read_ from Ubuntu, right ? (Like reading lots of PDFs and listening to music)

Yes, although you'd be surprised how frustrating it can be to not be able to rename your music files.

> I've been advised not to use FAT32 on a crappy HDD, so I guess I'll just go with the NTFS for IDE Secondary 0, 2nd partition, huh? :-k

NTFS isn't going to make a crappy hard drive magically non-crappy. If you don't trust it for FAT, then you probably shouldn't trust it with your data. Just my £0.02.

---

### Post by LLRNR on 2006-11-14
OK, all of you, thanks a lot for your good advice. I now _think_ lol that I know what I'm doing. Now seriously, it rocks to have all you great people around :) Keep it goin' ! I certainly will.

So there I dive in some long frustrating hours of chkdsk and Maxtor PowerMax stuff, and afterwards I might have a working system with Ubuntu on top, on the good HDD at last !

It it all turns out well, I'll catch you later in a few hours, guys!

LLRNR

PS - **My** advice: DON'T EVER BUY MAXTOR if you care about yourselves... :mrgreen:

---

### Post by Average Joe on 2006-11-14
I haven't encountered any problems using a NTFS partition as a shared document partition for Linux and Windows. I use the ntfs-3g package. There is not so much to "hunt down" in my opinion. Just install it and change one line in your /etc/fstab file. I know that it is still experimental, being beta and all, but it works perfectly fine for me. I am sharing my Firefox and Thunderbird profile, music, pictures, etc. between the two OS's. That's why I recommended it.

But of course the FAT32 file system is natively supported by both Linux and Windows. I guess that could make it more reliable in that sence. It is just not such a clever file system.

Another option would be to use the ext3 file system for your sharing partition and install the ext3 driver for Windows. That gives you full access to your ext3 stuff under Windows as well. But I have had some issues with that. I had some folders I could not open any more under Windows, and the ext3 drive letter did not show up with Picasa, my favorite picture manager under Windows, so a had no access to my pictures with that program.

I hope you will make the right decision for yourself, whatever it may be.

---

### Post by LLRNR on 2006-11-14
Hi there! Well my plans didn't turn out to be just right, for I used the diagnosis tool provided by the HDD's manufacturer and... well... it magnificently failed with a "nice" looking error message telling me "This hard drive is FAILING. You should replace it as soon as possible and backup your..." blah blah. Fortunately I already did that. Oh and when I then tried to re-boot, my BIOS just couldn't see the HDD anymore, ain't it cute ?!

So now I'm stuck with a good working but kind of small HDD of 20 GB. Right now I'm finishing my Windoze install (5 GB FAT32), yuck, you know, A/V, firewall, this sort of things... :(

Anyways, the good part is that the remaining 15 GB are entirely for Ubuntu :D and as soon as I finish setting up the CrapOS, I'll pop in the Ubuntu Live CD and start rockin' again !! (Wow I now find out that I'm actually _dependent_ of Ubuntu, you can't imagine how miserable I feel right now using XtraPain again)

The thing is, I'd like just as reminder to know what to do when I'm prompted to choose where to install GRUB, because at the last install (which was the first, by the way) it was simple, I simply chose the primary HDD and things were ok, but now I'm using the same HDD for the dual boot... :oops:

LLRNR

PS - Oh my God how did I forget that ?! You GOTTA hear this: as a student in the CS department in my University, I get the *cough* honor to benefit of a program called MSDN Academic Alliance, which provides each student with the opportunity to have M$ software for free... Hey but check this out: this XP install was in fact the second one from their CD, this being the most legal thing I ever did in my life, I never paid a cent for software, and when I finally got Windoze going it tells me that I have to activate it by PHONE, because they magically determined that I used the serial before, you know, like... MY OWN serial !! So there I was at 2am making phone calls to the local number of a M$ Center, which was, as you might have guessed, closed at that time, so the kind robot redirected me to another center, an international one... Geez! I don't even wanna imagine what the cost of the phone bill will be, I finally managed to get the M$-moron-consultant or whatever he was to understand the situation and he finally gave my another activation code... I swore to myself never to use MSDN AA products ever again, I might as well turn back to my pi*ate CDs, 'cause damn! I still need Windoze for school stuff and for my temporary job (by the way, did anyone manage to get Macromedia Flash 8 to run under Wine? I know it's possible for MX, but I need _precisely_ version 8... my boss loves it :-? )

PPS - Oups :) Sorry for the long post, but I couldn't help myself.

---

### Post by LLRNR on 2006-11-14
In fact, to be honest, the first time I installed Ubuntu I used the alternate install (I think that's the way it's called) i.e. NOT the Live CD and I had to manually choose where to put GRUB in. I suppose it's the same thing with the Live CD and I'm not actually sure, but I think it would be ok to put it in the partition with the Windoze, huh ?! :-k 

(I now only have 1 HDD, yey !!)

Thanks,

LLRNR

---

### Post by Average Joe on 2006-11-15
Too bad you couldn't save your second hard disk. But it seems like you have found a good solution anyway. I am curious how you have handled the partition to which you want read and write access from both Ubuntu and Windows. Is it FAT, NTFS, or ext3 (or non-exsisting)?

O, and I have put my GRUB on the MBR (master boot record) of my hard disk. I think that's default when you have one hard disk and multiple OS's. But maybe it will work as well on the boot section of your first partition (Windows).

---

### Post by LLRNR on 2006-11-15
Hi. I'm back... finally! So here's how I set up my 20 GB:
- 5 GB for Windoze... ;
- 2 GB NTFS (I only want read acces from Ubuntu, it will be a placeholder for important docs and my work) ;
- 1 GB for swap ;
- 9 GB ext3 for / ;
- 2.5 GB or so (the available rest) for /home.

I think that would do for now, until I manage to get a new HDD. And wow it didn't even ask me where to put GRUB in (as I recall from my previous install with the Alternate CD, not the Live one, I had to choose where to place it... now it did this itself) !

Thank you all so very much for all your help, I now solved my problem!

LLRNR

---

