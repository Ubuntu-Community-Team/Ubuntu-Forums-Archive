---
title: "[SOLVED] Help - i didn't partition the drive"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by beckym@cincoed on 2008-03-28
I've done something really stupid - i went to install ubuntu 7.10 - i selected "guided" and was expecting to get the option to create a partition but an option never came - it just installed ubuntu and now i can't boot into windows vista and access my files there !  I tried to reinstall vista but it says it can't install onto a drive that isn't ntfs - when i try to reformat the drive it comes up with an error and won't let me.  fortunately i backed up all my files but obviously i have to install vista before i can access them  - can i create a partition that is ntfs from within ubuntu and then install vista into there?  please help.....

---

### Post by wolfen69 on 2008-03-28
try partedmagic. [www.partedmagic.com](www.partedmagic.com)

---

### Post by lswest on 2008-03-28
first off, don't panic, anything can be fixed ^^
can you post the output of
```
sudo fdisk -l
``` from the terminal (go to applications-->accessories-->terminal).  And yes, you can shrink Ubuntu's partition, make an ntfs partition and then install vista to it, and restore GRUB so ubuntu is bootable, but let's just check if there's still anything left.  If not, i can guide you through how to install vista again.

---

### Post by beckym@cincoed on 2008-03-28
thankyou soooooo much :)




Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19268   154770178+  83  Linux
/dev/sda2           19269       19452     1477980    5  Extended
/dev/sda5           19269       19452     1477948+  82  Linux swap / Solaris
becky@becky-desktop:~$

---

### Post by Inxsible on 2008-03-28
Too late. You nuked your ntfs partition, meaning you erased Vista. 

If you have the install discs for Vista, you will need to format the drives to ntfs and then install Vista. Once you are done, you can install Ubuntu later, if you haven't done much with Ubuntu, you might just want to get rid of it and install Vista first.

Its always better to install Linux after Windows in a dual boot.

---

### Post by kwacka on 2008-03-28
What size partitions do you have?

If you look under System --> Admin is there a partition editor entry?

If not, use package manager to install it.

You can use this to resize the partitions to make space for Windows.

Then search here for modifications to 'grub' to enable dual booting.


edit: you cannot use partition editor on a mounted disk; use LiveCD.
Apologies for mis-insforming you (bangs head on desk).

---

### Post by dorkdork777 on 2008-03-28
Pretty sure it would be a better idea to use a Live CD to do the partitioning, or else you'd have to unmount the Ubuntu partition to resize it. The gparted Live CD does the job for me, but AFAIK the Ubuntu live CD has the partition manager on it, accessible from the menu described above.

---

### Post by beckym@cincoed on 2008-03-28
at the moment i can't find a partition manager but i'm just installing some updates so i'll check if i have it when i've finished the install

---

### Post by Inxsible on 2008-03-28
> **beckym@cincoed said:**
> at the moment i can't find a partition manager but i'm just installing some updates so i'll check if i have it when i've finished the installthe partition manager is not installed by default on the ubuntu installation. you will have to use the live cd 
 or get a live cd for GParted.

---

### Post by beckym@cincoed on 2008-03-28
thankyou for your help.............i'll see if i can sort it

---

### Post by lswest on 2008-03-28
Okay, so what you want to do is boot into the liveCD, or to download a gparted liveCD, but i'll assume you're just going to use the liveCD.

boot it, then go to system-->administration-->Gnome Partition Manager

then choose your linux partition and resize it. (right-click, resize)

after that is done (might take a while, so just be patient) reboot the PC, and boot to your vista CD/partition and install it into the empty space (it should be able to format the free space to ntfs, if not, reboot back into the liveCD and create a partition of ntfs from the free space).

once Vista installs boot back into the liveCD and then do
```
sudo grub
find /boot/grub/stage1
root [the output of the above command, something like (hd0,0)]
setup [the first bit of the output from the first command, like (hd0)]
quit
``` in the terminal - each line is a separate command, then reboot and grub should be restored. 

if not, have a look at this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by beckym@cincoed on 2008-03-29
Okay, so I've resized the partition, rebooted into vista cd and windows install couldn't format the partition, so i boot back into ubuntu liveCD and do it there. then i boot back into vista install, and it still seems to want to reformat the partition - this time it seems to reformat (which only seems to take 20 seconds?)  but it still won't install vista.  i'm hearing from reading other threads that vista doesn't like installing into a partitioned drive, and also that perhaps the problem might be the partition manager i've used (gnome) and how that might deal with partitions - so i'm thinking perhpas using a different tool to repartition the drive?  any ideas :-(

---

### Post by angry_johnnie on 2008-03-29
Maybe you already thought about this, but where did you create your ntfs partition?  I think Vista will  claim the first primary partition of your hard drive for itself.  Also, Vista needs at least 20 Gb.  Did you allocate enough space?

---

### Post by lswest on 2008-03-29
What the guy said before me is correct, (at least, it is in the case of my HP laptop) Vista reinstalled to the first primary partition (which is only ever going to be Vista, i group my linux into an extended partition with /home, /, and swap).  If it's not at the start, you can move the partition (either with a move function, or by deleting it and "resizing" the partition in front of it so the free space is before that partition).  And yes, Vista, by default, does a "quick format" of the partition, which takes roughly 20-30 seconds.  Oh, and thanks for the thanks ^^  Also, what laptop/PC is this you're trying to re-install on?  Maybe there's some info on the web about it.

---

### Post by beckym@cincoed on 2008-03-29
ooh thankyou - i will try that. i am on a dell dimension e520 - i've tried the dell website and found somebody with similar problem - it came down to the order in which it is booting - i've changed that with no joy - but changing the partition order is well worth a go ...... wish me luck........

---

### Post by barbedsaber on 2008-03-29
just as a note, please please PLEASE don't make multiple threads about the same problem, I know that your problem seems more important than anyone elses (I have been guilty of thinking that before) but it won't get you any help faster, the only real way to speed up help, is to have a title that explains what the problem is, and that you go into detail about the problem in your .


thanks.

---

### Post by beckym@cincoed on 2008-03-30
I did it! thankyou for all your advice - even though it caused a number of hours of frustration it worked out ok in the end as even vista is working quite fast now that i've got rid of most of the stuff on there (which i obviously didn't need)i was also able to recover all my files via my backup disks.

If anybody is reading this thread because they have the same problem - basically the only way i could sort it was by taking out both partitions using Ubunutu LiveCD and reformatting the whole drive as FAT32 (vista wouldn't even accept being the primary drive it wanted the whole thing before it would install!) - i then booted into vista installation and got vista
to reformat the partition as ntfs, as soon as it had done this it happily installed itself. Now its back to getting ubuntu back on there, preferably without nuking vista this time :)

---

### Post by lswest on 2008-03-30
Glad you got it sorted, and if you would be so kind as to mark this thread as solved (using the thread tools at the top of the thread) people who have the same problem will know and answer is here.  Thanks! and enjoy your Ubuntu experience ;)

---

