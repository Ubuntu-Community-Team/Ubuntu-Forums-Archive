---
title: "[SOLVED] A basic Install question!"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by adh2 on 2008-03-20
Hi,
I'm entirely new  to Ubuntu, I've only used Windows before.
Being sick of windows and curious in Linux I now want to try Ubuntu..
I'm downloading the ISO image while writing, but I just want to have some *very* basic help;

1) can you please verify that I can keep windows, creating a dual-boot, or do i have to format the HD entirely?
2) do i need to do some kind of division of the HD, so that Ubuntu will only have access to part of it, and Windows part of it?
3) I've heard that there might be issues with the HD "working too hard", or aging to fast with Ubuntu..? Should I get a patch or something for this?

I know that I can find this information elsewhere, but I've searched and have a popup in my head screaming "overloaded!".. English is not my first language, computer-english is definitely not!

Thank you for your help!

Alfred

---

### Post by barbedsaber on 2008-03-20
1) yes this is called partitioning, where you can split your harddrive into sections. you ge to decide which OS to use at boot up

2) before you install ubuntu, partition the HD and select the empty partion during install, this way windows and ubuntu will be kept seperrate, you can still (normally) read the windows partion while you are in ubuntu 

3) never heard of this happening, might be wrong tho.


and welcome to ubuntu, feel free to ask if you have more questions. :)

---

### Post by adult swim on 2008-03-20
1.  Whenever you boot from your Ubuntu Live CD and you chose to install it will give you some options for where to install ubuntu.  Choose the one that says guided resize, it should be the first choice.  DO NOT USE the one that says guided, use entire disk.  WIth the guided resize it will set up a partition for your windows and partition for ubuntu
2.  step one takes care of this
3.  linux will not zap your drive
EDIT: too slow! :)

---

### Post by jan quark on 2008-03-20
> 1) can you please verify that I can keep windows, creating a dual-boot, or do i have to format the HD entirely?

you can have a dual-boot system no problem with that
see here for guides:
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
> 
2) do i need to do some kind of division of the HD, so that Ubuntu will only have access to part of it, and Windows part of it?

yes ubuntu needs its own partitions:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
> 
3) I've heard that there might be issues with the HD "working too hard", or aging to fast with Ubuntu..? Should I get a patch or something for this?

cannot confirmed that issue
perhaps in the past there were some problems but with the newest ubntu version gutsy and the newest release which comes in april hardy you should be just fine

---

### Post by hyper_ch on 2008-03-20
Next time plz use a descriptive topic title and not a generic "noob here" or "need help"...

> **adh2 said:**
> 1) can you please verify that I can keep windows, creating a dual-boot, or do i have to format the HD entirely?
You can dualboot... in the partitioner during the install do NOT select "Guided use whole disk". That will format it all. Simplest way would be:
(1) defrag the windows drive 3-4 times
(2) use a windows based partitioner to shrink windows
(3) leave the unpartitioned freed space unpartitioned
(4) during ubuntu install select "Guided: Use largest continous empty space" (or similar).

> **adh2 said:**
> 2) do i need to do some kind of division of the HD, so that Ubuntu will only have access to part of it, and Windows part of it?
Yes, that's called partitioning

> **adh2 said:**
> 3) I've heard that there might be issues with the HD "working too hard", or aging to fast with Ubuntu..? Should I get a patch or something for this?
This applies to notebooks when running on battery power only. There is a patch provided for that... you'll have to search the forums if you are in that situation

