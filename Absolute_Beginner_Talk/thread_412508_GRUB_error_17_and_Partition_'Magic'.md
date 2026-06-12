---
title: "GRUB error 17 and Partition 'Magic'"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Zeedok on 2007-04-18
So I have had an Ubuntu install and Win XP happily coexisting for six months. Needed to shuffle around my drives to make space for my Music collection so I (stupidly perhaps) used a third party commercial partition manager to delete a couple of partitions and increase the size of my 'music one'. This physical drive had my Ubuntu partitions on it (though nothing else - my WinXP and data were on other physical drives).

The partition manager rebooted the system to perform the changes and now GRUB no longer works.

I get:

```
GRUB Loading Stage 1.5

GRUB Loading, please wait . . .
Error 17
```

I can't seem to boot from Live CD (yes I checked the Boot sequence in the BIOS).

HELP!!

---

### Post by Zeedok on 2007-04-18
Ok . . . So I must have had a dodgy 7.04 Beta disc, my 6.1 disc allows me to boot off the live CD.

i found this post([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) and thought I might try it I think it should solve my problems . . . shouldn't it?

---

### Post by Terl on 2007-04-18
> **Zeedok said:**
> Ok . . . So I must have had a dodgy 7.04 Beta disc, my 6.1 disc allows me to boot off the live CD.

i found this post([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) and thought I might try it I think it should solve my problems . . . shouldn't it?

I would give it a go.  

You do know what happened, right?  You originally had a certain number of partioins on the drive.  Ubuntu knew it was, say, on partition 4 of the drive, but you deleted things and altered the drive so now Grub is confused because of the change hence the error.

---

### Post by tchoklat on 2007-04-18
should - give it a go. A better way to resize/ move partitions is GPartEd avalable for download and burn to a liveCD

---

### Post by Zeedok on 2007-04-18
SOLVED!! That thread did the trick.

Thanks for the replies (and the reassurance). Once again the Ubuntu community provides awesome support - as a real Newbie (who can't stop fiddling with things and stuffing them up!!) I really appreciate the help you guys offer!

PS I thought about using GParted, but I tried once to partition an external drive and had some trouble - hence the use of Commercial software - should of known FOSS usually does it better.

---

### Post by Zeedok on 2007-04-18
SPOKE TOO SOON . . .

I can boot my WinXP partition (which has stayed on the same virtual and physical (C:) drive I guess) but now GRUB can't find my Ubuntu Partitions!

What's the next step?

---

### Post by Terl on 2007-04-18
Can you boot from the live cd?

Do you know how your drives are setup and what they are called?  What has to happen is the menu.lst needs to be corrected as it is pointing toward the old partition number.  Once you know the partition Ubuntu is on and can boot from the cd (we need the terminal) we can fix this.

---

### Post by Zeedok on 2007-04-18
Yes I can now boot from the live CD. I have two physical drives (hda = WinXp, hdb = music partition and Ubuntu partitions). I'm not sure what the partitions will be called now (eg hdb3 or 4), but I will be able to work that out from GParted after I've booted from the live CD - Correct?

How do I correct the menu.lst?

---

### Post by Terl on 2007-04-18
Once you know what the partition number is do this from the terminal:

sudo mkdir /mnt/here

sudo mount /dev/hd# /mnt/here (the # will be what the partition of your ubuntu install is)

chroot /mnt/here (now you are in your ubuntu install)  

Do you know how to use Vim?  If not you can try this (if you can use vim just use vim instead of gedit below):

sudo gedit /boot/grub/menu.lst

Find the section that is for ubuntu and correct the partition number.  Save it.  Exit terminal.  Reboot and try.

---

### Post by freebird54 on 2007-04-18
I had a long post nearly entered on how to do this - but all you really need is to open a terminal and

sudo fdisk -l

This is from the Live CD. BTW. This willl print out a list similar in structure to this:

```
freebird@roost:~$ sudo fdisk -l
Password:

Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3824    30716248+   b  W95 FAT32
/dev/hda2            4869        5129     2096482+  82  Linux swap / Solaris
/dev/hda3            5130       19457   115089660   83  Linux
**/dev/hda4            3825        4868     8385930   83  Linux**

Partition table entries are not in disk order

```

Check out the **bolded** line: it is smaller than the other ID 83 line, so it is the root&boot partition.  Grub will will see this drive as **(hdo,3)**.   This is becasue Grub counts from** 0,0** rather than **a,1**.  Write this value down - you'll need it! :)

If you need more - come on back.  Here too is a helpful link about Grub and all the things you can do with it.  [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

What you need to do now is get into your system, then edit your /boot/grub/menu.lst to match your new partition setup.

---

### Post by Zeedok on 2007-04-19
Sorry Terl but your suggestion didn't seem to work - when booted with the live CD I can't correctly mount my linux partitions, therefore when I try to edit my /boot/grub/menu.lst a blank page comes up. Sudo fdisk -l yields:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        4862    39021885    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         122      979933+   b  W95 FAT32
/dev/hdb2   *        8786        9729     7582680   83  Linux
/dev/hdb3             123        8785    69585547+   f  W95 Ext'd (LBA)
/dev/hdb5             123        7916    62605273+   7  HPFS/NTFS
/dev/hdb6            8741        8785      361431   82  Linux swap / Solaris

Partition table entries are not in disk order

```

How can I mount my Ubuntu partitions so that I can edit my menu.lst? How do I edit it so it works well? Which one is my Ubuntu boot drive hbd2 (=ext partition) or hdb6 (=swap partition)?

---

### Post by Zeedok on 2007-04-19
SOLVED it!!!

Followed the steps provided here: [http://ubuntuforums.org/showthread.php?t=406271&highlight=edit+with+nano]("http://ubuntuforums.org/showthread.php?t=406271&highlight=edit+with+nano")

I couldn't work out how to save when using the file editor NANO, so I substituted ```
nano
``` with ```
gedit
``` and then I was able to change all the old hd(1,2) entries to hd(1,1) - which was what my linux partition had been renamed to after my re-sizing and maipulating of partitions.

Now I am all sorted. Thanks for all the help.

---

### Post by Terl on 2007-04-19
Excellent!!  I just saw your post.  Sorry I could not be on earlier (I was responding from work yesterday, as I am now).  I know that feeling of triumph when you finally get it fixed.  :popcorn:

---

### Post by Zeedok on 2007-04-19
Yes that moment of triumph is great. I danced a jig! 

Unfortunately when I stopped  dancing I realized that my progress had not actually 'solved' my problem but merely  mutated it into some other boot nightmare.

Given that 'Feisty' is literally here and I don't have many configured files etc I've to do a clean install (my data's elsewhere).

Hopefully a fresh GRUB will work fine!

---

### Post by Terl on 2007-04-19
I've done the premature dance before too.  Oh well....

A clean install should fix it up though.  I like doing them better than just an upgrade anyway.  Just seems cleaner and smoother.

What happened with the booting?  One of the other os's fail?

---

### Post by Zeedok on 2007-04-19
No WinXP still boots fine. I can get the Ubuntu Splash screen then a new error message.

With the amount of time I've already devoted to this problem I figure I'm better off with Feisty (especially since it's supposed to migrate bookmarks and install codecs by itself!).

---

### Post by Terl on 2007-04-19
I installed the beta of Feisty and have been very pleased so far.  It does indeed migrate bookmarks, even wallpaper.  I did the wallpaper thing and had the stupid windowsXP logo on my Feisty install.  It lasted only until I got to the menu entry to change it.

---

### Post by Zeedok on 2007-04-19
Does it migrate firefox extensions as well as bookmarks? That would be really cool!

---

