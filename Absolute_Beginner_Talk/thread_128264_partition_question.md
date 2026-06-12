---
title: "partition question"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-02-11
I'm trying to onstall ubuntu version  5.04

First it says to partition your drive.

Okay I've done that with Ranish Partition Manager as follloew,

Partirion 1 --Window 98        Dos16
Partition 2 --Windows 2000   Dos16
Partition 3 --ubuntu             Linux
Partition 4 --common filres    Dos16

When using the install ubuntu install disk it show,

Partirion 1    Fat32
Partition 2    Fat32
Partition 3    Fat32
Partition 4    Fat32

How do I select Partition 3 to install ubuntu on?

Don Cole
 A Bug is an un-documented feature.
A Feature is a documented Bug.

---

### Post by Herman on 2006-02-11
Did you put in the Ubuntu install CD and get a screen that says 'press enter for the default install'? Then you go through a few screens where it asks you some easy questions and some blue and red 'progress bars' cross the screen until finally you come to one where it stops at '[!!] Partition Disks'.
Is that where you get to? 
And you see the list of partitions you showed, and you need to know what to do next?  
Okay then, just use your up and down arrow keys to move the blue rectangle over the line that says '#3 primary x GB fat32 /media/hdax', and press enter.
(As long as you are SURE that is the right partition to install Ubuntu on).
On the next screen it will remind you you are editing the partition you just selected, and ask you what to do with it. You need to delete the partition!
The reason for that is because the Ubuntu install needs at least another two more partitions. These would be your main Ubuntu partition to install the operating system on, plus a small 'swap area', (for the memory).
Now you'll get the '[!!] partiton disks' menu back again showing 'free space'.
Select the free space (where your partition was), and press 'enter again.
On the next screen, 'automatically partition the free space' should be the easiest thing to do, the rest of the install should be easy after that.
If all this sounds too complicated for you, don't worry, it will all make sense when you start doing it. It's just that your set-up is a little different to most people who only have one Windows installed, otherwise you could just follow one of the example installs in my left-hand 'sig link' under this post. If you want, you can have a look there to see how the rest of the install will go, there should be some information there that will help you, it's just the middle part you needed to do a little bit different from most people. Good luck with it! :-D (Herman)

---

### Post by don cole on 2006-02-11
(As long as you are SURE that is the right partition to install Ubuntu on).
On the next screen it will remind you you are editing the partition you just selected, and ask you what to do with it. You need to delete the partition!
The reason for that is because the Ubuntu install needs at least another two more partitions. These would be your main Ubuntu partition to install the operating system on, plus a small 'swap area', (for the memory).
Now you'll get the '[!!] partiton disks' menu back again showing 'free space'.
Select the free space (where your partition was), and press 'enter again.

Thank you Herman for you quick reply.

So you delete the partition and then ubuntu finds the empty space and formatts
it after you select finish?

Now this is just one partition I assume for the Linux Operating System.

I have reseved another partition w/ Ranish Partition Manager for the swap file.

Are you saying that both the swap file and the OS will be installed in my original selected partition (which will now really be 2 partitions?

I know I may be going on too much about this simple stuff.  I want to make sure I get it right because I got too much stuff I don't want to delete on my
common files partition. I allready messed up my windows98 partition. That's OK
because I didn't have anything on it except the 98 OS which is easy to re- install.

And I don't have the money to buy more drives for backup.

One more thing with the Ranish Partition Manager, when I boot up and press [1] Windows 98 boots up. If I press [2] then Windows 2000 boots up. So when I finish the ubuntu installation (in the correct partition) and press [3] the ubuntu should boot up right?

That's my goal anyway.

Don Cole
 A Bug is an un-documented feature.
A Feature is a documented Bug.





Don Cole
 A Bug is an un-documented feature.
A Feature is a documented Bug.

---

### Post by Bartender on 2006-02-11
Hi, don -
I can't give u definitive answers but can try to help out.  I followed the hermanzone directions to dual-boot.  GRUB (don't let the weird acronyms throw you, GRUB is just the program that handles the boot loading/partitioning stuff) took a look at the chunk of hard drive that I gave it for Ubuntu and split off the small swap partition from the larger piece.  So I THINK the correct answer is that GRUB will do this within your allotted Linux partition and you don't need to use any third-party software to prepare for its arrival.  It's good to see you asking these questions now!
Having said that, I'm vewy newvous after reading your comments about valuable data on Partition 4.  Can you at least back it up to CD's, DVD's, or transfer to a friend's computer, or do SOMETHING so that you're not painting yourself into a corner?   

