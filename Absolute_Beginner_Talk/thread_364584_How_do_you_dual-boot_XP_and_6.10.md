---
title: "How do you dual-boot XP and 6.10?"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Aifel on 2007-02-18
OK, so I have 3 days to setup both WIndows XP (Pro SP 2) and Ubuntu 6.10 on my box before this coming Wednesday (February 21st). So, I need help. 

I'm aware that I have to first delete my existing Linux partitions, and I have no qualms about this, considering I've reinstalled more than 10 distros in the last month or so. Now, what comes after the deletion of my Linux partitions? And what kind of filesystem should the XP partition be?

---

### Post by draculashaun on 2007-02-18
I did it by wiping everything, then partitioning my hard drive into 4 partitions... 1 for XP, 1 for XP's swap file, 1 for ubuntu, and 1 for its swap file. If you do the partitioning with the XP fdisk, and install xp first, you should be fine to install linux on the other partitions. XP should be on a NTFS partition. When you install linux, format the partition for it as ext3, but -don't- reformat XP's partition(s). Hope that's helpful.

-Shaun.

---

### Post by rsambuca on 2007-02-18
XP should be NTFS.  I would recommend using gParted live CD to partition your drive ahead of time.  It is probably easiest to install XP first, and then ubuntu on another partition.  I like to have a smaller FAT32 partition because both systems can natively read/write to it (good for transferring files).  Alternatively, there are drivers for XP to read/write to ext2/3 drives, and there is an RC version of ntfs-3g to allow linux OS's to read/write to NTFS drives.

The ubuntu grub loader will write to the MBR and give you a choice of whether to boot XP or ubuntu.

---

### Post by islander_810 on 2007-02-18
Well, is there a spl prob or something cos i can't understand what could be the prob?

Anyway, i'd recommend installing XP first and then Ubuntu cos XP rewrites the mbr.

XP Partitions can be NTFS or FAT32. If u intend to use the two independently without any files being commonly used, like mp3 files or something, then i recommend u format windows partitions as NTFS. Else if u want to share files between the two, format the windows partitions as FAT32. 

FAT32 - can be read and written by both XP and Linux
NTFS - Linux doesn't write into NTFS by default, but can be configured to do so using ntfs-3g etc

Well, that's the most i can say in such a general manner.

---

### Post by Aifel on 2007-02-18
OK, thanks for the quick replies everyone. I will try this, and will probably need help configuring GRUB. 'TIl then, I'm off to partition my drives.

---

### Post by kvorion on 2007-02-18
You dont necessarily need to delete your existing linux partition if you want to dual boot xp and ubuntu. All that matters is that you have the required disk space. I would suggest you first install windows xp first as it writes over your MBR even if grub is installed. 
The windows xp can have ntfs or fat32 filesystem: it is upto you to choose which one you want depending on your needs.
It is best to use a partitioning tool to create the partitions beforehand where you want to install your operating systems. On the other hand you can also keep some free space unformatted, so while installing ubuntu, you can select the option of 'use the available free space.'
Format your ubuntu partition in ext3.

---

### Post by benfindlay on 2007-02-18
If Winblows is already installed, then grub should automatically realise this and set up your boot list accordingly. Admittedly, it will boot Ubuntu by default, but you can edit this in seconds to make Winblows the default boot OS.

Hope this helps!

---

### Post by Aifel on 2007-02-18
OK, for some reason, the XP CD won't boot... Any suggestions?

---

### Post by benfindlay on 2007-02-18
check your boot order in the bios to make sure the cd is given priority over your hard drives

---

### Post by Aifel on 2007-02-18
Yes, I've done this, but it says that the CD I'm using is not bootable. I'll try to dig up another cd...

---

### Post by cornellpd on 2007-02-19
> **benfindlay said:**
> If Winblows is already installed, then grub should automatically realise this and set up your boot list accordingly. Admittedly, it will boot Ubuntu by default, but you can edit this in seconds to make Winblows the default boot OS.

Hope this helps!
I am searching the forums to find out how to make XP the default boot with ubuntu already installed and I came across this.  How do you edit this to make xp the default?  I need to do this to appease my wife-she doesn't Ubuntu.  Thanks

---

### Post by rsambuca on 2007-02-19
You must edit your menu.lst file.  It is what tells grub where to find the different operating systems.  To do this, open a terminal and enter```
gksudo gedit /boot/grub/menu.lst
```
After entering your password, a new window will open up (the gedit text editor).  There will be a line in there that says "Default=0"

You want to change the number "0" to the entry corresponding to Windows XP.  Keep in mind that the numbering starts at zero, not one, and that you also have to include the line that indicates "Other operating systems" in your count.  Thus if ubuntu is 0, the recovery mode is 1, the memory check is 2, the Other Operating Systems is 3, Windows 4, for example.  Then just change the line to Default=4 in this case.

---

### Post by cornellpd on 2007-02-19
thanks for the quick reply-even if you choose not to help any more...when I enter that command-it tells me "bash: menu.lst; command not found"
I assume I am not on the right level to run that command-what should I type and what does it mean?

