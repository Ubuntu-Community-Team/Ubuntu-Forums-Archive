---
title: "resizing partitions with data on"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by norton1 on 2007-04-24
hey, i've been having fun with edgy for the past month or so and so far i've found it great - so great in fact that i wanna extend the palty 10 gig partition i installed into as i'm running out of space already ;)... now what i want to know is

can i resize my windows partition with 43gb free space to claim some of that for my linux partition

also, on a similar note - do i need to if i install linux programs and things into the windows partition that i can access from ubuntu?

thanks for your help!!
#
ben

---

### Post by LaRoza on 2007-04-24
In general, you can resize partition without loosing data, but always backup!

If you are using Windows, defrag before resizing.

If you are using Windows Vista, you must resize the partition with Vista.

---

### Post by oilchangeguy on 2007-04-24
just run from the live cd, and use gparted. i gotta ask, what are you doing that you've managed to almost fill 10 gigs of space?

---

### Post by mikewhatever on 2007-04-24
You can resize the Windows partition either with gparted live cd, or with Ubuntu install CD. Yet another way would be to install gparted on Ubuntu from synaptic and manually un-mount the partition you want to resize. Defragment it first to make sure the data is moved towards the beginning and then shrink it from the end. 
You can read access files on NTFS partitions from Ubuntu. If you also need write access, [http://www.google.co.il/search?q=ntfs-3g+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.co.il/search?q=ntfs-3g+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by LaurelLynn on 2007-04-24
Dear norton1,

Be aware that modifiying partitions always runs the risk of loosing the contents if something goes wrong (with any os).  Resizing seems pretty stable in Ubuntu, but if you can backup everything first.

Gparted (which you may have to install first)  has an option to resize partitions. You click the right-mouse button on the partition and select "resize/move".

Defragment windows first, as you can only use empty space on the end of the partition.  Also windows will still leave some files in the middle of the partition, so there is a limit to how much an existing partition can be shrunk.

---

### Post by norton1 on 2007-04-24
hey, thanks guys - i'm gonna give it a go with gparted - i remember looking at it whilst installing and it looked straightforward enough - i will back it up tho, for sure.

and oilchangeguy -if that is your real name, i dunno - most of it went on the install - aparently i've only got about 2gb left accorrding to ubuntu (495meg if you listen to the windows part - it can read  ext2 as drive z)

thanks again - i'll post back if i destroy everything

---

### Post by mikewhatever on 2007-04-24
That is very strange. My Ubuntu 6.10 installation has never gone beyond 5 BG.

---

### Post by psusi on 2007-04-24
IIRC, gparted can not move the starting location of partitions, so while you can shrink your windows partition, even if your linux partition follows it, gparted can not move the start of that partition backward to use the new free space.  I could be wrong though, and it may have only not been able to move the start location of windows partitions.  In that case, as long as the windows partition comes first, then you can do it.  

If the linux partition is first, then you can't since the free space will be at the end of the disk, and the windows partition will still start right at the end of the linux one.

---

### Post by jerrylamos on 2007-04-24
Well my Feisty partition is at 13 G because it's got a lot of *.iso files of Beta Ubuntu Kubuntu Xubuntu Dapper Knoppix SimplyMepis PCLinuixOS Puppy DSL Freespire and I forget what all else.

Now on my laptop I had quite a thrash defragging XP.  One big help was to go into Control Panel, System, I forget which menus to turn paging off so there wouldn't be that big fat paging allocation at the upper end of memory and then reboot and defrag once again.  Microsoft uses a "scatter" file allocation system hardly performance oriented.  I also wound up using a defragger from the Internet.  Do remember to turn paging back on after resize.

With very careful measurements on the defrag display screen I saw how much I could resize XP down without hitting data.  Then I did it with standalone Gparted which worked.  Pretty scary.

Moving down and resizing the Linux partition worked, slowly of course.  Achtung, back up everything!

Cheers, Jerry:)

---

### Post by norton1 on 2007-04-26
well - i was unable to create a back up as the only thing available was a usb storage device that windows wouldn't let me use - but hell iwent ahead and gparted'd it up - after defragging - and it seems to have worked fine - strangly gparted found errors on my windows partition that windows didn't but they are fixed now too.  all my programmes and documents seem to be in order on both partitions with the only problem being that when booting back into windows it announced that it had found new hardware??? and then on subsequent restarts the taskbar has become inactive - so i'm unable to click on the start button or maximise windows etc - although the windows button works to launch the start menu - 

- ah well, i guess i'll need to join an xp forum now to solve that one!!

thanks again,

ben

---

### Post by macabro22 on 2007-06-06
My ubuntu partition is 17 gb! I need a resize as well.
I don't know how it's gotten so big!

---

