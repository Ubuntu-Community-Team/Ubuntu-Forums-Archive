---
title: "Battle of the OSs!!"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by Apotheosis on 2006-09-25
So, a little while ago, I had a problem with Vista's MBR taking over Grub.  I finally got that worked out using [this]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub") thread and could properly dual-boot between Vista and Ubuntu.  Then, I had to reformat everything due to messing up some config files(:) ).  So, I reinstalled Vista first, and when I installed Ubuntu it appeared to overwrite Vista.  Vista was nowhere to be found in Grub.  So, I reinstalled Vista, and had the original problem all over again - Vista's MBR took over Grub.  So, I reinstalled Grub via the original instructions, and Vista is nowhere to be found, again.

It worked the first time, so I have no idea what the problem is now.

---

### Post by xpod on 2006-09-25
WOW...You seem like you done more re-installing than moi lately....:D 
If you install vista first then install Ubunto should`nt it be the same principle as it is with xp\ubu.....i.e all done for you??

---

### Post by bulldog on 2006-09-25
It seems the loader of Vista workes a little different then XP bootloader.

I didn't try  to do it with GRUB,

So I can't give you any usefull advice,and I think I never will cause I installed Vista for two days,and whiped it again,couldn't get the simplest things working.

No more Vista on my computer.

---

### Post by bodhi.zazen on 2006-09-25
[How to dual boot ubuntu and Vista](http://www.commonmancomputing.com/qd-linuxvistadualboot.txt)

---

### Post by Apotheosis on 2006-09-25
> **xpod said:**
> WOW...You seem like you done more re-installing than moi lately....:D 
If you install vista first then install Ubunto should`nt it be the same principle as it is with xp\ubu.....i.e all done for you??

No.  Microsoft decided they were the only/best OS around, so their MBR completly overwrites all others.

> **bodhi.zazen said:**
> [How to dual boot ubuntu and Vista](http://www.commonmancomputing.com/qd-linuxvistadualboot.txt)

This calles for a fresh HD.  I finally got everything back the way I like it... once again... so I would prefer not to reformat everything again.  Any other suggestions?

---

### Post by bodhi.zazen on 2006-09-25
With all your installs you have a fresh HD :lol:

Can you be a little more specific on your current problem?

What is your partition scheme? ```
sudo fdisk -l
```

What is now on your MBR ? Grub ?

What is> I finally got everything back the way I like it... once again...  mean exactly?
If everything is the way you like, what is the problem?

Last, the link I gave you gives clear directions and I think you should follow them ](*,), they were written by someone more knowledgeable then I :). Even tells you how to set up grub.

I know less (or should I say care less) about Microsoft then Bulldog.

---

### Post by Apotheosis on 2006-09-25
Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1798    14438400    7  HPFS/NTFS
/dev/hda2            7157        7296     1124550    5  Extended
/dev/hda3            1799        2435     5116702+  83  Linux
/dev/hda4            2436        7156    37921432+  83  Linux
/dev/hda5            7157        7296     1124518+  82  Linux swap / Solaris


What I ment by that by everything how I like it is: I got my wireless up, the programs I like, Automatrix installed, ect.

Yes, they were very good instructions and yes, I do have a semi-clean HD, but those directons call for a blank HD.  "Next, load up the LiveCD of Ubuntu Desktop and delete all partitions except for your Vista install partition."  If I delete my Linux partiton again, I will have to redo everything... again.

Edit to add - Being as specific as possible - Grub will not include Vista as in option when I start the computer.

---

### Post by bodhi.zazen on 2006-09-25
Thank you. Now I understand, sorry for the rant....

Try this:```
sudo gedit /boot/grub/menu.lst
```

Add:> title  Vista
root  (hd0,0)
makeactive
chainloader +1
boot

Save your changes, re-boot.

---

### Post by Apotheosis on 2006-09-25
Yeah, sorry I wasn't exactly clear on things.

Well, I did that and when I selected Vista in the menu it gave me a couple of lines of errors, one being Unknown Filetype, then proceded to boot Ubuntu.

I have been tinkering with stuff myself, so I think I may have messed something up.  I will re-install Vista and then follow your directions and see where that gets me.

---

### Post by wpshooter on 2006-09-25
Here is what I would do.  Well not exactly because I probably would not put VISTA on there at all to start with.

Get Killdisk program from this site and WIPE the entire drive.

[http://www.killdisk.com/](http://www.killdisk.com/)

Then install VISTA if you want.

Then install Ubuntu, preferrable from the ALTERNATE CD.

Good luck.

**BUT**, I am not positive that this will work because VISTA may not want to co-exist with another O/S.

---

### Post by Apotheosis on 2006-09-25
Wpshooter, at the beginning of all this, I installed Vista first on a clean HD, then Ubuntu which is what caused me to have the aforementioned problems.  How would what you told me to do change my situation in the slightest?

Bodhi, Well I reinstalled Vista and followed your instructions... and it worked!  Thanks a lot man.

---

