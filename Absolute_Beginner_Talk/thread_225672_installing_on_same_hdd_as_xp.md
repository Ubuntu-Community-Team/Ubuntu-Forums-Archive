---
title: "installing on same hdd as xp"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-07-30
Hi people
        Been trying out live cd this week BUT am lacking the confidence to try install it.
I have 2 hdds in here..One is a 40g seagate which has my xp on it but we dont really store anything on our pc`s so 2 thirds of it`s space is unused(it`s all one big partition..38g with 2g unallocated on the end of it(dont know why?).
Theres also a tiddly little 3.2g disk in there that i had took out old pc just to see if i could install a spare ok(empty)
I`ve already gathered that the 3.2g disk is not big enough on it`s own to install unbunto So could someone comfirm just how safe it is OR is`nt to use the GPARTED tool to resize the seagate (with xp) down to about 30g so i could use the spare 10g for unbunto.
Whats the chances of it messing my xp up?.
No xp cd`s(my copy is ON the pc in the 1386 directory)(got a copy of THAT though)
I believe i KNOW what to do BUT just lack the confidence to jump in.
If somebody could give me just a bit of a push in the right direction i reckon i`d manage.THANK YOU for any time & help

---

### Post by xpod on 2006-07-30
PLEEEEEEEASE!!!
This is the second time in a week i think ive posted for a bit of advice in helping this pc newcomer.
If my requests are being ignored because "the answers are out there" then please know that i have read & read & read till my head is sore.

As i stated ...i DO know what i need to do(as per instructions)BUT having read so much on the subject i am now really weary about doing anything that might kill xp.

PLEEEEEASE....SORRY for being a persistant git but this helpless scotsman could really do with some help..cheers(again)

---

### Post by ProjectGod on 2006-07-30
you need to resize your one HUGE NTFS window partition with another software... not GPARTED. 

i suggest you use Partition magic. its cool. i think you can get a demo version which works for a few days.

anyway. what you do is resize your windows. before doing so just make sure you backup all of your important data to DVD or something. 

yeah so i was saying. resize your NTFS with partition magic and leave about 10-15 Gigs (if possible) for your ubuntu. after resizing you need to remove all FS formating on the 10-15 gig so you have "un allocated" space. then install ubuntu into that... just install GRUB into the MBR when prompted to. you can then dual boot!

besides this i think 3 gig is enough for ubuntu to fit into. that is if you just want to learn and not actually download music videos and other software.

cheers

---

### Post by impeachw on 2006-07-30
You can put it on the 3.2. Try it.I'm running it now here on a 4.0.,It only takes 2.0. Flawless install. If you load it on the 40 back up your work first. Usually works, may not, for win is somewhat corrupt after a time. If you want to keep win get another 20 or 40 and ghost it first, just to make sure. If your only restore is on the h/d, and you really want to keep it get another 20 or 40  h/d for Linux. Theyre only about $30.:cool:

---

### Post by Herman on 2006-07-30
>  No xp cd`s(my copy is ON the pc in the 1386 directory) Is there a way to make it into a Windows install or a Windows 'Recovery' CD?
My Acer notebook had a restore partition in it and there wassome instructions somewhere to follow to make a 'Recovery' CD from it.

If you can do that, you should be *relatively* safe. 
GParted LiveCD is great partitioning software, I use it all the time and I have never had any problems with it at all. GParted is compatible with Ubuntu and other Linuxes which use the 'Parted family of partitioning softwares. The version that's in the 'Desktop' Live/Install CD has caused the odd problem here and there which we read about here on the forums. For the number of new users installing the percentae of problmes would be relatively small though.

We really don't know what problems commercial sofwares have because the information is not publically available on any open forums, but there is no reason to believe that just because you have to pay for them that they are any better at all. Refer to the following link: [http://www.computergripes.com/PartitionMagic.html](http://www.computergripes.com/PartitionMagic.html)

There is no such thing as totally risk free disk partitioning software. It's the same as everything else in life. You need to *manage your risks* so that even if something does go wrong, you'll be okay.  Before disk partitioning and installing operating systems, as long as you have all your software and data backed up so that you can re-install it all again you'll be fine. The chances of something going badly wrong are slim, but they are still there.

Partition Magic not recommended for use with Linux filesystems. I recommend GParted.

Regards, Herman :D

---

### Post by jason.b.c on 2006-07-30
> **ProjectGod said:**
> you need to resize your one HUGE NTFS window partition with another software...  

i suggest you use Partition magic. its cool. 

anyway. what you do is resize your windows. 

yeah so i was saying. resize your NTFS with partition magic and leave about 10-15 Gigs (if possible) for your ubuntu. after resizing you need to remove all FS formating on the 10-15 gig so you have "un allocated" space. then install ubuntu into that... just install GRUB into the MBR when prompted to. you can then dual boot! 

cheers

I would highly advise against that...!!!!

That is how i recently lost windows 2000...!!!   Trying to do it that way , And i'm positive that i did everything correctly..!

No , Just get yourself another hard drive , Just to be safe...

---

### Post by andrew_stoned on 2006-07-30
There would be no problem with putting Ubuntu and XP onto the same harddrive. Just make a backup of your HD (better safe than sorry), resize the windows partition down by about 10GB using GParted on the LiveCD. With the second hard drive, why not partition that into two and use on for the linux swap file, and the other for to put the paging file (virtual memory in windows, basically the same as the paging file) on so it does not clog up your main drive.

---

### Post by xpod on 2006-07-30
Thanks people.
I should have mentioned that the reason i assumed it would`nt fit on the smaller drive is i tried...(plus others reckon 10g)
Anyway it only seems to get to stage 5 then freezes.I`ve left it for hours but it dont move.
Once it actually got to the next stage where it listed what partitions it was going to create BUT again it had froze and nothing further happened.
My disks are actually formatted to fat32 (even the HUGE one.).
As far as making a recovery cd with that 1386 directory(xp setup)is concerned THAT too has been one of my recent "must learns".
I have been trying out the instructions on "slipstreaming" your copy of XP with sp2 but most sites talk of copying from a disk first.Im not entirely sure if my 1386 copy is the same thing.
I have learned to redirect the sfc /scannow function to retrieve files from 1386 SO i suppose it is the same..(instructions for integrating did`nt seem to work though).
Surely if anything went wrong i could use a bootdisk with the copy of 1386 i have on a disk..NO???

