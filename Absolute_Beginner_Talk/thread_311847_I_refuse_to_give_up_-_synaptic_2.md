---
title: "I refuse to give up - synaptic 2"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Carolyn62 on 2006-12-03
Good Morning,

Because of the problems I am having with synaptic and being unable to download updates I was on the verge of quitting ubuntu and Linux all together. (see [http://ubuntuforums.org/showthread.php?t=307383&highlight=synaptic+error](http://ubuntuforums.org/showthread.php?t=307383&highlight=synaptic+error))
however I seem to enjoy ubuntu more then windows in spite of some of these problems because it is faster, cleaner, and of course free. In addition I am a 60 something year young woman and if I did not allow Bill G. to defeat me with windows I am certainly not going to allow ubuntu to beat me. I have been using windows since version 3.11 so I am not totally inept.

I am slowly realizing that I may have to reinstall all or parts of ubuntu to fix this problem(s) because I believe that there are no answers in fixing this synaptic error so I am willing to do whatever it takes with your help please. I am terrified that if I reload ubuntu that I am going to lose XP pro because I believe that is where ubuntu installed the duel boot portion. let me lay out what I have and what I did:

I have windows XP pro on /dev/hda ntfs which is a 60 GB primary hard drive:
I allowed Ubuntu to install on /dev/hdb which is a 40 GB slaved hard drive with the following partitions: /dev/hdb1 ext3 (36.91 GB),
 /dev/hdb2 extended (1.43 GB),  
/dev/hdb5 Linux-swap (1.43GB)

If I have to reinstall I would like to add a fat32 partition to the 40 GB hard drive so that I can move my windows documents there for read and write access.

What I need is if I have to reinstall how would I do it without the possibility of messing up my access to XP because of the duel boot issue. Keep in mind that I am an absolute beginner and if you could give me a step by step approach I would be forever grateful.

The reason that I allowed ubuntu to do the whole install is because I was having problems with partitioning was was afraid of messing it up.

Carolyn

---

### Post by nixclusive on 2006-12-03
Whoa kudos to your spirit mam! =D>

If you really intend to re-install Ubuntu, you can go ahead the way you did previously. But this time, make sure to use manual partitioning and allocate a little less space for the 'root' partition; and make a new fat32 partition in the newly created space.

If this seems a bit confusing to you, please have patience and wait for at least a day there while I come back with screen-shots and a Step-By-Step guide for you.

A day I ask, for its 01:00 AM in the moring here and I'm feeling really sleepy for this :redface:

So what would you like to do? Go ahead right now or do you want me to come back with screen-shots et al?

---

### Post by Carolyn62 on 2006-12-03
Hi,

I think to be on the safe side that I should wait the day. I can use your guide tommorrow after work to do the reinstall (I do not see any way out). After I have gained more experience in Linux I should be OK, but for now I don't want to take any chances. Thank you for your help.

Carolyn

---

### Post by nixclusive on 2006-12-03
Sure thing, I thing the guide can be useful to other users as well. Thanks :-)

---

### Post by Johan! on 2006-12-03
Try [this]("http://psychocats.net/ubuntu/installing") guide.

[Here]("http://psychocats.net/ubuntu/index.php") you can find more information and other guides.

---

### Post by Carolyn62 on 2006-12-03
I have tried both of these guides and when it comes to the partitioning the windows are not the same and I chicken out.

---

### Post by LLRNR on 2006-12-03
Carolyn, I'm glad you haven't given up and bravely came back (by the way, I'm sorry, I didn't know what else to tell you back then) ! 

There's no need to "chicken out" if you want to reinstall Ubuntu and keep Windows, even though the partitions in that guide don't exactly match yours.

As far as I understand, you want to keep XP on your master HDD (the 60 GB one). Reading through the information you provided in your first post, I see that your master HDD is only referred to as "hda" - so any partition you might have there and want to keep will only be referred to as "hda**x**".

If - as i understood it - you want to reinstall Ubuntu on your slave HDD (the 40 GB one) and create another extra FAT32 partition (for both read and write access), then the partitions on your second HDD will only be referred to as "hdb**x**"...

So, when you do the reinstall, it will be fairly easy as long as you don't mess with anything reading **hdax**, right ? :)

No need to chicken out, just create:
- an EXT3 partition for /
- a swap partition
- a FAT32 (vfat) partition for your shared documents.

That should do it ;)

