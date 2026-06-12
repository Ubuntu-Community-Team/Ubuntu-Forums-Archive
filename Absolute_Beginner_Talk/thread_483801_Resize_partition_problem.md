---
title: "Resize partition problem"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-25
currently i want to increase my Windows Partition [SDA2] by 15GB
by decreasing my EXT3 [SDA3]

but! i can oln yfree up space AFTER my EXT3 yet Windows is BEFORE it.
i have attached a screen shot of my partitions.

im currently in the Live CD.

---

### Post by molly_001 on 2007-06-25
If ext3 is primary, and it looks to be, I believe you'll need to:
   1) get data off of your FAT16 - onto some external device or media as I assuming that it's not possible for you to slide it to the NTFS partition temporarily

    2) delete FAT16 partition

    3)  expand NTFS in its front end

    4)  put back a FAT16 again, but smaller

---

### Post by skymera on 2007-06-25
that FAT16, is a hidden partition on windows, its a Dell one.

and its only 40mb, thus making useless to me.

i want to use my EXT3, its got over 75Gb spare....

---

### Post by skymera on 2007-06-25
anyone else got ideas?

---

### Post by molly_001 on 2007-06-25
Roger, sorry -- I read 40GB not 40MB.

---

### Post by skymera on 2007-06-25
its quite importsnt, i ned to defrag windows (since i nver done it before) oops.
but requires 15% free space and i have 2%

i thought this would be quick and easy but its not

---

### Post by molly_001 on 2007-06-25
Time to get that external (or internal) DVD burner to use.
Copy over 2 DVDs worth of data to writeable DVD from sda2 ntfs.
That will free up your 15% (of 44 GB).
Borrow a friend's DVD burning device maybe.

---

### Post by carloslosgrande on 2007-06-25
Hi, I'm wondering if you're using the Ubuntu live CD to use GParted? The reason I ask is that I find that the GParted live CD is actually more powerful and can move and resize partitions more effectively. I am, however, a babe in the woods regarding this stuff so perhaps I'm barking up a different tree.

---

### Post by skymera on 2007-06-25
i have the Live CD.
i ordered them and dowloaded it.
ive moved My Documents from Windows Partition to my external hard drive.
freed up 10GB.

im doing a defrag to all of it.
so resizing isnt urgent, buty i would prefer

---

### Post by Orochi on 2007-06-25
Using gparted from the Live CD should allow you to safely move Ubuntu partitions. However do NOT move NTFS partitions around because Windows will most likely fail to boot. You SHOULD be able to use the Live CD and gparted to shrink the ext3 partition (freeing up space on the right of it) then move the ext3 partition over to the right (so that the free space is now on the left) and then expand the NTFS partition into that free space. Keep in mind that Windows has a lot of issues with resizing partitions and also that moving partitions around in general is not always completely safe. Definitely back everything up first in both OSes before you try playing with partitions.

When I tried to resize my dual-boot partitions, Windows simply could not handle a resize and so I had to backup everything and reformat. You may have to do the same if nothing else works.

---

### Post by skymera on 2007-06-25
when i go to reize, i can only free space AFTER the partiton. not before from which i need it to be.

i will resize windows, in windows.

i have PartitionMagic 8 which is good.

---

### Post by Orochi on 2007-06-25
> **skymera said:**
> when i go to reize, i can only free space AFTER the partiton. not before from which i need it to be.

i will resize windows, in windows.

i have PartitionMagic 8 which is good.

What I'm saying is create the free space AFTER the partition, and then try to move the ext3 partition right into that free space. (I'm not totally sure this will work, like I said I just decided to reformat instead of messing around with partitons too much).

Here's a little ascii art to explain what I mean.
* is ntfs
+ is ext3
_ is free space

Current partitions -> [**++++]
Resize ext3 -> [**+++_]
Move ext3 -> [**_+++]
Resize ntfs-> [***+++]

---

### Post by skymera on 2007-06-25
yes i understand that nice drawing.

it could work i will try when my external fdinsihes defragging.

thanks

---

### Post by Orochi on 2007-06-25
Make sure to back up all your data first!

---

### Post by floke on 2007-06-25
Whoah!
An easier thing to do might be to simply resize your ext3 partition and then create a new FAT32 or NTFS partition in the free space - then XP will pick this up and you'll be able to use it as a shared document or whatever facility between XP and Ubuntu - note if you go down the NTFS route you'll need to have the NTFS-3g thingy installed in ubuntu to be able to write to it - but it's very easy to setup.

** EDIT - Well you already have 4 primary partitions setup so this might be a problem unless you delete the sda1 thing - but I'm not recommending this since I don't know what its for **
** EDIT2 - If you don't want to delete sda1 you could: (a) backup your extended partition data; (b) delete it; (c) resize ext3; (d) create new extended partition in the free space; (e) recreate your deleted partitions from step (b), and create the NTFS/FAT32 partition here.

---

### Post by skymera on 2007-06-25
the SDA1 is a hidden partition put by dell.

and im cureently in Gparted in LIVE CD.

ive put 20gb AFTER linux partition.
but i cant seem to move it into it, freeing uop 20gb before.

---

