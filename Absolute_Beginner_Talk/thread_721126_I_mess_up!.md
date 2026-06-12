---
title: "I mess up!"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Ryson on 2008-03-11
Hi there
I'm in a real problem
Today,I try to install Winutuxu (My friend said it's Windows XP and Linux in one,how can I resist? :P )
Anyway,I mess up.
Before,I can dual boot with Windows XP and Xubuntu
After fixing the grub thing,I select Windows XP and to my horror,it Winutuxu.It crash at BSOD,but we wouldn't get to that.
I know my orignal Windows Xp is still exist,because I just browse though it!
How to edit the grub to boot into my original Windows XP?

---

### Post by Ryson on 2008-03-11
PLEASE PLEASE HELP ME!!
I know I'm impatient,but I really really want my Windows XP  back!

---

### Post by hyper_ch on 2008-03-11
boot into the live cd and post the following:

```

fdisk -l

```

```

sudo fdisk -l

```

---

### Post by Ryson on 2008-03-11
Sorry for a noob question,but what does it do? 

And btw,I found out my Windows XP is

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

But after I change the root(hd0,0) into root(hd0,1) and try to save it,it wouldn't let me,saying that "Can't open or write file"

---

### Post by Ryson on 2008-03-11
Hey,I done it!

And I think you mean the computer,not the live CD:)

Disk /dev/sda: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66ff0e63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    7  HPFS/NTFS


Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd834d834

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        4870    18635400    f  W95 Ext'd (LBA)
/dev/hda5            2551        3442     7164958+  83  Linux
/dev/hda6            3443        3484      337333+  82  Linux swap / Solaris
/dev/hda7            3485        4820    10731388+   7  HPFS/NTFS
/dev/hda8            4821        4870      401593+   7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361344 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66ff0e63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161    7  HPFS/NTFS

---

### Post by Ryson on 2008-03-11
Hello,any help at all!!!!!!

---

### Post by hyper_ch on 2008-03-11
is the bios set to boot from teh sata drive? If so, then root (hd0,0) is correct... if not it should be root (hd1,0) to boot into windows.

---

### Post by forrestcupp on 2008-03-11
> **Ryson said:**
> Sorry for a noob question,but what does it do? 

And btw,I found out my Windows XP is

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

But after I change the root(hd0,0) into root(hd0,1) and try to save it,it wouldn't let me,saying that "Can't open or write file"

You couldn't write the file because you didn't open it with sudo privileges.

If you're just wanting to get rid of your Linux install and get rid of GRUB completely and just use the Windows boot loader, try using [Super Grub](http://supergrub.forjamari.linex.org/).  It's a CD that you boot to, and it has an option to restore the Windows boot loader.  That will overwrite GRUB for you.

---

### Post by Ryson on 2008-03-11
Ok,first
> is the bios set to boot from teh sata drive? If so, then root (hd0,0) is correct... if not it should be root (hd1,0) to boot into windows.

I don't know,sorry

> You couldn't write the file because you didn't open it with sudo privileges.

If you're just wanting to get rid of your Linux install and get rid of GRUB completely and just use the Windows boot loader, try using Super Grub. It's a CD that you boot to, and it has an option to restore the Windows boot loader. That will overwrite GRUB for you.
I never said I want to get rid of Linux!
I said I mess up my installion with Winutuxu and somehow the grub is mess up too and keep booting into Winutuxu instead of my original Windows XP

---

### Post by rillip on 2008-03-11
You have a lot of NTFS partitions.  Is Windows installed on the sata drive? Is it booting from the SATA drive?  Without understanding your partitioning scheme it's hard to tell you how to fix the grub menu.  I don't suppose you have a backup of it from before installing this Winutuxu>

---

### Post by Ryson on 2008-03-11
> You have a lot of NTFS partitions. Is Windows installed on the sata drive? Is it booting from the SATA drive? Without understanding your partitioning scheme it's hard to tell you how to fix the grub menu. I don't suppose you have a backup of it from before installing this Winutuxu>

Yes,it is booting from SATA,i think!
and my scheme(bear with me)is I think is Windows XP,first,then Ubuntu,then, SWAP,then Wintuxu,

I didn't backup it(stupid me!)

How to edit the grub thing to Windows XP instead of Winutuxu?
Do I need another program to do it or something?

Sorry,I'm half computer illiteraller (spelling?)

---

### Post by Ryson on 2008-03-11
Ok,I know I sound really rude and impatient but I honestly need to use Windows XP badly!!

---

### Post by Ryson on 2008-03-11
Sos!!

---

### Post by Ryson on 2008-03-11
Please Help Me!!

I Been Really Desparate To Get My Windows Xp Back!!

---

### Post by alzie on 2008-03-11
If you go into grub do you have a file called menu.old ?

Maybe you can revert to an old menu.lst?

Just a thought

Otherwise sudo gedit menu.lst but make a backup of your current grub menu just in case.

---