I did a dual-boot just a coupla weeks ago.  It wasn't scary because the W2K installation was all fresh and shiny.  If I botched it I'd just start over again.  This oughta be a fun experiment instead of a sweaty-palmed thrill ride.  As far as I'm concerned, nobody should be doing major brain surgery on their HDD without being prepared to lose everything and start over.  GRUB works but there are too many things that can go wrong and way too many posts that start off with "Ubuntu ruined my Windows partition & I lost all my research into cold fusion and the cure for the common cold".

EDIT:  How come you're installing 5.04?  Do you want a stamped set of 5.10 discs?

---

### Post by don cole on 2006-02-11
Hello Bartender,

I think you're right about back up.

I do have 2 physical drives on my computer.

One bigfoot 19GB and one other 2GB. I suppose I could copy every thing on 
the other drive to my planed linux partition on the bigfoot.
And unplug the bigfoot. Then install ubuntu on the 2GB drive.
But how would that work on my muli-boot sceme? Would I have to go into the BIOS every time I wanted to change Operating Systems?

I'm trying to use version 5.04 because I got it free in the mail.

Don Cole
 A Bug is an un-documented feature.
A Feature is a documented Bug.

---

### Post by Herman on 2006-02-11
> I know I may be going on too much about this simple stuff. I want to make sure I get it right because I got too much stuff I don't want to delete on my
common files partition. I allready messed up my windows98 partition. That's OK
because I didn't have anything on it except the 98 OS which is easy to re- install.
And I don't have the money to buy more drives for backup. That's okay then, bartender is right, even if you can get a little of the most important stuff backed up on a CD or DVD it would be a good idea, probably everything will be okay and you won't need it, but then again, you might. 
Now, it's okay to use the partitions you already made, I didn't know what they were, I just saw these:
>   Partirion 1 --Window 98        Dos16
Partition 2 --Windows 2000   Dos16
Partition 3 --ubuntu             Linux
Partition 4 --common filres    Dos16 
>  So you delete the partition and then ubuntu finds the empty space and formattsit after you select finish?It looks to me like you should delete partition 3 there for Ubuntu, then _you select_ the free space that will be left there where it was and choose 'automatically partition the free space'.

Otherwise:
If you have another partition for a swap area already made and you want to use that you can. Instead of 'automatically partition the free space, choose 'create a new partition, and then create a new partition with either ext3 or reiserfs file system instead of fat32. and make it bootable, and make it your / (root) partition.
Then, if your swap area is already formatted as a linux swap area, it will be okay, just leave it and Ubuntu will detect it and tell you it will format it for you.
> I know I may be going on too much about this simple stuff. I want to make sure I get it right because I got too much stuff I don't want to delete on my common files partition.That's okay, don't do anything until you feel like you know what you are doing, ask all the questions you want, people around here love to help, so don't be shy.
> One more thing with the Ranish Partition Manager, when I boot up and press [1] Windows 98 boots up. If I press [2] then Windows 2000 boots up. So when I finish the ubuntu installation (in the correct partition) and press [3] the ubuntu should boot up right?I don't know anything about the ranish partition manager, it has a boot loader has it? Most people here use GRUB, but it isn't compulsory. Doing everything a different way from the rest of us means you need more help though, and some things we all might not know. It isn't that we don't want to, but you might be waiting a long time for someone else who knows about the Ranish partition Manager's boot loader, compared with GRUB, which lots of people around here can advise you on. However, if you already have the Ranish one, I don't know what will happen if you change either. ???
I hope everything goes okay, I have to get a few hours sleep now but I'll check to see what you're up to when I wake up. Lots of others are here to help. Bye for now, (Herman).

---

### Post by Bartender on 2006-02-11
don -
2GB is too small for Ubuntu.  Too small for the standard install, anyway.  I've seen folks talking about using the server version or some such but you don't want to go there.
You probly have some good reason for wanting to keep Win98.  But I've gotta ask - what about just dumping Win98, taking the space back, and going with W2K/Ubuntu?  The stuff you need to back up - will all of that fit on the little 2GB drive?
Ubuntu can't access the NTFS file system, so if you could format the dinky drive as FAT32 & then stash the valuable files there, both OS'es should be able to read the data from their locations on the main drive.  Depending on the nature of the data of course; if it's a Windows-specific format Linux won't be able to read unless you install Wine blahblah I'm getting off track.
  
Check your private mail, OK?

---