---

### Post by Jimmy_r on 2007-02-19
You may want to check my signature, SUM will let you change default boot without messing with config files.

---

### Post by rsambuca on 2007-02-19
> **cornellpd said:**
> thanks for the quick reply-even if you choose not to help any more...when I enter that command-it tells me "bash: menu.lst; command not found"
I assume I am not on the right level to run that command-what should I type and what does it mean?
Just copy and paste the command from my last post and it will work.

---

### Post by cornellpd on 2007-02-19
Yes-I saw my typo not a space after gedit.  I don't see the line Default=0.  There is a line like this...

Default                          0

...above where all of the OS's are, is that what I change??

Thanks.

---

### Post by Jimmy_r on 2007-02-19
That is correct.

---

### Post by rsambuca on 2007-02-19
Yeah, that's the line.  Sorry, trying to go from memory here as I am booting from XP right now.  Every line that says "Title" is counted, starting at zero.

---

### Post by cornellpd on 2007-02-19
Thanks-this has been on ongoing process for me, tried for a while to get ubuntu to work on an old laptop-couln't.  Finally got xubuntu to work on it-till Xfce was screwing it up constantly.  Tried to install from alternate to main computer, couldn't-bad disk?  Finally booted up the live dvd I made and installled from there, but there was already a partially created Ubuntu from the alternate-so I made a two new partitions for the live install-now, I was just trying to get rid of the alternate install partitions, and it wiped out my GRub-so now I have to fix the MBR before I continue....but I am learning!!  And that is the whole purpose of this.  Besides-my wife will stop yelling about her lost pictures in a week or two!:lolflag: Thanks.

---

### Post by NeoGreen on 2007-02-19
I had the same problem when trying to create a dual boot.  I didn't install Linux first though.  I first installed Windows XP and created the partitions for Linux and Windows first using the Windows XP CD.  I tried to do it the by installing Ubuntu first but I just could get it work.  It was way to complicated.  If it isn't too late, try installing XP first then Ubuntu.  The Windows XP install CD comes with a really easy to use partitioning program.

---

### Post by Sbarton on 2007-02-19
Just for your info this is another site worth a visit for dual booting
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by rsambuca on 2007-02-19
You can even make her happier by decreasing the timeout line.  I have changed mine to 2 seconds.  Since my wife just wants it to go into XP, it is quick for her, but I know when to press a button to get into one of my linux distros.  Once you press an arrow key, the timer stops so you can take your time selecting which system you want.

---

### Post by cornellpd on 2007-02-19
> **rsambuca said:**
> You can even make her happier by decreasing the timeout line.  I have changed mine to 2 seconds.  Since my wife just wants it to go into XP, it is quick for her, but I know when to press a button to get into one of my linux distros.  Once you press an arrow key, the timer stops so you can take your time selecting which system you want.

Yes-that is perfect-I just completed the new install and am changing the default boot (again, I   guess I didn't count "other operating systems" as an entry!!)  I do see how it works now though.  Going to change the time frame also-thanks.

---

### Post by cornellpd on 2007-02-19
> **Sbarton said:**
> Just for your info this is another site worth a visit for dual booting
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

Thanks Sbarton-I've used this site during my trials and tribulations.  All is well now-I have the default set, the time set, and I need to do my updates.  However-why, pray tell, is there  3  Dell Icons on my desktop-could it be that I partitioned wrong?  Can I remove them without hurting Windows?

---

### Post by cornellpd on 2007-02-19
The Dell Icons must be in my start up settings/configurations...enough of them for now-after installing updates, I seem to have added duplicate boot entries in the boot selection-can I go into the same place as above that we talked about and just delete the duplicates?

---

### Post by cornellpd on 2007-02-19
> **cornellpd said:**
>  I seem to have added duplicate boot entries in the boot selection-can I go into the same place as above that we talked about and just delete the duplicates?

Nevermind-I just went into the /boot/grub/menu.lst and deleted one of them out, restarted, and it is gone from the boot selection.  Now to figure out the icons...

---

### Post by Sbarton on 2007-02-20
Sorry about delay in replying. Glad you sorted and edited the menu.lst. As for the Dell Icons, what are they, shortcuts? Is it possible to try saving one somewhere (pen drive perhaps) and then delete one shortcut (if it is a shortcut!!) Make sure first that it is one! If they are 'files' then I would not remove them.
regards

---

### Post by cornellpd on 2007-02-20
they are icons showing that I have mounted these particluar partitions in my hard drive.  I can remove them with 
sudo umount /media/sda1/

but then when I reboot they come back-how do I keep them unmounted?

---

### Post by Sbarton on 2007-02-21
Have a look at the following item:
[http://www.ubuntuforums.org/showthread.php?t=247037&highlight=removing+mounted+icons](http://www.ubuntuforums.org/showthread.php?t=247037&highlight=removing+mounted+icons)
There are other posts available with same problem.You can try a search in Ubuntu Beginner Forum and view them.
regards

---

