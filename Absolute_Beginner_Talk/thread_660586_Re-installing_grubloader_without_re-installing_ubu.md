---
title: "Re-installing grubloader without re-installing ubuntu?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by childofstrings on 2008-01-06
Hello Ubuntu forum,

I've been having booting issues with my computer and recently had to erase my MBR. I know grub loader was written to my MBR and I was wondering if there is any way to re-install grub loader without re-installing Ubuntu. 

I have a feeling that the easiest way to get grub loader back is going to be just re-installing Ubuntu, but I just spent all day getting my programs and drivers up to date and if I can, I'd like to avoid loosing all my hard work hehe. Butttt...if getting grub loader back is going to be complicated (and possibly dangerous), then I guess I'll just stick with a re-install (as unwilling as I am to do it)

Enough tl;dr

---

### Post by logos34 on 2008-01-06
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by childofstrings on 2008-01-06
Yayy!!! Thank you!!!

---

### Post by logos34 on 2008-01-07
my pleasure!  enjoy.  Mark as 'solved' (->thread tools)

---

### Post by antoz on 2008-01-07
Just did that yesterday by following the same instructions here [http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

What I did find though was, that it would not return the correct filesystem till I used the the Dapper live CD, not sure if it would have worked anyway? A

---

### Post by childofstrings on 2008-01-07
> **logos34 said:**
> [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

One quick thing I realized I forgot to ask...will this override any other bootloaders I have on my MBR? (Such as Windows XP)

---

### Post by logos34 on 2008-01-07
grub overwrites (and thus overrides) any bootloader on the mbr, including xp
s.  You can always reinstall windows bootloader with xp install cd or super grub disk

---

### Post by childofstrings on 2008-01-07
> **logos34 said:**
> grub overwrites (and thus overrides) any bootloader on the mbr, including xp
s.  You can always reinstall windows bootloader with xp install cd or super grub disk

Ahh...sorry to bother you again but could I ask how I would go about reinstalling the windows bootloader with the xp install cd? Do I need to re-install windows?

---

### Post by manmohanpv on 2008-01-07
try grub, download super grub iso and burn it...and boot from cd...

it will show u a prompt....and u can boot ur kernel from there...but windows...if it is in FAT-32...

but, i need to understand ur file system and ur harddisk type, is it SCSI for giving u the correct command..u should be careful with bootloaders...

read any documents from grub, will be helpful...

if u want both win and linux, u need to edit ur boot.ini and provide path for grub.bin there.for example...

c:\grub.bin="Linux"

-thanks
manmohan

---

### Post by gunbladeiv on 2008-01-07
new info there,

thank you manmohanpv, never knew how to boot with window's bootloader before.

---

### Post by childofstrings on 2008-01-07
> **manmohanpv said:**
> try grub, download super grub iso and burn it...and boot from cd...

it will show u a prompt....and u can boot ur kernel from there...but windows...if it is in FAT-32...

but, i need to understand ur file system and ur harddisk type, is it SCSI for giving u the correct command..u should be careful with bootloaders...

read any documents from grub, will be helpful...

if u want both win and linux, u need to edit ur boot.ini and provide path for grub.bin there.for example...

c:\grub.bin="Linux"

-thanks
manmohan

So I would just copy....
"c:\grub.bin="Linux"" into my boot.ini file? And that will load grub loader at startup?

---

### Post by dstew on 2008-01-07
You need to decide if you want to modify the Windows boot sequence to allow you to boot Linux, or have grub dual boot Windows and Linux. The latter is easier.

> So I would just copy....
"c:\grub.bin="Linux"" into my boot.ini file?No, that is not enough. You would have to install grub first into the MBR. After it is working, you need to use the dd command to make an image of the MBR that you save in the Windows root directory as the grub.bin file. Then, you have to modify the boot.ini file. Then, you have to re-install the Windows boot loader using the recovery console on the Windows restore CD, with the fixmbr command.

It is easier to install grub, as recommended by logos34: Boot LiveCD, open a terminal, and enter```
sudo grub
```That gets you the grub> prompt. At the grub prompt enter```
grub> find /boot/grub/stage1
```Whatever answer it gives, use as the root in the command```
grub> root (hdx,x)
```Then, setup grub in the MBR and quit```
grub> setup (hd0)
```You would have to do this anyway to create the grub.bin file to use in a Windows multi-boot attempt.

---

### Post by stump138 on 2008-01-07
there is a good guide for fixing grub [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
might be useful

---

### Post by vasili on 2008-01-07
nice...

---

### Post by sailor2001 on 2008-01-07
there is no need to install mbr if you are going to dual boot anyhow. Grub will boot xp or ubuntu, whatever you choose at startup screen. To set the default, gksudo gedit /boot/grub/menu.lst  and change default (probably set at 0 which is the first option on boot up .. count down from there to xp if you want that as default and make your edit)

---

### Post by childofstrings on 2008-01-07
I think I'll just go ahead and re-install Ubuntu. This all seems helpful but I dont think I want to go messing around in my windows boot.ini file since I messed it up pretty bad yesterday and I dont feel like going through that again. Also, I dont want grub loader to over write my windows boot if thats what your saying it will do.

But thanks to everyone for your help anyway.

---

### Post by dstew on 2008-01-07
I agree that trying to get Windows to dual boot Ubuntu is a bad idea. But, you really shouldn't be afraid to let grub into the MBR. If you don't like it, it can easily be fixed. Grub will not overwrite your Windows partition boot sector, only the MBR.

I know you see all kinds of trouble if you look at posts about grub problems, but these are only the people who have problems. There are hundreds of people who install grub, have no problems, and don't post to this forum because they don't have to.

If you read grub problem posts a lot, as I do, you see a recurring theme. New users are sometimes afraid to put grub into the MBR, and because of that they do strange things such as removing disks, then replacing them to "protect" their Windows disk MBR, or mis-directing grub to install into a partition instead of the MBR. They get into all kinds of trouble. Really, if you just use grub in a straightforward way, as it is intended, and put it into the boot disk MBR, you will not have any problems 99 times out of 100.

---

### Post by childofstrings on 2008-01-07
> **dstew said:**
> I agree that trying to get Windows to dual boot Ubuntu is a bad idea. But, you really shouldn't be afraid to let grub into the MBR. If you don't like it, it can easily be fixed. Grub will not overwrite your Windows partition boot sector, only the MBR.

I know you see all kinds of trouble if you look at posts about grub problems, but these are only the people who have problems. There are hundreds of people who install grub, have no problems, and don't post to this forum because they don't have to.

If you read grub problem posts a lot, as I do, you see a recurring theme. New users are sometimes afraid to put grub into the MBR, and because of that they do strange things such as removing disks, then replacing them to "protect" their Windows disk MBR, or mis-directing grub to install into a partition instead of the MBR. They get into all kinds of trouble. Really, if you just use grub in a straightforward way, as it is intended, and put it into the boot disk MBR, you will not have any problems 99 times out of 100.

Alright, Im still alittle confused. If I write grub to my MBR, what exactly will it do to my windows? Will it prevent NTLDR from showing up? What will happen? Thats my main concern and really the only reason why I hesitate to follow the instructions that everyone has given me above. I still want to be able to boot my windows. Currently I have a messed up boot.ini file that lists two non-functioning windows operating systems and one functioning one. While the functioning one is now set as my Default in NTLDR, I'd still like to have NTLDR show up right after the grub menu. This is the setup I had previously.

---

### Post by logos34 on 2008-01-07
Do you have a floppy drive?  Because you could put grub on a floppy and boot to that for ubuntu, and then let windows have the mbr.

---

### Post by childofstrings on 2008-01-07
> **logos34 said:**
> Do you have a floppy drive?  Because you could put grub on a floppy and boot to that for ubuntu, and then let windows have the mbr.

Unfortunately no, but that would be a good idea if I did.

---

### Post by dstew on 2008-01-07
> If I write grub to my MBR, what exactly will it do to my windows? Will it prevent NTLDR from showing up?grub will not touch NTLDR, which is a file in your Windows partition root directory that loads the Windows system. NTLDR is called by the partition boot code, which is also not touched by installing grub to the MBR. If you are worried about grub being able to boot your Windows system, try this harmless experiment:

1. Boot a LiveCD
2. Open a terminal window. Start grub```
sudo grub
```
3. At the **grub>** prompt try these commands. I am assuming that your Windows partition is the first partition on the first hard disk:```
rootnoverify (hd0,0)
makeactive
chainloader +1
boot
```If Windows boots, you really have nothing to fear by using grub to boot your system.

---

