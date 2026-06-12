---
title: "[SOLVED] Linux Noob Questions"
date: 2006-02-08
forum: Absolute Beginner Talk
---

### Post by xHero on 2006-02-08
1) How come I cannot connect to the internet even though it says that my wireless signal is at 92%?  I cannot send IMs or access any websites.

2) How do I partition my Hard Drive to boot Windows and Ubuntu?  And how do I set it up so that Ubuntu is on the right partition...

Thanks,

xHero

---

### Post by z|x on 2006-02-08
[QUOTE=xHero]
2) How do I partition my Hard Drive to boot Windows and Ubuntu?  And how do I set it up so that Ubuntu is on the right partition...

Thanks,

xHero[/QUOTE]

Some specifications would have helped.

1. If you already have a partition, then backup that partition completly.
2. Take down the capacity of both the partitions.
3. Start the installation and when you reach the partitioning setup, choose the manual mode.
4. Select the partition that has approximatly the same capacity as the 1 that you backed up. 
5. Select "Finished..."

Once installed, Ubuntu will detect the other operating systems and accept when asked for installing GRUB for booting. Then every time you start your computer, you will be asked which OS to boot into.

---

### Post by xHero on 2006-02-08
1. I have no partition, I don't know how.
2. N/A
3. Thanks
4. Huh? As in space?
5. Ok cool


And the wireless?

---

### Post by Pragmatist on 2006-02-08
1.) Need more info on this question.  First you should check the network configuration via something like System-->Network Admin I'm not in GNOME, but look through the menus and you'll find the network config program.  Make sure the connection is enabled and that you have DHCP set if that is appropriate.  What are you using? Cable, DSL?

Send the output of these commands: ```
ifconfig
``` ```
ping -c 5 66.102.7.99
``` 

2.) What does your current partition table look like?  try: ```
fdisk /dev/hda
``` in a terminal window.  In general, Windows likes to be on the first primary partition (usually /dev/hda1).  After that, your Ubuntu partitions are fine the way they are.  So, if you just installed Ubuntu, everything else being equal, it might be easier to install windows on the first partition (you can use fdisk, just make sure that the first partition has the right type, FAT or NTFS, depending on your Windows version).  Then install ubuntu and when the installer prompts you for partitions, begin with /dev/hda2 or anything less than the first primary partition.  As for Linux partitions, you want at least 3 partitions. A boot partition (/boot) of around 100MB and set this to be bootable, a root partitions (/), and a swap partition which should be between 1 and 3 times the size of your RAM.

Hope this helps.

---

### Post by z|x on 2006-02-08
[QUOTE=xHero]1) How come I cannot connect to the internet even though it says that my wireless signal is at 92%?  I cannot send IMs or access any websites.

2) How do I partition my Hard Drive to boot Windows and Ubuntu?  And how do I set it up so that Ubuntu is on the right partition...

Thanks,

xHero[/QUOTE]
Another way, you can do the partitioning is by:
1. Backing up your partition completly.
2. In windows, go to Control Panel >> Administrative Tools >> Computer Management >> Storage >> Disk Management.
3. Select the partition that u just backed up, right click and delete the partition.
4. Run the Ubuntu Install. When asked which partition to use, go to manual mode.
5. Select unpatitioned space and partition it according to how you want.
6. Continue with the installation procedure.

---

### Post by xHero on 2006-02-08
What program do I use to partition my HD?

Also where you put in:

```
ping -c 5 66.102.7.99
```

Do I put in my IP there?  Remote or Local?

---

### Post by z|x on 2006-02-08
[QUOTE=xHero]1. I have no partition, I don't know how.
2. N/A
3. Thanks
4. Huh? As in space?
5. Ok cool


And the wireless?[/QUOTE]
Since you haven't got any partition (drives), it would be better to backup your whole system, and start windows installation from scratch. While installing windows create a partition. After that install Ubuntu in the unused partition.