For more details on installation consult this:  [http://www.psychocats.net](http://www.psychocats.net)

---

### Post by Arthur Archnix on 2008-03-20
1. Verfiied.
2. Probably a good idea. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
3. Perhaps, though it may affect Windows too. Anyway, this thread has everything you need to determine if you need to 'patch' it, and gives precise step-by-step instructions on how to do just that. [http://ubuntuforums.org/showthread.php?t=591503&highlight=load+cycle](http://ubuntuforums.org/showthread.php?t=591503&highlight=load+cycle)

EDIT: Everyone is so fast, so let me be the first to also add, keep the forum family friendly and avoid using words that some might find offensive, or that you might not say in front of a 12 year old. RE: Thread title that will probably get changed.

---

### Post by kesman on 2008-03-20
You need to create an empty partition for ubuntu, you can do this with the ISO-image you are downloading, after you burn it to cd and boot with it, there's a graphical tool for editing your HD's partitions.
Ubuntu will by default ask how you'd like to install it, for the only operating system, or with windows. Pay attention during the install process, it's very simple thing to accomplish.
After this, you WILL have both windows and ubuntu on your HD, and a menu asking wheter you want to boot ubuntu or windows when you switch on your pc.

For ubuntu shortening the life of your HD, I have no idea, sounds a bit funny to me...

For your language, make sure you select your location to be near the place you live, but language as english, since the translations usually suck in Ubuntu, and it's a lot easier to follow any instructions given here with an english Ubuntu.
[B]
EDIT: Oh man I was ultra-slow this time :D[/B]

---

### Post by MONODA on 2008-03-20
welcome!
1. yes you can keep windows
2. yes you will need to virtually split your hard drive, also known as partitioning.
3. i dont think that's true

for more info about partitioning see:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Arthur Archnix on 2008-03-20
I think this may be some kind of record, seven identical responses in the space of two minutes. 

Take that Dell-we appreciate your business, please continue to hold-telephone support!

---

### Post by sayakb on 2008-03-20
1. Of course, you can.
2. Yes, by just creating two different partitions. Linux could access your Windows partition unless you remove the drive's entry from /etc/fstab (but why would you do so?).. Windows cannot read ext3 unless equipped with an ext2fs driver..
3. Gutsy comes inbuilt with HDPARM, which reduces the problem you mentioned.

---

### Post by kesman on 2008-03-20
> **Arthur Archnix said:**
> I think this may be some kind of record, seven identical responses in the space of two minutes. 

Take that Dell-we appreciate your business, please continue to hold-telephone support!

Too bad I subscribed this thread with an email notification :D My mail-notifier went nuts.

---

### Post by adh2 on 2008-03-20
Wonderful!!
Thank you so much, this exceeded all my expectations of how much help you can get of a forum in three minuites! :D

Sorry for the thread name, not very appropriate I realize (got a varning as well.. ashamed:$).
Just one more question; how do I change the topic again..? My questions are indeed answered!

About the HD patch; I do use a laptop (dell inspiron 6400), but rarely use it on battery. Will fix that patch later.

Now I'll fix a backup of my music collection, and move on to install Ubutu! Feels great :)

Again, thank you so much!

---

### Post by hyper_ch on 2008-03-20
> **adh2 said:**
> Sorry for the thread name, not very appropriate I realize (got a varning as well.. ashamed:$).
Just remember it for next time...

> **adh2 said:**
> Just one more question; how do I change the topic again..? My questions are indeed answered!
You can't, only mods can....

Good luck with the installation.

---

### Post by barbedsaber on 2008-03-20
Marking threads as solved 101



have a look near the top, and on the left of the page (this one, you are looking at it right now!) you should see somthing labled "thread tools" click on that, and look near the bottem of the drop down menu, you should see mark thread as solved, CLICK IT.  thats it.

this is very hellpfull to the people that look through the forum for people to help, and saves a lot of their time, so it is much appreciated

thanks

---

### Post by Berean on 2008-03-20
> **adh2 said:**
> Hi,
I'm entirely new  to Ubuntu, I've only used Windows before.
Being sick of windows and curious in Linux I now want to try Ubuntu..
I'm downloading the ISO image while writing, but I just want to have some *very* basic help;

1) can you please verify that I can keep windows, creating a dual-boot, or do i have to format the HD entirely?
2) do i need to do some kind of division of the HD, so that Ubuntu will only have access to part of it, and Windows part of it?
3) I've heard that there might be issues with the HD "working too hard", or aging to fast with Ubuntu..? Should I get a patch or something for this?

I know that I can find this information elsewhere, but I've searched and have a popup in my head screaming "overloaded!".. English is not my first language, computer-english is definitely not!

Thank you for your help!

Alfred

Hi, and welcome!  We've all been where you're starting so don't worry about asking whatever questions you need answering.

1. When you insert the disk into your drive it will load Ubuntu - quite different to Windoze - but will not install anything unless you click on install, so no problems with partitioning.  Effectively, you're working in RAM.
2. As already mentioned in a previous post, if you like Ubuntu partition you HD, and you can keep Windows and Ubuntu, choosing to boot whatever OS at startup.
3. I've not heard of any issues with the HD working too hard.  However, before you choose to partition PLEASE back up all your files to an external HD or flash drive to ensure that should you run into any problems you don't lose important info.

With any new OS there is a learning curve, sometimes steep, but the purpose of the forums is to answer any questions you may have so don't worry about posting.  I'm a newbie, but I've just discarded Windows and find it is the best decision I've made: good luck with your installation.  Regards.

---

### Post by adh2 on 2008-03-20
Hi,