I will try again with the smaller drive but i know it`s going to do the same SLOW RIGHT DOWN AND JUST STOP(even clock stops).
So if anyone knows a way round THAT then i`d be really gratefull

THANK YOU ALL for the much needed input.

PS....so what is it....TO GPART OR NOT TO GPART???????

---

### Post by xpod on 2006-07-30
PPS.......I should have mentioned im a complete PC newbie NOT just linux.
BUT in my short 6 months i have managed to learn a fair old bit considering ALL the problems from BSOD`s,dodgy drivers,dodgy bios settings...I`ve reinstalled our kid`s m.e from the copy on disk,And ive De`hyjacked BOTH our xp pc and our m.e pcs AND they both work like new(sometimes)
So i can follow relatively verbose instruction BUT still have problems when it comes to stuff i aint done before

---

### Post by Herman on 2006-07-30
> I should have mentioned that the reason i assumed it would`nt fit on the smaller drive is i tried...(plus others reckon 10g) I have installed on half a 6.0 GB hard drive (3.0 GB for Ubutu) many times. Ubuntu might be able to be installed as small as 2.0 GB, it think it would actually occupy about 1.8 GB of that.
> Anyway it only seems to get to stage 5 then freezes.I`ve left it for hours but it dont move.That shouldn't be happening. How much RAM does your computer have? 

Perhaps, if it has less then 256 mb, you would be better off using the 'Alternate' Install CD? And maybe even installing Xubuntu rather than Ubuntu. That will work better in systems with less RAM. Ubuntu will work okay as low as 127 mb ram though, as long as you can install it. GParted doesn't need much RAM on its own, but combined with the other software it'd running with, you could be running out of RAM.

 That used to happen to me in the PC Chips 'Book PC' there pictured in my avatar, but only when running the operating system installed GParted and issuing the 'swapoff' command.

andrew_stoned's tip would be really worth doing if you are in the low RAM end of the scale. Swap area is a great thing in Linux and makes low RAM computers work really well! Having your swap on the other disk means you will be splitting the work between two sets of read/write heads in your hard disks, so it will make your performance much faster!

Here's a couple of links that I hope will help you by explaining some of the basics, the first is by myself, mainly about using the 'Alternate' install CD,[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
 and the second is by aysiu, who you'll also see helping here in the forums.   [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) 
Those might help you , I hope. I need some sleep badly right now... be back sometime later... All the best, and good luck with it, Regards, Herman :D

---

### Post by xpod on 2006-07-30
That has been yet another problem..Although the stick of ram in here says 256 on the side it actually only shows up as 224mb in my pc OR even checking via everest.
I am going to get more but everything (xp)works so i aint had a real problem in that department.

I know your tired herman so goodnight my friend.I will check out your links.Thanks.

If anybody else has their two bob`s(OR 2 bit`s)worth im all ears.
I dont know why but my main drive actually has nearly 2g unallocated space on the end of it.This pc was bought new a few years ago so i dont know why it had dodgy amount`s of memory and little unallocated spaces on the end of it`s own hdd??

So all in all i have nearly 5 g of space WITHOUT touching the big(relatively)XP partition.

I`ll go and try install again on the smaller hdd.....Im using unbunto at the moment and it works good & fast online BUT is really slow opening things within itself...

---

### Post by Herman on 2006-07-30
Table 1 Recommended Minimum Requirements 
> Install Type        RAM          Hard Drive Space 
  Desktop       256 megabytes      3 gigabytes 
   Server        64 megabytes    500 megabytes  I don't know for sure if this is your problem or not, but you are running just under the borderline for the amount of RAM you need for the 'Desktop' Live/Install CD to function correctly. I am sure that Ubuntu will work fine as low as 128 megabyytes of RAM once you get it installed, especially when you get a swap area made on one of your disks.
If you don't have to pay extra for the extra internet useage, you might be best advised to download the 'Alternate' Install CD .iso and use that one to install with instead, xpod.
If you have to pay extra you should check with your friends and see if anyone has a copy of the Ubuntu Dapper 'Alternate' .iso, they may be able to burn you a copy for free.
That's all I can think of to suggest for now.-Oh, unless you use a GParted LiveCD to partition with beforehand. Those are a 30mb download, but they are free. I have to go to work now, bye, Regards, Herman :D

---