---

### Post by z|x on 2006-02-08
[QUOTE=xHero]What program do I use to partition my HD?

Also where you put in:

```
ping -c 5 66.102.7.99
```

Do I put in my IP there?  Remote or Local?[/QUOTE]
you can use partition magic.

You put in the ping commands in the terminal

---

### Post by Bartender on 2006-02-08
The best guide I know of for dual-booting -

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

If you can, set your computer up next to an internet-connected computer so you can follow the steps precisely.  I tried printing the guide out but none of the graphics came thru.  Used the "Ubuntu+NTFS" guide, made a FAT32 partition, it worked great.  Windows will see the FAT32 partition automatically but you'll probly have to mount that partition in Ubuntu so that it can use.  Don't worry, this isn't hard, just different for a Windows user.  1st things 1st.   

Do you have Windows installed already, and you've been using a LiveCD?  Couldn't tell from your original post.  Asking this cause it works better to have Windows laid down 1st, then install Ubuntu.  If Windows is already there, back up your data, defrag, find your Windows CD and the 25-character key code, take notes as you go along.  It should go OK but you want to be prepared. 

Are you planning to use a stamped CD or download/burn?  If downloading, please use an md5 utility to check the download against the md5 checksums listed at the website where you got the download, and burn the CD at a SLOW speed.  Anything above 2X just gets riskier and riskier.  Use the "test" or "verification" option when burning.  There are several md5 checksum utilities for Windows users.  Some are easier than others.  It's worth the extra effort to learn about them.  I liked md5Summer because it was really easy but that utility was poo-poohed by some Linux aficionados.  It worked for me but what do I know ;) 

EDIT: It sure sounds like zx knows more than me, but in my case Windows had the whole HDD.  I tossed the Ubuntu install CD in the tray without doing a thing to change that.  All partitioning was done in GRUB using the above-mentioned guide.  

Can't help you w/ wireless...

---

### Post by z|x on 2006-02-10
[QUOTE=Bartender]The best guide I know of for dual-booting -

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

If you can, set your computer up next to an internet-connected computer so you can follow the steps precisely.  I tried printing the guide out but none of the graphics came thru.  Used the "Ubuntu+NTFS" guide, made a FAT32 partition, it worked great.  Windows will see the FAT32 partition automatically but you'll probly have to mount that partition in Ubuntu so that it can use.  Don't worry, this isn't hard, just different for a Windows user.  1st things 1st.   

Do you have Windows installed already, and you've been using a LiveCD?  Couldn't tell from your original post.  Asking this cause it works better to have Windows laid down 1st, then install Ubuntu.  If Windows is already there, back up your data, defrag, find your Windows CD and the 25-character key code, take notes as you go along.  It should go OK but you want to be prepared. 

Are you planning to use a stamped CD or download/burn?  If downloading, please use an md5 utility to check the download against the md5 checksums listed at the website where you got the download, and burn the CD at a SLOW speed.  Anything above 2X just gets riskier and riskier.  Use the "test" or "verification" option when burning.  There are several md5 checksum utilities for Windows users.  Some are easier than others.  It's worth the extra effort to learn about them.  I liked md5Summer because it was really easy but that utility was poo-poohed by some Linux aficionados.  It worked for me but what do I know ;) 

EDIT: It sure sounds like zx knows more than me, but in my case Windows had the whole HDD.  I tossed the Ubuntu install CD in the tray without doing a thing to change that.  All partitioning was done in GRUB using the above-mentioned guide.  

Can't help you w/ wireless...[/QUOTE]
hey, I guess I'm a newer noob than you (not saying that you are a noob). I just got ubuntu installed 2 days ago. 
Well, I have never tried defragmenting and then partitioning the hard drive. I would just back up the whole drive, format the whole drive and then partition it and then format again. But since, many users on this forum have said that just defragmenting the drive and then partitioning is enough, i dont think it will be a problem.

---

