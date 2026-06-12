---
title: "new to ubuntu. answer my noob questions pls.?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by mark. on 2007-06-07
hi, ive been looking around using linux for a while and want to try it out. im downloading the iso for the cd right now, but i think i need some help around things.

first, when i install ubuntu, how do i install it so that i can keep my WinXP os as well (dual-boot).
--keep in mind i dont really know what 'partition' means and i only have one hard drive.
also, do i need to backup my files on a cd before installing? because im not sure if the files will be deleted when installing ubuntu. 

anyway, thanks in advance- ive heard the linux community is very supportive.

---

### Post by esavato on 2007-06-07
It is a great idea to backup all of your files before you perform the install.
You will be resizing your drive to have two new partitions, one for the Ubuntu install, and one for swap space.  I was able to just defragment my drive and then create these new partitions, without having to reinstall XP, or Vista.  You just need to make sure you have enough contiguous space on your drive, and put the new partitions at the end of the drive.  There are plenty of guides that go over this process in detail.  After you install Ubuntu, you will have a new bootloader called grub, which will give you the option to choose your Ubuntu installation, or windows XP upon boot.

---

### Post by floke on 2007-06-07
Try this
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

Defrag + scandisc Windows
Back up valuable data (never gone wrong for me but just in case)
Load LiveCD of ubuntu
Use Gparted (system/admin/gparted) to shrink Windows; 
Proceed to install - double click on desktop icon
When asked where to install ubuntu select 'largest available free space' option
Answer questions
Make a cup of tea
Reboot
Enjoy!

Welcome to ubuntu :D

---

### Post by mark. on 2007-06-07
ok, thanks. 
so when i install ubuntu (from live cd, right) then it will keep my windows XP and then use grub to make it dualboot?

oh- and i downloaded the iso from here. when i burn it to cd it will launch automatically when i start my comp?

---

### Post by lazyart on 2007-06-07
You might want to defrag twice to be safe.

> **mark. said:**
> anyway, thanks in advance- ive heard the linux community is very supportive.

As long as you promise to never, ever again put a vague title to a thread. :)

---

### Post by Rocket2DMn on 2007-06-07
It *should*, but as always, make sure you make very good backups before you start.  I cannot stress the importance of backups enough.  Make sure you make good backups.

Make good backups.

---

### Post by dfreer on 2007-06-07
Welcome to Ubuntu! This forum is one of the best, from what I've seen.

