---
title: "Windows no longer boots.."
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by Resin on 2005-11-25
Hey all,

I tried searching the forums to find someone with a similar problem, but I could only find solutions which involved re-installing grub..


My windows partition no longer boots :(  I'm using grub as my bootloader, heres the output I get when selecting windows:

-------------------------

Booting `Microsoft Windows XP Professional'

root (hd0,0)
 Filesystem type unknown, partition type 0x7
save default
make active
chainloader +1

--------------------------

Then it proceeds no further, this is as far as I get.  I thought I may have corrupted something, but I can access the windows partition from ubuntu just fine.

heres some more info from System > Administration > Disks

/dev/hda1
Windows NTFS

Any ideas on what the problem is? or better yet, a solution?

cheers

---

### Post by bfonseca on 2005-11-25
I have the same problem, I have not really looked into trying to figure this out, however I am going to be looking into it either tonight or tomowrrow.  If anyone can help us that would greatly appreciated.  I get the exact error. wierd.

Please help us
Thanks
Brian

---

### Post by Resin on 2005-11-29
[QUOTE=bfonseca]I have the same problem, I have not really looked into trying to figure this out, however I am going to be looking into it either tonight or tomowrrow.  If anyone can help us that would greatly appreciated.  I get the exact error. wierd.[/QUOTE]

Hey, did you find anything out?  I still cannot find out the reason why it doesnt work.

---

### Post by Vega on 2005-11-29
my suggestion is that you load the Windows Installation Disk and use the recovery console. I know of no commands but it works really well.

best of luck

---

### Post by Robgould on 2005-11-29
to boot back to windows, boot from your windows install cd to recovery console.  Run either fdisk /mbr or fixmbr.  The command is different depending on your version of windows.  This will remove Grub and allow your computer to boot directly to windows again.  You will have to use your ubuntu install cd in rescue mode to boot back to linux.  From there re-install grub.

---

### Post by shane2peru on 2005-11-29
I would try this.  I had to edit my Grub to get Windows to log in, because it wasn't in the menu.  If you boot into Linux and go to /boot/grub/  you should find a file called menu.lst open it with sudo gedit menu.lst  and then put a # in front of the line that **Filesystem type unknown, partition type 0x7**  This will comment out this line.  My menu list looks like this:
[B]title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/B]

I'm running XP Home, so it may be a little different, but I'll guess that is the problem.  I'm not a Linux pro, so this would be at your own risk, but should work!  Good luck!

Shane

---

### Post by Resin on 2005-11-30
[QUOTE=Robgould]to boot back to windows, boot from your windows install cd to recovery console.  Run either fdisk /mbr or fixmbr.  The command is different depending on your version of windows.  This will remove Grub and allow your computer to boot directly to windows again.  You will have to use your ubuntu install cd in rescue mode to boot back to linux.  From there re-install grub.[/QUOTE]

rock on, will give it ago this evening

---

### Post by lcg on 2005-11-30
[QUOTE=shane2peru]If you boot into Linux and go to /boot/grub/  you should find a file called menu.lst open it with sudo gedit menu.lst  and then put a # in front of the line that **Filesystem type unknown, partition type 0x7**  This will comment out this line.[/QUOTE]
Actually, this line is probably not present in his menu.lst. This is Grub's output when executing the 'root ...' line, as Grub can not read NTFS partitions. shane2peru, you also have this line in your config, so you probably have this warning when booting Windows as well.
In the Windows section of Grub, just change ```
root (hd...)
``` into ```
rootnoverify (hd...)
``` to get rid of this warning.

However, this doesn't solve the original problem. For that I'd suggest to go with Robgould's method. But be sure to make yourself comfortable with the procedures involved before you start to minimize the risk of ending up with a non booting PC.

Lars

---

### Post by shane2peru on 2005-11-30
[QUOTE=lcg]Actually, this line is probably not present in his menu.lst. This is Grub's output when executing the 'root ...' line, as Grub can not read NTFS partitions. shane2peru, you also have this line in your config, so you probably have this warning when booting Windows as well.
In the Windows section of Grub, just change ```
root (hd...)
``` into ```
rootnoverify (hd...)
``` to get rid of this warning.

However, this doesn't solve the original problem. For that I'd suggest to go with Robgould's method. But be sure to make yourself comfortable with the procedures involved before you start to minimize the risk of ending up with a non booting PC.

Lars[/QUOTE]
Lars,

You are right, I didn't notice at first, but he does say this is his output.  I also have what line?  I don't get warnings when booting into XP.  My system is working fine, to my knowledge.  I don't want to fix something that is not broken.:D  Can you clarify a little bit?  Thanks.

Shane

---

### Post by lcg on 2005-11-30
[QUOTE=shane2peru]You are right, I didn't notice at first, but he does say this is his output.  I also have what line?[/QUOTE]
A few lines above, you posted the part of your menu.lst to boot Windows XP. In there, you also had a ```
root (hd0,0)
``` line, which causes Grub to complain about not knowing the partition type of an NTFS partition.

[QUOTE=shane2peru]I don't get warnings when booting into XP.[/QUOTE]
Two possible reasons I can think of:
1.) You have XP installed on a FAT32 partition. I've seen a lot of laptops where the default installation of XP is on FAT32. IMO, that's a "bad idea"(TM). The same thing is probably true for workstation which come with Windows XP installed.
2.) The Grub lines disappear quite fast and you keep missing them. Grub does print all the lines it executes when booting a section in your menu.lst, so there has to be some lines of output. If the warning about an unknown partition type is in fact missing from these lines, see explanation #1.

[QUOTE=shane2peru]My system is working fine, to my knowledge.  I don't want to fix something that is not broken.:D  Can you clarify a little bit?  Thanks.[/QUOTE]
Actually, I couldn't agree more: Don't mess with a working system. (Now, if only I followed that advice a little bit more often myself. Ah, well ... ;))

HTH,
Lars

---