Seems like I already need some more help..
I'm in the installation process, and have a window called "prepare partitions".
There's a table with different partions named "/dev/sda1", /dev/sda2", -sda5, and -sda4.
Sda4 is the largest one, with 114 569MB. 
It says that I need to "specify a partition for the root file system and swap of at least 250 MB"... which I'm not sure I really understand what it means.
I mark the sda4, and click on "edit partion", where I'm asked to enter "new partion size", and "use as". 
Am I supposed to enter the size of the ubuntu partition (the new partition) in the partition size field, or enter the new size of the old, windows, partition? In the second field I'm supposed to take "swap" right?
Hope I made myself clear :)
Cheers!

---

### Post by adh2 on 2008-03-20
Nevermind, I found the information I needed in the official installation guide.. :)

---

### Post by hyper_ch on 2008-03-20
The four/five most helpful resources (I think):

For installation and first steps:  [http://www.psychocats.net](http://www.psychocats.net)

For common tasks and stuff: [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

For shell/bash introduction: [http://www.linuxcommand.org](http://www.linuxcommand.org)

For the rest: [https://wiki.ubuntu.com](https://wiki.ubuntu.com)

(and of course for problems that are not solved: [http://www.ubuntuforums.org](http://www.ubuntuforums.org))

---

### Post by adh2 on 2008-03-20
Nope, it didn't work out after all.
Thanks for the links, they helped but I still can't solve my little problem... so as a final resort I ask you guys again :)

I get to this stage:
[http://img379.imageshack.us/my.php?image=feistydual08ks0.png](http://img379.imageshack.us/my.php?image=feistydual08ks0.png)
And opt for the first option, and theres a popup named "write previous changes to disk and continue?" The alternatives are "go back" or "continue". If I chose continue, there's an error message and I get here:
[http://img379.imageshack.us/my.php?image=feistydual10ea7.png](http://img379.imageshack.us/my.php?image=feistydual10ea7.png)
If I chose 'go back', and then chose forward on the main window, then I get to a window "prepare disk space" where it says "How do you want to partition the disk?"

The option that makes most sense to me, is "partition #2 (sda) and use free disk space", but that doesn't work because "it's not a root file system", and it says "please correct this from the partitioning menu" hence it takes me here again:
[http://img379.imageshack.us/my.php?image=feistydual10ea7.png](http://img379.imageshack.us/my.php?image=feistydual10ea7.png)
The first option is "guided -resize SCSl 1 (0", This produces the same result as the other one.

This "prepare partitions" window seems to make things a bit more advanced than I would prefer..

Any ideas? :)

---

### Post by hyper_ch on 2008-03-20
why is on both ext3 partitions already something installed?

hda5 uses already 54gb and hda7 uses already 4gb

---

### Post by adh2 on 2008-03-20
Oh, sorry!! Forgot to say; the pictures I linked to are only for illustrating what steps in on, they are not from my computer! They are from the psychocats guide

---

### Post by adh2 on 2008-03-20
To me it looks something like this:

/dev/sda                                      size                used
 /dev/sda1   fat16   /media/sda1   90MB               33MB
 /dev/sda2   ntfs    /media/sda2    114596 MB       90000MB
 /dev/sda5   fat32   /media/sda5   2146MB            1800MB
 /dev/sda4   fat32   /media/sda4   3234MB            2200 MB

---

### Post by adh2 on 2008-03-20
Hm I have to abort this for today, but if anyone has any experience of this issue then please post... :)

---

### Post by hyper_ch on 2008-03-20
fat16?

what's on sda5 and sda4?

The problem is those are all primary partitions (I think) so you can't create anymore partitions.

---

### Post by adh2 on 2008-03-20
> **hyper_ch said:**
> fat16?

what's on sda5 and sda4?

The problem is those are all primary partitions (I think) so you can't create anymore partitions.

What is on sda5 and sda4; no idea. There is a guest user on the computer, could that be it..?

I'll try to remove the guest user, it's barely ever used anyways

---

### Post by notwen on 2008-03-20
It looks as if your current system may have a restore option.  What kind of system do you have and do you know if it has a Windows/System Restore option?  Those FAT32 and FAT16 partitions generally turn out to be partitions used in a System Restore.

---

### Post by adh2 on 2008-03-20
I use a Dell inspiron 6400 laptop...
There is a "fast format" thingie that restores the computer to (about) what it was when it was new; programs etc. Can that be it you think?
If so, what do I do next? :)

---

### Post by adh2 on 2008-03-20
I've downloaded the gparted live cd.. haven't used that before, do you think it might be possible to fix a partition with it? Or even remove the fat32 and fat16 partitions with it?

---

### Post by adh2 on 2008-03-20
hmm.. guess its better to create a new thread with this question.

---

### Post by barbedsaber on 2008-03-20
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")




if you run vista thats the way to got.


worked for me.

---