When you get your ISO downloaded, make sure to burn it the correct way (Nero has an option "Burn image to disc", it isn't that hard to burn). When you reboot with the CD in the drive, it will load the Ubuntu desktop entirely in RAM, so that you can play around with the system and see what drivers work before you install.

Now for your questions:
(1) The install wizard is very easy to use, the only probably you will probably have is with the partitioner. If you want a short explanation of what partitions are, you can read below. Otherwise, the wizard *should* do everything for you, choose the "Guided Partitioning" option. It will even autodetect you are running windows and set up the dual boot for you.

(2) Partitions are just divisions of the Hard Drive. Say you have a piece of paper, and you draw a line across half of it. You now have two boxes, but only one piece of paper. A partition is just a "box" on the hard drive. Now, the important thing to note here is that each OS (windows, ubuntu) should have it's own partition. So windows in one "box", ubuntu in another "box". 
  One other important thing is there should be an third "box" for the swap drive. Both windows and Linux use hard drive swaps, you can read up more about what a swap is or just ask. But basically while windows stores it's swap in a file called C:\pagefile.sys, linux likes to put the swap in it's own partition or "box". By the time the partitioner is done, it should have three "boxes", one for windows, one for ubuntu, one for the ubuntu swap :D

(3) As with ANY major change to your system (remember you ARE installing a new OS), you should always backup important data just in case. However, the install process has been getting so good lately I personally wouldn't worry about it. As long as you don't mess with things and delete/format your windows partition, you should be A-OK.

Remember, because you can surf the internet while installing, you can always ask for help if you get stuck in the install process, and even post a screenshot if you need to. Ethernet drivers should work great, wireless sometimes works out of the box. Just a thought.

Good luck and let us know how the install goes!

EDIT: As always, I type slow and end up reiterating information. Oh well

---

### Post by jfinkels on 2007-06-07
When you're installing Ubuntu, make sure NOT to choose to overwrite your entire hard disk!

---

### Post by mark. on 2007-06-07
i promise, lazy :p

Well i have one hard drive, with 100.7 gb free, on a dell desktop rebooted a year ago.. and ill backup my documents ect. on a dvd-r. 
But ive wondered, what does defragmenting do? Ive done it before and for all i know it just makes my comp faster lol.

---

### Post by Bohlio on 2007-06-07
Partitions are just different parts of your hard drive. In a way, They kind of act like different hard drives all together. When you Dual boot WinXP and Ubuntu, You will probably end up with 3 partitions in the end, One Windows partition that uses a type of filesystem called NTFS, One ubuntu partition that uses a filesystem called EXT3, and a Swap partition. If you are on a Dell or another computer that has a recovery partition or a partition for system tools, then it gets a little more complicated, but you can still do it.

Heres my Step by Step
1. Under Windows, Defragment your Harddrive, Then do it again.
2. Burn that Iso that you are downloading onto a CD, then pop it in the drive.
3. Restart your computer.
4. Get into your boot menu by pressing the correct F button, It usually tells you but with Dell's it is F12
5. select to Boot from your CD rom.
6. The ubuntu Live CD will load up, and it will act as you are running ubuntu (it runs off the CD instead of your           harddrive, This can be usefull for testing out if your hardware is supported)
7. Click the Install icon on the desktop
8. Answer the questions about the language and time zone and such...
9. It will bring you to a partition editor, 
     Option 1 will resize your First partition on your drive, (which may be a recovery partition) Only do this option if you are certain that your first partition is your windows partition.
      Option 2 will get rid of windows and do an all ubuntu system, You dont want this.
     Option 3 may be what you need, It allows you to manually edit the partitions, where you will shrink your windows partition, create a ubuntu partition from the empty space, and create a swap partition. Look for a guide to do this, there is plenty around.
10. Once you get through the partitioning step according to your systems needs, It will install Ubuntu.
11. When it finishes installing, You restart, and you are greeted with a menu before you boot up. This menu will allow you to select which Operating system you want to use. (Ubuntu or Windows)
12. Select Ubuntu and have fun :-)


Edit: Dang, Many people beat me while i was typing this up :-P and I am assuming that you are installing Ubuntu 7.04, Fiesty Fawn, I dont know if the older versions have this same system. And somewhere mixed along in those steps, is an option to import some windows settings into Ubuntu (ex. Firefox bookmarks) :-P

Defragmenting takes all those chunks of data on your hard drive, Puts them together, and plops them right at the beginning of your drive. This makes it so your drive doesnt have to access everything thats spread all over, and allows you to later shrink the partition, without cutting off chunks of the data. Think of it like this, Its like moving all the cars to one end of the parking lot before you demolish the other half. :-)

---

### Post by jgrabham on 2007-06-07
> **mark. said:**
> 
But ive wondered, what does defragmenting do? Ive done it before and for all i know it just makes my comp faster lol.

It basically moves your files around so windows can find them easier.

---

### Post by dfreer on 2007-06-07
> **mark. said:**
> i promise, lazy :p

Well i have one hard drive, with 100.7 gb free, on a dell desktop rebooted a year ago.. and ill backup my documents ect. on a dvd-r. 
But ive wondered, what does defragmenting do? Ive done it before and for all i know it just makes my comp faster lol.

A good defragmenter should move all of the files from the end of the partition to the beginning, and sort them. A defragmenter's regular job is to take fragmented files (a fragmented file is 1 file spread across several locations), and put them together so they are no longer fragmented. Anyways, it is good to defragment your hard drive so all of the files are near the beginning of the drive and not the end where you will be shrinking the partition to fit ubuntu :D

---

### Post by jfinkels on 2007-06-07
> **mark. said:**
> i promise, lazy :p

Well i have one hard drive, with 100.7 gb free, on a dell desktop rebooted a year ago.. and ill backup my documents ect. on a dvd-r. 
But ive wondered, what does defragmenting do? Ive done it before and for all i know it just makes my comp faster lol.

When files are written to your hard disk, they are not necessarily written in a linear, contiguous pattern, i.e. there might be one half of a file at the beginning of your disk, and one half a few blocks later on. This might potentially be slower because the hard drive spindle has to move to the next part of the file when it is trying to read it, and the spindle is the slowest part, or so I've heard :D. Defragmenting will make fragmented files contiguous.

