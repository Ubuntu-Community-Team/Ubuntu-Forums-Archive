---
title: "Removing ubuntu"
date: 2005-11-14
forum: Absolute Beginner Talk
---

### Post by Mongey on 2005-11-14
Hi,
ok i installed ubuntu but i want to remove it. [IMG]http://img120.imageshack.us/img120/7493/untitled7ef.jpg[/IMG] im not sure which to remove/format. Is it the  5.68gb or the 290mb. I dont want to keep it cause i probley wont be allowed (im 14)Thanks for the help

---

### Post by Kyral on 2005-11-14
Well that bites that you won't get to keep it (Parents I assume? I hated that :D)

Which one has Ubuntu on it?

---

### Post by Pablo_Escobar on 2005-11-14
5,68 GB is a main partition (/) 290 MB is a swap partition. 
If You want to delete Ubuntu than You can delete them both. (but I'd make sure :) )

---

### Post by Mongey on 2005-11-14
yep parents, i'm not sure what drive it was installed on(ubuntu auto did it)

---

### Post by Mongey on 2005-11-14
Are u sure to delete both? Because if i mess this up im screwed:(

---

### Post by aysiu on 2005-11-14
If the partition is "healthy," but Windows has no idea what filesystem it's using, the partition is a Linux partition.

---

### Post by Mongey on 2005-11-14
[QUOTE=aysiu]If the partition is "healthy," but Windows has no idea what filesystem it's using, the partition is a Linux partition.[/QUOTE]
thank you ill post what happens next

---

### Post by Chayak on 2005-11-14
Well with all the Fat32 find the partition that isn't Fat32 and remove those.
Not allowed?  If it's a parent issue just sit down with them and talk about it.  I know this can be difficult but my father's comuter got bogged down with all kinds of excess programs and spyware so I wiped it and installed linux (this was about the fifth time I had to fix it).  All he cared about was surfing the net and getting email so he was happy, especially when he never got viruses or spyware.  I was happy because I didn't have to fix it every few weeks.  If you still want to keep using linux and learning about it, grab the live version and you won't have to install anything.

In short you're safe as long as you don't delete any Fat32.  Remove the two 'Health (Unknown Paritition)' and you'll be set.  If windows needed them they wouldn't be 'unknown'.  The way I would do it is first remove Grub then redo those partitions.

To remove Grub from your MBR.  Take your windows CD, boot it and go to recovery mode. Type ```
fixmbr
``` at the prompt to let windows fix the mbr the way it likes it and exit out of the disk, reboot into windows and format those two non-Fat32 partitions and you're done.

---

### Post by Mongey on 2005-11-14
well now ive got a big problem. I removed the two healty but unkown partions but i get (on boot) grub loading....please wait.... error 2. Well now im in big trouble

---

### Post by lik3n on 2005-11-14
[QUOTE=Mongey]well now ive got a big problem. I removed the two healty but unkown partions but i get (on boot) grub loading....please wait.... error 2. Well now im in big trouble[/QUOTE]

Oh yeah, I had that when I didn't like linux and wanted windows back on there.

Dumb, I was.


Ummm, I think how to fix it was you had to get a Windows disc and go into recovery mode. It'll ask you for your admin name and password. Once you enter that, I think you type "Fixmbr" (Without the quotes)

This will fix your master boot record (mbr)

I think this is the way to do it, if someone wants to back me up on this one before he does it, that'd be awesome.

**Edit:** Looks like I was right. Look right above your last post Mongey.

---

### Post by SSTwinrova on 2005-11-14
Actually, not quite as much as you think -- all that means is that Linux really is gone, now you just need to fix your MBR (i.e. overwrite Grub and let Windows boot itself again). I believe the command for this will just be:

```
fixmbr
```

at a Command Prompt from within XP (Start > Run > "cmd" (sans quotes) or Start > Programs > Accessories > Command Prompt). This is, of course, assuming you're running with admin priviliges in XP.

Source for this answer provided by: [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)

EDIT: That appears to be the right command, but if you can't get into XP (I was assuming you could, but now realize that post could have come from a different comp) then use lik3n's suggestion about the CD.

---

### Post by lik3n on 2005-11-14
Oh snap, I didn't know you could do it from the command prompt. That's awesome.

---

### Post by SSTwinrova on 2005-11-14
[QUOTE=lik3n]Oh snap, I didn't know you could do it from the command prompt. That's awesome.[/QUOTE]

Actually, you can't:

> Repairs the master boot record of the boot disk. **The fixmbr command is only available when you are using the Recovery Console**

I knew about the command and just assumed that it could be run from any command prompt. Stupid me for not reading the full page I got for my initial answer  :)

---

### Post by Mongey on 2005-11-15
damn it i cant find my xp cd, is there anyother way . please help. maybe a n00b guide

---

### Post by Chayak on 2005-11-15
Can't really help unless you have your Windows disk to boot into recovery mode, but if you can boot into XP go to the command prompt and type
```
C:\> FDISK.EXE  /MBR
```

Lesson for the future.  Keep your OS install disk and any driver disks that came with hardware in a safe place so you can get to them if you need them

---

### Post by Mongey on 2005-11-15
i have a knoppix disc it thats any help :_(

---

### Post by psusi on 2005-11-15
FDISK.EXE is a DOS program, it does not exist in non DOS versions of windows ( i.e. XP ).  

I am pretty sure that either grub or the linux fdisk are capable of restoring a normal MBR, but I'm not exactly sure how to do that.  If you can't find your winXP install CD, then you might try booting the ubuntu livecd and looking into running grub to restore the MBR.

[QUOTE=Chayak]Can't really help unless you have your Windows disk to boot into recovery mode, but if you can boot into XP go to the command prompt and type
```
C:\> FDISK.EXE  /MBR
```

Lesson for the future.  Keep your OS install disk and any driver disks that came with hardware in a safe place so you can get to them if you need them[/QUOTE]

---

### Post by Chayak on 2005-11-15
I realized that after I'd posted.  I don't know how windows likes it's mbr but it's probably wise to let it fix it to be safe.  Every text I have says to use recovery mode from the CD but if you don't have the CD...

Linux fdisk doesn't touch the mbr, just partition tables

You have knoppix? It's easier then just su and
```
install-mbr /dev/hda (or whatever your drive is)
```  It will overwrite your MBR and point it to the first partition, hopefully that's where you have windows installed.

---

### Post by Mongey on 2006-11-19
woah, that was one hell of an experience. Just over a year later i have returned and all i can do is laugh at how god damn stupid i was. ](*,) 

Over the past year i have uninstalled ubuntu, kubuntu, vista, FC5 among others. But i have still come back to the same one kubuntu :KS :KS :KS :KS :KS .

Id like to thank you guys for your help last year :D

Oh and i ended reinstalling. It was no problem and all went good.

---

### Post by cantormath on 2006-11-19
> **Mongey said:**
> Hi,
ok i installed ubuntu but i want to remove it. im not sure which to remove/format. Is it the  5.68gb or the 290mb. I dont want to keep it cause i probley wont be allowed (im 14)Thanks for the help

I cant think of a good reason to remove ubuntu.  You should use it.  Why would you not be allowed?

---