LLRNR

---

### Post by nixclusive on 2006-12-04
Ok lets do it now, you might want to print out these instructions for offline reference.

We'll be using the command line a little bit for faster operations. First off, boot the target computer from the live cd. When the system is comfortably up and running, proceed as follows:

1. Click Applications > Accessories > Terminal.

Since we already have a swap partition in place, the live CD will allocate that partition for its own swap usage. This is known to interfere in the re-partitioning process; so we turn off that:

2. In the terminal, enter the following: ```
sudo swapoff -a
```

3. Now, to make sure we have options to recover in case we mess up anywhere while partitioning, enter the following in the terminal: ```
sudo fdisk -l
``` The command will produce a long cryptic output. Write down the output somewhere on paper, maximize/scroll in the terminal window if required.

4. Now close the terminal and double click the 'install' icon on the desktop.

5. Proceed as normal till you reach step 5. This is where you select the method the installer utilizes to re-partition your hard drive for installation. Of all the options presented to you, select the option labeled: "Manually edit partition table".

6. After a while, you'll be presented with the partition layout of current storage system. Select /dev/hdb from the menu/toolbar -- make sure you did select hdb from the menu, you should see the present status of your target drive (hdb) for editing -- and clear the whole disk by selecting each individual partition and pressing the delete key. Make new partitions as required by right clicking in the empty space and selecting 'New...' from the pop-up menu. For instance, create a partition of 20G for installing Ubuntu, a 10G FAT32 partition to be shared with windows, and the rest to be filled by your '/home' and 'swap' partitions. Don't make a the 'swap' space too large, 1.5 times of your present RAM should be enough. Press the 'forward' button.

7. Here, you are presented with a table using which you inform the installer how to use the newly partitioned disk. Select the largest space in 'hdb' to be allocated as '/' (root partition). The left column represents the mount point and the right column represents the partition to be mounted. Select the FAT32 partition to be mounted in /media/hdb*x* (*x* being a number), and the /home and swap partitions in their respective mount points. Select to reformat the newly created partitions by clicking the appropriate check boxes.

8. Press the 'forward' button only once. At this stage, the installer seems to forget to gray out the pressed button, but nevertheless, it will proceed after a while.

Now you'll be presented with a 'point of no return' dialog. This is where the installer shows you the changes to be made and asks for your confirmation to proceed. Review the given information in the dialog and if you are satisfied with the changes, press 'install'.

After a little while, you should have a new Ubuntu installation in your second hard-drive (hdb) with Windows XP intact on hda. You can access the shared FAT32 partition from the mount point defined in /media/hdb*x* in Ubuntu; in Windows, it'll show up as another drive.

Congrats. :-)

---

### Post by Carolyn62 on 2006-12-10
Hi,

Good news!:p :p :p  I have been able to fix the synaptic package manager and have not had to reinstall Ubuntu.

Here is how I did it. On a previous thread someone had recommended that I use synaptic to uninstall flash, as I was unable to do this because there was zero across the board at the bottom and no packages showing I gave up on doing that. Yesterday I had printed out all the information you had given me for the reinstall (have to use windows for my printing) went back to Ubuntu for one last look, opened synaptic and stared at it for about 5 minutes when I noticed the reload button.

The first thing that crossed my mind was that it would never work so why bother but another thought said what do I have to lose so I pressed it. Well, after about 10 different error messages popped up I noted that all the packages were showing so I closed all of the error messages, found flash and unmarked it for complete removal. Worked like a charm. Now I am back to my original problem of not all packages updateing but I am able to download and install software updates and everything else seems to work.

I do have one more question though. I still want to add a fat 32 partition to my second drive. Is this possible without messing things up?

Thank you for all the help that you have given me. I am in you debt. I have learned more about Ubuntu through this problem then had it not happened.

Thank You,
Carolyn

---

### Post by al_sharpe on 2006-12-10
Hello Carolyn62:

Yes you still could add a FAT32 partition to hdb, but I would recommend
buying an external USB harddrive and formatting it in FAT32.
This way you would have a secure copy of everything if your computer 
fails. A great place to store those digital photos and both OS's can
see it.

Just a thought
Al Sharpe

---