EDIT: I'm getting slow...

---

### Post by zero244 on 2007-06-07
Excellent How To's guys.
Its a littel dangerous doing a dual boot install, especially the first time.
Ive always used a disk manager in Windows to setup a unallocated spot to put Ubuntu.
Unfortunately it takes a third party app to resize partitions in Windows.
Read the How To's very carefully and proceed with caution and it should work just fine.
Good Luck.

---

### Post by floke on 2007-06-07
Linux filesystems don't need defragmenting, so you don't need to worry about it.
Along with viruses, trojans, spyware, paying for software, forced upgrades.....

* EDIT * BTW: Burn the Iso at the slowest possible speed  - and check the verify option in the first startup menu to make sure the cd's good to go.

---

### Post by mark. on 2007-06-07
omg, thats fast posting.
so i finished downloading desktop 1386 ubuntu 7.04. im pretty sure thats feisty fawn, right?

ok thanks alot people, its a big help. 

oh- when i install ubuntu, will it include the customizations? (cube desktop, window drag animations, ect.)?

---

### Post by floke on 2007-06-07
You can use the desktop effects option - or install beryl
Check it out here:
[http://www.beryl-project.org/](http://www.beryl-project.org/)

---

### Post by Bohlio on 2007-06-07
Yes, Ubuntu 7.04 is Fiesty Fawn

And when you install it, You will have basic desktop effects that can be enabled, I dont quite know if the cube in those basic effects. If you want to get more, You install Compiz or Beryl. There are many threads on installing those two, just search around and you should find the information you need. :-)

---

### Post by mark. on 2007-06-07
so im posting from the live cd os, and i really like the look of linux, freakign amazing :D

i didnt defragment yet, i think i should before i install feisty fawn. but is there anything else i should know before installing? umm how do i 'manually edit' the directories for partitions?

---

### Post by dfreer on 2007-06-07
> **mark. said:**
> so im posting from the live cd os, and i really like the look of linux, freakign amazing :D

i didnt defragment yet, i think i should before i install feisty fawn. but is there anything else i should know before installing? umm how do i 'manually edit' the directories for partitions?

Not sure want you mean here, but unless you know a bit more (or have someone here holding your hand :) ) I wouldn't recommend running the manual partitioner. Too much of a chance to hose your windows installation.

---

### Post by Bohlio on 2007-06-07
I think he has to do it manually, Chosing the first option only works with the first partition on the first drive, I think, and his Windows partition is the 3rd. The second option gets rid of windows completely, and he doesnt want that. All you have to do for the manual is... Calculate how many GB you want for Ubuntu + 2x your RAM. Say you want 20GB for ubuntu and you have 1GB of RAM, Then that ends up as 20 for ubuntu and 2 for your swap. add those together and you get 22GB total for your Ubuntu stuff. Since the partition editor deals in MB, you need to convert that to megabytes. You'll end up with 22528MB that you need to remove from your Windows partition. So you select your windows partition, and when it asks for a new size, You take the current size - 22528 and there you have your resized partition. With the newly created emptyspace, you want to create your Ubuntu "/" directory. If you want that to be 20GB (20480MB) you just select create new partition (or something similar) select the type "ext3" and create a new 20480MB partition.
Use the rest of the empty space for another partition, of the type "Swap" and have it be 2048MB. Then you are all set :-P
Its really not that hard, I did it when i first started with Linux (a couple weeks ago) and I didn't have any problems... Just look at a picture guide beforehand so you know what to expect.

[Memory and Storage Converter]("http://www.csgnetwork.com/memconv.html")

---

### Post by mark. on 2007-06-07
ok, i installed it and i worked perfectly, as i am on ubuntu right now xD

thanks for all your help in this, i am really grateful. 
anyway, now that i have it installed it, how do i install themes? i heard something about 'beryl', but i dont know what that is.
also, how do you view your desktop as a cube? and as well, is there any way to access your winxp files (my documents, music, ect.)

and do i need to download/install any codecs for video/audio ect.?

---

### Post by Bohlio on 2007-06-08
head on over to the desktop effects and customization section to get all the info on beryl that you need. And heres a thread with directions on how to get the codecs and such... [Enabling Multimedia In Fiesty]("http://ubuntuforums.org/showthread.php?t=413626")

And just out of curiosity, Did you have to do the manual partitioning or did the first option work correctly for you?

---

