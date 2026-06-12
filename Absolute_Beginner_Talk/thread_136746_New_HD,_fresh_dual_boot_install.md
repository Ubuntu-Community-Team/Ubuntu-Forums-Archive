---
title: "New HD, fresh dual boot install"
date: 2006-02-26
forum: Absolute Beginner Talk
---

### Post by BobC. on 2006-02-26
Hello, I’ve been a member here for a while with the intention of dual booting Ubuntu and 
Windows but circumstances have prevented it ..so now’s the time but I have questions, no surprise I guess.

The system I have for this dual boot is an AMD Athlon 1700 (1.2 GB CPU )  It has
256MB RAM and it will have a brand new and unformatted 80 GB IDE Western digital
HD running at 7,200 RPM.  It has a 2nd HD (for file backups)  formatted for Windows98.

If any of these very fundamental questions below are located elsewhere please accept my
apologies for taking up space here and direct me there.......

I have the choice of Windows98SE or Windows XP Home and Ubuntu.  So my
questions:

1. Windows98SE or Windows XP Home for use with as a dual boot with Ubuntu?

2. (a) I understand I should load Windows first and format the entire Drive as (b) fat 32 is
that right?

3 Does this mean that Ubuntu will allow me to “take” some of this 80 GB space for its
own ( as in repartition)?

4 If that’s true How much of the 80 GB HD should I use for Ubuntu 50%, 25% or...?

5.  (a)What about a “Swap” partition, do I need it (b) If yes how big?   (c)Will Ubuntu do
this or do I need to do this in windows?

6. Since I’m only using one hard drive (a) does that mean the so called “boot loader”
should be loaded in the Windows C partition. (b) will Ubuntu offer this option to me as I
install Ubuntu?

Thanks for any help.

Bob C.

---

### Post by senning on 2006-02-26
1. It shouldn't matter.  As long as you're using fat32, either Windows is fine.  
2. Yes.  Windows installers don't like seeing if there are other operating systems around.  b) Probably, though FAT32 is limited to ~20GBs per partition, so you'll need four(ish)
3.  Yes.  It should be relatively simple, though be sure to read the partition screen carefully when it comes up.
4. It doesn't particularly matter.  A base Ubuntu install is maybe 1-2Gs.  Depends how much stuff you plan to install.  You'll probably want to keep most of your files in the FAT32 partitions, though, so they're mutually accessible and not taking up space on your Ubuntu partitin.
5. No.  As long as you're using FAT32, all your files will be accessible to both Ubuntu and Windows.  The part holding Ubuntu will probably be formated in EXT3, though, and that won't be windows accessible.
6. Ubuntu will take care of that.

---

### Post by BobC. on 2006-02-26
Thanks very much senning,

I'll give this a try .....It's a spare system so I risk little ..Now I gotta figure out the ISO burn stuff.

Bob C.

---

### Post by Bartender on 2006-02-26
Bob -
I did the same thing as you; a spare system and no valuable data on HDD.  Good way to go.  You've visited the hermanzone website for instructions on dual-boot, right?  XP may be different, but when I installed W2K I never saw an option to format in FAT32 so just did the whole drive in NTFS.  Following the hermanzone directions GRUB made a FAT32 partition for sharing between the two OS'es, and it also converted the half of the HDD that I gave it for Ubuntu & its swap.
If you can do the whole drive as FAT32 that would probably make a more flexible setup since the NTFS part of my drive is off-limits to Ubuntu (at least inasmuch as writing to it goes).
When following the hermanzone directions I gave Ubuntu half of the HDD.  It's up to you.  GRUB made a small swap file for me.  Since I was dinking with a 120 GB HDD I didn't care.  There are posts that talk about not building a swap partition, but I don't think that's advisable unless you have at least a gig of RAM.
When I was done, I didn't know what to expect.  I turned the PC back on, saw the typical BIOS displays, then got a GRUB window with choices.  If I did nothing, it would boot Ubuntu after waiting - um - five seconds, I think?  If you want to go to your Windows partition, you just stab the down arrow a few times then Enter.  No problemo
You'll like it.  You did read up about defragging the Windows partition first, right?

---

### Post by BobC. on 2006-02-27
@ Bartender, Thanks.

I did read the very helpful hermanzone website.

But I plan to format as FAT32 so I think I don't need a “Swap” partition, I have an 80 GB HDD and it seems I may need to use my Windows98 disk to do this.


