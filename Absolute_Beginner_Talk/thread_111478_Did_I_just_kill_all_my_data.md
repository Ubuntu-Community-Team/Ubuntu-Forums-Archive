---
title: "Did I just kill all my data?"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Prozzy on 2006-01-02
Hey..

Okay, yeah Im a total noob with linux, and i bet i just fucked up.

I just got myself a copy of the ubunto install and live cd and was playing around trying to get the live cd to work, though it wouldnt work. While loading it got stock at APCI or something. 

So i figured, well how hard and bad can it be, ill just make another partion on my primary disc (only got 1 disc in my laptop), so i made a 5gig partion and booted on the install cd.

While installing i choose to install on the 2nd partion i had made in windows, before i started on this installing of ubuntu. As far as i remember i told the install not to do anything with my other partion running windows xp.

So after the install i have my laptop booted in ubuntu, and everything seems to be working file, only got a few probs with my soundcard and some drives, but thats just a minor problem. Ive been browsing various ubuntu/linux forums reading  about how to make a dual boot, 'cause i wanted to get back in my windows system. 

This is were the problem is. I think during the installing of ubuntu i have deleted the primary windows partion!?! (dont ask me how), when i do df i dont see the /dev/hda1 and in gparted i got a nice 73gb of unallocated space...

So, now did i kill all my data on my old 73gb NTSF partion, or can i still get it back? 

If i have killed my data, i was planning on doing a fresh install of windows and ubuntu. How would i do that best? how should i partion my disk to get the best out of both systems?

Greets Prozzy

---

### Post by Swab on 2006-01-02
Open up System > Administratation > Disks then click on partitions to check if it's still there.

---

### Post by az on 2006-01-02
[QUOTE=Prozzy] ill just make another partion on my primary disc (only got 1 disc in my laptop), so i made a 5gig partion and booted on the install cd.
[/QUOTE]

How did you do that?  Did you use the installer's partitioner or a third-party tool?

---

### Post by Prozzy on 2006-01-02
In the disk manager it says "Free Space", "Partion 2", and "Swap Partion". 

So i kinda figures i deleted the partion, but i havent formatted the partion.

and to partion i used Partion Magic in windows

---

### Post by Swab on 2006-01-02
Then the data is still there... I don't have a clue how to get it back.... How important is this data?

---

### Post by Prozzy on 2006-01-02
Well its not super important, i have backup of my documents and stuff on my usb key. 

The data i lost is mainly my music, which i have on original CDs, would just be nice if i didnt have to encode everything again. 

There was also a few programs that i use for school stuff, but i can probably get those again.

It wasnt my idea to go full linux yet, but guess the way to learn linux it is the hard way.

Edit::

GParted cant make ntfs partion, would it be possible if i choose "New" on the 73gb unallocated part and created a fat32 system to get my data? or would i kill everything in the process of adding the fat32 system?

---

### Post by Swab on 2006-01-02
Yeah creating a FAT partition is not going to help you get your data back... The problem is that the table containing the location of all your files is gone.

---

### Post by vasudevank on 2006-01-02
you may want to try r-studio (i don't know if it will work)

---

### Post by Iandefor on 2006-01-02
It's gone. Deleting the partition deletes the table the computer uses to access the information; without that, the computer can't differentiate between files or find the location of a file on disc. You can't re-index it, unfortunately. So: your data is, for all intents and purposes, gone. Thankfully, it seems all your data got backed up, so it should be a trivial matter to get up and running with Linux, or, if you feel like it, making a new partition table so you can install Windows again.
> 
It wasnt my idea to go full linux yet, but guess the way to learn linux it is the hard way. You *can* learn Linux the hard way, or just go with man pages, which is a lot less destructive :-D.

---

### Post by az on 2006-01-03
[QUOTE=Iandefor]It's gone. Deleting the partition deletes the table the computer uses to access the information; without that, the computer can't differentiate between files or find the location of a file on disc. .[/QUOTE]


Actually, you can use parted to remake a partition.  Use the rescue feature.  You tell it approximately where the partition once was and where it once ended, and it will look there, discover the exact numbers  and create an appropriate entry in the partitoin table.  You probably can get your data back.

type
man parted


and boot the installer and use the shell (CTRL-ALT-F2)  You need to use the installer because it does not mount the hard drive which prevents you from modifying the partitoin table.

---

### Post by akniss on 2006-01-03
There are quite a few programs for windows that will recover data from deleted partitions.  I even reformatted one and was still able to recover about 60% of my files.  I don't remember which programs I used, If I find them i will post again. 

Just be sure you don't do anything else to the partition in the meantime... the more gets written on it, the less the chance of recovering anything.

Just remembered one of the programs was called recovermyfiles.  imagine that.

---

### Post by Suger on 2006-01-04
else, in ubuntu, you can try testdisk (in synaptic)

---

### Post by steve.horsley on 2006-01-04
If none of those proggies seem to help, there is a remote chance you can recover by simply allocating all the free space as an NTFS-type partition (which is what it presumably was) but not reformatting it. Command-line **sudo cfdisk** is what I would use, but any partition table editor would do.

---

### Post by soonindallas on 2006-01-04
I have used a windows app, GetDataBack, to recover data from a NTFS partition in the past.

[http://www.runtime.org/gdb.htm](http://www.runtime.org/gdb.htm)

You can download the demo version for free to see if the files are recoverable, you need then to purchase a license to save the data.  I don't know how much the licence costs, but in some cases it can be worth it...

---

### Post by meborc on 2006-01-04
but what do you do with a windows app without windows??? :D ... anyway, i wouldnt waste my time on it... my friend went through the same ordeal... and got nothing back... but lost two weeks on different tools and measures to get ntfs back... no luck... but it is a good way to get to know your computer... you can learn a lot by messing up :rolleyes: 

if you still want to use windows and ubuntu together, then use this guide next time... _[http://www.users.bigpond.net.au/hermanzone/](http://www.users.bigpond.net.au/hermanzone/)_ just to be sure that everything works out fine :D ...

---

### Post by Prozzy on 2006-01-04
I spend some time trying to figure out the stuff...

I finally came to the conclusion that it would be a waste of time trying to get my data back, just to save a few emails that i didnt backup. So i did a reinstall of ubuntu cause i found that to be the easiest, since i had to figure out some other stuff also, and now i got only ubuntu :)

But thanks for all the ideas and suggestions. Ill start reading about how im gonna use ubuntu.

---

### Post by Iandefor on 2006-01-04
[quote=azz]Actually, you can use parted to remake a partition. Use the rescue feature. You tell it approximately where the partition once was and where it once ended, and it will look there, discover the exact numbers and create an appropriate entry in the partitoin table. You probably can get your data back.

type
man parted


and boot the installer and use the shell (CTRL-ALT-F2) You need to use the installer because it does not mount the hard drive which prevents you from modifying the partitoin table.[/quote] Really? Awesome. I wish I'd known that earlier- would've saved me more than one headache. Thanks, Azz!

---

