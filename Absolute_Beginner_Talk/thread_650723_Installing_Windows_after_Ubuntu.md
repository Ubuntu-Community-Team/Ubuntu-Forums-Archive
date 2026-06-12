---
title: "Installing Windows after Ubuntu"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Pulshion on 2007-12-26
I installed windows after having ubuntu for at least a year. I do not want to format and reinstall ubuntu. I heard its easier to set up dual boot that way. But now i can only boot up to windows. How can i setup dual boot? Ubuntu is on a different HD

---

### Post by taurus on 2007-12-26
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by overdrank on 2007-12-26
> **Pulshion said:**
> I installed windows after having ubuntu for at least a year. I do not want to format and reinstall ubuntu. I heard its easier to set up dual boot that way. But now i can only boot up to windows. How can i setup dual boot? Ubuntu is on a different HD

and to add
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
good luck!

---

### Post by Pulshion on 2007-12-26
Im not really sure, but i only have windows, i cant get to ubuntu so i can restore MBR Grub(?)

---

### Post by meindian523 on 2007-12-26
yup,using a Live CD,you can.......

---

### Post by Zuuswa on 2007-12-26
use an Ubuntu LiveCD

*edit* meindian beat me to the punch :p

---

### Post by overdrank on 2007-12-26
> **Pulshion said:**
> Im not really sure, but i only have windows, i cant get to ubuntu so i can restore MBR Grub(?)

Ok then if you don't have ubuntu, then you can reinstall it. And create your dual boot.

---

### Post by Pulshion on 2007-12-26
I have ubuntu but i cant get to it because i installed windows. Thanx for quick replies though. I appreciate it

---

### Post by meierfra on 2007-12-26
Click on FixGrub in my signature. (edit: that is the same link as in post 3)

That link  shows you  how to  boot into Ubuntu. You will also need to add Windows   to the grub menu. If you need further help, boot from the Ubuntu LiveCD and post the output of "sudo fdisk -l".

---

### Post by overdrank on 2007-12-26
> **Pulshion said:**
> I have ubuntu but i cant get to it because i installed windows. Thanx for quick replies though. I appreciate it

Ok have you tried the link I posted to reinstall the grub?

---

### Post by thiebaude on 2007-12-26
can your computer boot from CD?

---

### Post by Pulshion on 2007-12-26
yes

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe500e500

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        8286    66557263+  83  Linux
/dev/hda2            8287        8455     1357492+  82  Linux swap / Solaris
/dev/hda3   *        8456        9729    10233405    b  W95 FAT32

Disk /dev/hdb: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa849a849

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        5006    40207360    7  HPFS/NTFS


```

---

### Post by meierfra on 2007-12-26
In a terminal in the Live CD:

```
sudo grub
```

and at the "grub>" prompt:

```
root (hd0,0)
setup (hd0)
quit
```

Reboot and make sure that the 80GB Ubuntu drive is first in the boot order.

My next post will give you instruction how to add Windows to the "grub menu"

---

### Post by Pulshion on 2007-12-26
Sorry for double post, i followed directions and i can boot into ubuntu now, but i cant get to my windows lol

---

### Post by meierfra on 2007-12-26
Once you successfully booted into Ubuntu, you need to add Windows to "menu.lst".
(this assumes that you are booting from the ubuntu drive. If not let me know)

Open a terminal and type

```
gksudo gedit /boot/grub/menu.lst
```

This opens "menu.lst" in a new file. 

Look for the line

timeout 3

and change it to

timeout 10

(you only need to do that if you want more that 3 seconds to pick Windows at the Grub Menu)

Next change 

hiddenmenu

to

#hiddenmenu

Finally, add this to the end of the file:


title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


I'm not 100% sure that "root (hd1,0)" will work. If it didn't try

title Windows XP
root (hd0,2)
chainloader +1

instead.

---

### Post by Pulshion on 2007-12-26
The second option worked :) thanx a lot. Now i have to edit windows bootloader because it shows 2 options. One says that there is unknown OS on drive C, which i my FAT32 and there is no operating system. Do you know how i could just let it boot to windows and not show any options.

Edit:

Also my windows partition is D instead of C. Is it possible to change it?

---

### Post by meierfra on 2007-12-26
> Do you know how i could just let it boot to windows and not show any options.
You need to edit the  file "boot.ini".  Although I think Windows also has a GUI interface for that. But I don't know the specifics.

> Also my windows partition is D instead of C. Is it possible to change it?
No idea.  (Other then making 40 GB drive the primary drive and reinstall Windows, or repairing Windows, although I don't know whether the latter would work)

---

### Post by Pulshion on 2007-12-27
what do i do now? I switched HD's master and slave

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa849a849

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5004    40194598+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe500e500

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        8286    66557263+  83  Linux
/dev/hdb2            8287        8455     1357492+  82  Linux swap / Solaris
/dev/hdb3            8456        9729    10233405    b  W95 FAT32


```

---

### Post by meierfra on 2007-12-27
Did you reinstall Windows? Are you able to boot into Windows?  If yes you can skip to step 3) below.


I'm assuming that you did not reinstall. Lets  try a couple of things:

1) Set the Bios to boot from the Ubuntu drive.

This should let you boot into ubuntu. But I have no idea whether you will be able to boot into Windows and what your C:\ will be.

I don't have much hope that 1)  will work. But it won't take long. So its worth a shot. 


If 1) didn't to succeed:

2) Disconnect the Ubuntu (slave) drive

Boot from the Windows CD. Press "R" to get into recovery console.

Type 

```
fixmbr
```
and

```
fixboot
```


If you have  "Repair install" option somewhere give it a try.

Reboot (still without the ubuntu drive).  If you cannot boot into windows, then you need to reinstall Windows (still without the ubuntu drive)


One you successfully booted into Windows with just the Windows drive attached:

3)  Plug the Ubuntu drive into the slave position. Set the boot order so the slave drive is first. Boot into Ubuntu and edit menu.lst:

title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Reboot. You should be able to boot into XP from the Grub menu.

4)  If 3) still gives you the wrong "C:\" drive after reboot, come back here. You will have to reinstall grub and edit menu.lst so that you can boot from the master drive.

---

### Post by Pulshion on 2007-12-27
Thanx a bunch, i owe you. Everything works now :) Thanx to Ubuntu forums too :)

---

### Post by meierfra on 2007-12-27
Was 1) already enough to solve the problem?

Or did you have to reinstall Windows? 

 I would like to know, just so that I can provided better help the next times a similar case comes along.

---

### Post by meindian523 on 2007-12-28
Please explain that and mark the thread solved...

---

### Post by Pulshion on 2007-12-28
I reinstalled the windows anyway because it was a clean install before i even saw your last post. Sorry i can't give you an explanation if if worked or no. I have windows as master and linux 80 gig slave. Evertime i reinstall windows now, the grub doesnt get messed up. :)

---

### Post by meindian523 on 2007-12-28
And Grub is on

1]Master MBR
2]Slave MBR
3]Your Linux partition?

Or do you select the boot order from the BIOS to select which OS you boot?

---