@ Thread,
So I guess I need to use FAT32 and would like to split the HDD like ~ 40 GB for Windows and the rest for Ubuntu. Does this mean I want to format the entire HDD using my Windows98 disk first (for FAT32 over 32 GB limit) then install Windows XP on the entire HDD ...then install Linux (Ubuntu) and let it  take the remaining ~40 GB space? Is that the process?   I guess I DON"T need the small FAT32 utility i have been reading about if I do it this way? 

Thanks ......

Bob C.

---

### Post by RaiSuli on 2006-02-27
To my knowledge there is no 20 GB limit to the size of a FAT32 partition. I use an external 200 GB hard drive which has been formatted as a single partition with FAT32. Windows and Ubuntu have no problem with it. FAT32 has a limited folder size, however, I believe, it's 4 GB.

---

### Post by Bartender on 2006-02-27
[QUOTE=BobC.] Does this mean I want to format the entire HDD using my Windows98 disk first (for FAT32 over 32 GB limit) then install Windows XP on the entire HDD [/QUOTE]

Wouldn't XP just turn right around and format the HDD as NTFS?  I don't know...

Some XP/FAT32 links...

[http://www.abit-usa.com/faq/mb/2002031801.php](http://www.abit-usa.com/faq/mb/2002031801.php)

[http://www.theeldergeek.com/formatting_drives_using_xp_cd.htm](http://www.theeldergeek.com/formatting_drives_using_xp_cd.htm)

[http://kadaitcha.cx/format.html](http://kadaitcha.cx/format.html)

[http://support.microsoft.com/default.aspx?scid=kb;EN-US;310525](http://support.microsoft.com/default.aspx?scid=kb;EN-US;310525)

That last one looks interesting...from MS but lots of info

---

### Post by jason.b.c on 2006-02-27
> Wouldn't XP just turn right around and format the HDD as NTFS? I don't know...

quick answer, yes!!   i don't even think its possible to install xp unless the hard drive is formatted ( ntfs )

just install xp to your first partition and install ubuntu to the other one formatting as fat 32 at the same time!:)

---

### Post by munga_bill on 2006-02-27
> 5. (a)What about a &#8220;Swap&#8221; partition, do I need it (b) If yes how big? (c)Will Ubuntu do
this or do I need to do this in windows?
Just to clarify a little possible problem in terminology here:

_ A 'swap' area_ as used by Linux is a special area of the hard disk reserved for 'virtual memory'. Slow moving data from the memory can be written here, freeing up the faster RAM memory for high speed processes. A computer with very little ram can use a swap area as large as three times the size of its RAM, but any larger would be a waste of space. The amount of swap area is important if you don't have much RAM (eg, less than 128 mb. or 128 to 512 mb.) Over 512 mb of RAM, swap area size can be less, but even with 1.0 GB of RAM or more, a small swap area is still recommended. Maybe you can't detect the use of the swap area, but it still seems to improve performance having even a small one there for some reason. The best way is to let the Ubuntu installer decide automatically.

_A 'data partition'_, is a partition for storing files and folders. A fat32 'data partition', can be accessed by both Linux and another operating system with both read and write  abilities. I agree with RaiSuli, a fat 32 data partition can be any size if it is made by Linux, Windows can only make a 20.0 GB fat32 partition maybe, but Linux can make one bigger than the biggest hard disk ever invented, I think the hypothetical limit is somewhere in the several terrabyte range. Some people like a large 'data partition', for doing a lot of sharing between OS's, and some like only a small one, leaving more room in their operating systems for file storage with fast access. 
If your Windows system is on fat32 already, it's not really necessary to have a seperate data partition, but it would be okay to use one anyway, it might help keep your Windows data safe from viruses. 
Actually, my computer started with Windows XP home edition on fat32 on an 80.0 GB hard drive, so Windows must be able to make fat32 partitions bigger than 20.0 GB, I don't know where the 20.0 GB fat32 limit comes from.
Windows XP Professional is likely to be NTFS only, Windows XP Home edition (the one I have anyway), is fat32 by default for backwards compatability with Win98, but can be converted to NTFS at the user's option.

---

### Post by mparker on 2006-06-09
Bob,

I did mine this way. but i already had xp loaded.
resize the windows partition, leave it as ntfs, then in the free space make a swap, a linux and a fat 32 partition.

load ubuntu  and grub as the boot loader.

linux and windows can read the fat32 so i use that as a share between the two and i put my thunderbird profile there so mail is the same however I boot.

---

