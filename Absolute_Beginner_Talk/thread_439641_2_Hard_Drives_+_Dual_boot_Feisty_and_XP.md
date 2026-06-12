---
title: "2 Hard Drives + Dual boot Feisty and XP"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by homerj742 on 2007-05-10
I got 2 SATA hard drives.

1 - Windows XP

2- Blank (Brand new).

I would like to install Feisty Fawn on Hard drive 2 (and make it the primary), and Dual boot it in the most flawless way possible. I hear Feisty can automatically detect another OS, and setup dual booting easily?

I'm not too sure how to approach this, hence my post here. If anyone can point me in the right direction, I would greatly appreciate it!

---

### Post by Nekiruhs on 2007-05-10
Just install Feisty on the second drive, it will recognize windows, add it to the boot menu as an option and set up the dual boot for you.  If you have any problems come back here and we'll help you. Welcome to Ubuntu.

---

### Post by spur on 2007-05-10
Yes it will be detected automatically and somewhere in the install you will be asked for the default os. Choose the one you want. Then when you boot you can select the other if you wish. If you want to change it you might need advice on how to edit your Lilo or Grub files.( I have never ventured there.) I have dual booted on separate hds a number of times and had no problems.
This only works if you have windows installed first. Linux detects windows , windows does not detect linux. Also if you want to have older versions of windows and triple boot etc then you need to install oldest version of windows first, then new versions of windows and finaly linux last for auto detection to work.[img]http://img168.imageshack.us/img168/605/post108621154881434ly5.gif[/img]

---

### Post by mustang2 on 2007-05-10
I am getting ready to do this exact thing  but my ? is should I format the second HDD with windows prior to installing feisty or will feisty do this for me in it's format?  Thanks

---

### Post by spur on 2007-05-10
If the second hd is the one you want to put Feisty on it will be done by the install program. I would check at that step that it is doing what you want as you can change what it chooses to do. Make sure it is not reformatting your windows drive.

---

### Post by Najand on 2007-05-10
Feisty Live CD will format it before installation. Don't forget to add a swap partition.

---

### Post by mustang2 on 2007-05-10
OK I am going to show my ignorance here guys so please be gentle.First what do I look for to be certain it is formatting the correct drive ( the reason I bought the 2nd HDD is I can't take the chance on the install going south and corrupting the XP disc) and secondly  I need a bit more info on the swap partition? As in do I need it as the second drive is totally for feisty?

---

### Post by spur on 2007-05-10
Yes you need a swap partition and when you get to the partitioning stage of the install it will not let go on if you don't have one.
The partitioning stage will show you what it is going to do. So look at it closely as partitoning cant be undone. To be safe I would ensure you have a back up of all your data on a dvd or removable drive or somethign not attached at the time of partitioning. That said there should not be any problems if you read what it says on the screen before clcking next or ok.
The screenis pretty clear just make sure the hd being partitioned is not the one that is ntfs. You might have to go into advanced or manual and do it yourself if you want your swap partition to be on the linux hd as the system might want to put it on your xp drive if it has free space.
Before you go into advanced check what it wants to do as in all liklihood you will not need to do anything special and can accept what it says. Just read the screen first.

---

### Post by confused57 on 2007-05-10
> **mustang2 said:**
> OK I am going to show my ignorance here guys so please be gentle.First what do I look for to be certain it is formatting the correct drive ( the reason I bought the 2nd HDD is I can't take the chance on the install going south and corrupting the XP disc) and secondly  I need a bit more info on the swap partition? As in do I need it as the second drive is totally for feisty?

If you want to be sure about your XP disk, you might disconnect it during your Ubuntu install:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

The link is for IDE drives, but should work for SATA as well.  You could connect your new hard drive to the SATA#1 controller, install Ubuntu...reconnect your Window's drive, then boot into Ubuntu and add an entry to boot your Window's drive on SATA#2.

---

### Post by mustang2 on 2007-05-10
Thank you for the help. I quess the big thing is be awake and read before clicking. I would prefer all things feisty on the 2nd drive but plenty of room on the first if that is where it wants to put the swap file.

---

### Post by confused57 on 2007-05-10
Here's a guide for installing with the desktop live cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The swap space doesn't need to be but 1-2 Gb.

---

### Post by homerj742 on 2007-05-11
Thanks for the information guys. Looks like Feisty was ready for dual booting. I can't wait to do this...

---

### Post by homerj742 on 2007-05-11
Oh, and is there a way to see the files on the windows disk from ubuntu? There might a  time to I want to copy a file or two over.

---

### Post by prowlingbear on 2007-05-13
I researched this thread and installed Feisty on my second hard drive, and I am amazed at how easy it set up and I was up and running.

I have a bit of a problem now in that the when I try to boot up, the up/down keys don't work until after Ubuntu has booted up?

I have a PS2 keyboard going through a belkin kvm switch that works fine all of my boxes except this new install of Ubuntu on one box?

Any ideas on where I can find info to let me dual boot between XP on the one drive and Feisty on the other?

Thanks

---

### Post by homerj742 on 2007-05-14
> **Nekiruhs said:**
> Just install Feisty on the second drive, it will recognize windows, add it to the boot menu as an option and set up the dual boot for you.  If you have any problems come back here and we'll help you. Welcome to Ubuntu.

So I followed the directions, now my pc won't even boot up a grub menu. any suggestions?

edit: nevermind I changed the windows drive to be the main boot up drive in my bios. grub showed up. does this mean that the windows MBR is toast?

---

