---
title: "Dual Boot Ubuntu + XP = Grub Error 17"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by oldmanpete on 2007-01-29
Hi there. I know there are various threads on this issue already and have gone through many of them following instruction to try resolve the problem to no avail.

I recently purchased a 250GB HDD with the view of dual booting XP and Ubuntu. The XP install went on fine and was allocated 100gb of space. Popped in the live CD and went to manually partition the HDD.

They where then set up as follows

Partition         Filesystem       Size              used        unused     flags

dev/hda1         NTFS              100gb           2.59gb      97.4gb     Boot
dev/hda2         Ext3               14.88gb        2.04gb      12.85gb
dev/hda3         Linux-Swap     964.84mb
dev/hda4         Ext3               117.06gb      1.96gb       115.10  

(I am reading this information from within live CD so the used and unused space equates to availability after the installs)

Then mapped 
'/' to hda2
'swap' to hda3
and '/home' to hda4
(hda1 being the windows partition)

On reboot i am presented with 

Loading Grub 1.5
Error 17

This leaves me unable to access either the Ubuntu or Windows install and I have to revert to the Live CD which I am currently using. From here I have entered terminal and followed the instructions on reinstalling GRUB to the MBR

>type grub
>type find /boot/grub/stage1

but at this point i am present with error 15 - File does not exist

Any and all assistance would be greatly appreciated and I do apologize if i have posted this in the wrong place.

Thanks in advance!

---

### Post by BarfBag on 2007-01-29
Maybe since you have 2 EX3 partitions, grub isn't sure which one to list.  What's the purpose of the extra EX3 partition?  My advise is to reinstall Ubuntu, but this time - select the "Use Largest Contiguous Free Space" option.  This will auto partition the free space in a way that Ubuntu likes.

---

### Post by oldmanpete on 2007-01-29
my thinking was to keep root and home on separate partitions incase i ever wanted to do a clean install but not lose all my files. Forgive my ignorance but would using continuos free space leave home on its own partition?

---

### Post by BarfBag on 2007-01-29
> **oldmanpete said:**
> my thinking was to keep root and home on separate partitions incase i ever wanted to do a clean install but not lose all my files. Forgive my ignorance but would using continuos free space leave home on its own partition?

That's a great way to manage your partitions.  A lot of people do it that way.  Unfortunately, the option will only create two partitions - a swap and a root.  I can't think of any other way to fix Grub, though.  If anyone else has alternative advise, do share.

---

### Post by oldmanpete on 2007-01-29
Some further info

> **catlett said:**
> This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

```
sudo grub
```

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

```
find /boot/grub/stage1

```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Finally exit the grub shell
```
quit
```

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a  small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition,  grub will use the mbr. hd0 is the  grub label for the first drive's mbr.
Quit will exit you from the grub shell.



I have gone through the above procedure and its showing stage1 as (hd0,1)

Still get the same error when trying to boot up from the hard drive though!

---

### Post by oldmanpete on 2007-01-29
Having spent ages trying to figure this out the problem has been resolved (Cheers monkey!).

As I have not seen any reference to this in any of the other threads I have read on problems with the Grub setup I shall briefly explain what the problem was.

The motherboard I am using is of an older model and as such only searches for its MBR within the first 8gb of space on the primary HDD. As my initial install of Windows was at 100gb the MBR was being installed outside this 8gb and the motherboard could not find it.

The solution was to flatten the HDD, install windows to a partition of 5gb, then install Ubuntu to a 5gb partition. Then make a logical extension for the remaining /home and NTFS drives and obviously a small Linux-Swap partition. Grub then being inside the 8gb limit imposed by older models of motherboard booted with no issues and I now have successfully got a working dual boot system.

Certainly something to consider if everything else fails. Newer mobo's don't suffer from this problem as much but I'm sure there are people like myself still running old hardware!

---

### Post by egis on 2007-03-08
I have sata hard drive with one primary partition and 4 logical partitions under extended. When i formated one partition, after reboot i get this error.

These commands resolved my problem "grub error 17".

--
Egis

---