### Post by floke on 2007-06-25
Moving in Gparted on the liveCD hasnt worked for me - the rescue disc version does but it takes a very long time. Try using the steps outlined in my last post to delete and then recreate your extended partition - an extended partition is a partition that you can subdivide to your hearts content - so this way you can have an NTFS/FAT32 partition within it with no problems.

---

### Post by skymera on 2007-06-25
i can only create Primary Partitons...

o well, i'll survive with my external.

thjanks for all the help

---

### Post by floke on 2007-06-25
An extended partition is a primary partition.
You shouldn't be able to create any new partitons ATM since you already have 4 primaries! 
That is why you need to delete one first - the extended being the best candidate since it can be recreated on a larger scale - and new partitions created within it - once you resize the ext3 partition.

---

### Post by skymera on 2007-06-25
o dear.
i deleted SDA1, and now Windows dosent boot.

missing hal.dll

s*** :(

---

### Post by skymera on 2007-06-25
ok now i have a REAL problem...
and no ones helps..

please guys, and ladies

---

### Post by floke on 2007-06-25
> **floke said:**
> Whoah!
Well you already have 4 primary partitions setup so this might be a problem unless you delete the sda1 thing - but I'm not recommending this since I don't know what its for 

And that's why!
Got a rescue disk?

---

### Post by skymera on 2007-06-25
yes, i have a Windows XP disk.

what shall i do? boot from it???
i dont want a new install i want that file back

---

### Post by floke on 2007-06-25
No idea.
I would do some googling on this before installing anything else!
On the positive side, though, you've not lost any essential data since you can always access your XP partition from inside Ubuntu. That probably doesn't help much ATM, but its worth bearing in mind.

---

### Post by molly_001 on 2007-06-25
The famous missing or corrupt hal.dll error ...

1)  Use your Windows Installation disc (must be from Dell, and must be purple)
2)  Use it and follow the instructions here below the red line
[http://www.michaelstevenstech.com/XPrepairinstall.htm](http://www.michaelstevenstech.com/XPrepairinstall.htm)

---

### Post by skymera on 2007-06-26
yes i booted up windows from disk,
but there was no repiar option!!

and now windows boots up automatically, i cant choose to boot ubuntu.
at the moment im running live CD.
do i have to edit boot file to choose what i boot???

hmm this is not my week :(

---

### Post by molly_001 on 2007-06-26
You didn't go deep enough into the dialogue of the CD.

Start up the machine from CD (make sure your BIOS is set to boot the CD before booting the hard drive)

Go through all options *as if you are going to install Windows on the current NTFS partition* .  It might seem you are going to wipe out all your data on that partition.

But when you get to the page which asks you to install Windows on the current partition, there will also be a Repair installation option.  (letter 'R' )

---

### Post by skymera on 2007-06-26
i got to the stage where it said something like continuing will erase data.
i think.

i have a backup of my documents, but thats not really point.

also, i went through my ubuntu CD to my Windows partiton and looked in system32 and hal.dll WAS there!!!
maybe its looking in the wrong place.

but why cant i boot up ubuntu?
it boots windoze automartically

---

### Post by skymera on 2007-06-26
anyone else have knowledge?
please share

---

### Post by molly_001 on 2007-06-26
You cannot boot Ubuntu because you overwrote GRUB when you fiddled with the installation disk yesterday or the day before.

hal.dll is almost always present, despite the hal.dll "missing or corrupt" error.  And, it's even usually not corrupt.  But alas, this is Windows.

If you want to load Windows without re-installing entirely onto the partition, you are going to need to do boot into the DOS Windows Recovery shell -- using the Windows XP install disc you received from Dell.

So, boot up on the CD, and choose 'R' for Recovery Console.
Then, [read all of this page]("http://www.kellys-korner-xp.com/xp_haldll_missing.htm").  That page of instructions has always worked for me in a missing hal.dll situation.  However, you may have to try all four options in order, to hit upon the one which will work in your particular situation.


Of course, you can always just reinstall Windows onto the current NTFS partition, since you said you have a backup of your documents.

---

### Post by skymera on 2007-06-26
yeah i backup documents.
not all my programs. they can be restored i know.

how do i sort my GRUB out then?

im so sorry!!!

this is why 15 year olds shouldnt fiddle :P

---

### Post by skymera on 2007-06-26
ok final problem.

thanks for that link i printed it out now.
hopefully get me windos sorted out.

but now GRUB, is it simple to sort out?

---

### Post by molly_001 on 2007-06-26
1) After you fix the hal.dll issue, completely, so that you are able to get Windows to boot and load its Desktop ...

2) You will need to reinstall Ubuntu onto its primary ext3 partition, and of course let it lay down GRUB for you, at the end of its installation.

However ...
3) before doing #2 above, but only after completing #1 ... I would burn an .iso of GAG Boot Manager and install it to the MBR.  Just follow its instructions -- it has saved me on many occasions in situations like yours.  When it works, it works great.  If it is able to detect the partitions which are bootable, then it will install an iconic sort of "menu" for you which is the first thing you will see after BIOS.  It has a button interface ... press the Penguin button to boot into Ubuntu, press the Flying Windows button to boot into Windows, etc.

Good luck with it.

---

### Post by Orochi on 2007-06-26
You don't need to completely reinstall Ubuntu just to fix GRUB. Once you have XP working properly, follow the instructions here: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp) to reinstall GRUB (you'll need the Ubuntu LiveCD).

---

